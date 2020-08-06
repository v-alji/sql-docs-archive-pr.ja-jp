---
title: データベース ミラーリングの前提条件、制限事項、推奨事項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- partners [SQL Server]
- database mirroring [SQL Server], prerequisites
- database mirroring [SQL Server], recommendations
- database mirroring [SQL Server], restrictions
- database mirroring [SQL Server], planning
- database mirroring [SQL Server], about database mirroring
ms.assetid: fdcf2251-9895-44c6-b81e-768fef32e732
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0dc29dbdc8432a4abd197a2a1a3f15b6ff5f6d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716778"
---
# <a name="prerequisites-restrictions-and-recommendations-for-database-mirroring"></a><span data-ttu-id="afba4-102">データベース ミラーリングの前提条件、制限事項、および推奨事項</span><span class="sxs-lookup"><span data-stu-id="afba4-102">Prerequisites, Restrictions, and Recommendations for Database Mirroring</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="afba4-103">代わりに [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="afba4-103">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="afba4-104">このトピックでは、データベース ミラーリングを設定するための前提条件と推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="afba4-104">This topic describes the prerequisites and recommendations for setting up database mirroring.</span></span> <span data-ttu-id="afba4-105">データベース ミラーリングの概要については、「 [データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-105">For an introduction to database mirroring, see [Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="afba4-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のディスク上のストレージ形式は、64 ビット環境でも 32 ビット環境でも同じです。</span><span class="sxs-lookup"><span data-stu-id="afba4-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="afba4-107">このため、データベース ミラーリング セッションでは、32 ビット環境で実行されているサーバー インスタンスと 64 ビット環境で実行されているサーバー インスタンスを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="afba4-107">Therefore, a database mirroring session can combine server instances that run in a 32-bit environment and server instances that run in a 64-bit environment.</span></span>  
  

  
##  <a name="support-for-database-mirroring"></a><a name="DbmSupport"></a><span data-ttu-id="afba4-108">データベースミラーリングのサポート</span><span class="sxs-lookup"><span data-stu-id="afba4-108">Support For Database Mirroring</span></span>  
 <span data-ttu-id="afba4-109">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でのデータベース ミラーリングのサポートについては、「[SQL Server 2014 の各エディションでサポートされる機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-109">For information about support for database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="afba4-110">データベース ミラーリングは、サポートされているすべてのデータベース互換性レベルで動作します。</span><span class="sxs-lookup"><span data-stu-id="afba4-110">Note that database mirroring works with any supported database compatibility level.</span></span> <span data-ttu-id="afba4-111">サポートされている互換性レベルについては、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-111">For information about the supported compatibility levels, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  

  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="afba4-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="afba4-112">Prerequisites</span></span>  
  
-   <span data-ttu-id="afba4-113">ミラーリング セッションを確立するには、パートナーとミラーリング監視サーバー (存在する場合) が、同じバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-113">For a mirroring session to be established, the partners and the witness, if any, must be running on the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="afba4-114">2 つのパートナー (プリンシパル サーバーとミラー サーバー) で同じエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-114">The two partners, that is the principal server and mirror server, must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="afba4-115">ミラーリング監視サーバー (存在する場合) は、データベース ミラーリングをサポートする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで実行できます。</span><span class="sxs-lookup"><span data-stu-id="afba4-115">The witness, if any, can run on any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports database mirroring.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="afba4-116">ミラーリング セッションでのパートナーであるサーバー インスタンスを、より新しいバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="afba4-116">You can upgrade server instances that are partners in a mirroring session to a more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="afba4-117">詳しくは、「 [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="afba4-117">For more information, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).</span></span>  
  
-   <span data-ttu-id="afba4-118">このデータベースは、完全復旧モデルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-118">The database must use the full recovery model.</span></span> <span data-ttu-id="afba4-119">単純復旧モデルと一括ログ復旧モデルでは、データベース ミラーリングがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="afba4-119">The simple and bulk-logged recovery models do not support database mirroring.</span></span> <span data-ttu-id="afba4-120">そのため、ミラー化されたデータベースでは、常に一括操作が完全にログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="afba4-120">Therefore, bulk operations are always fully logged for a mirrored database.</span></span> <span data-ttu-id="afba4-121">復旧モデルについては、「[復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-121">For information about recovery models, see [Recovery Models &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).</span></span>  
  
-   <span data-ttu-id="afba4-122">ミラー サーバーにミラー データベースを保持するだけの十分なディスク領域があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="afba4-122">Verify that the mirror server has sufficient disk space for the mirror database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="afba4-123">レプリケートされるデータベースでのデータベース ミラーリングの使用方法の詳細については、「[データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-123">For information about how to use database mirroring on a replicated database, see [Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="afba4-124">ミラー サーバーにミラー データベースを作成する際は、同じデータベース名と WITH NORECOVERY オプションを指定して、プリンシパル データベースのバックアップを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-124">When you are creating the mirror database on the mirror server, make sure that you restore the backup of the principal database specifying the same database name WITH NORECOVERY.</span></span> <span data-ttu-id="afba4-125">また、このバックアップが実行された後で作成されたすべてのログ バックアップについても、WITH NORECOVERY を指定して適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-125">Also, all log backups that were created after that backup was taken must also be applied, again WITH NORECOVERY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="afba4-126">データベース ミラーリングが停止している場合は、データベース ミラーリングを再開する前に、停止中にプリンシパル データベースで作成されたすべてのログ バックアップをミラー データベースに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-126">If database mirroring has been stopped, before you can restart it, any subsequent log backups taken on the principal database must be applied to the mirror database.</span></span>  
  

  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="afba4-127">制限</span><span class="sxs-lookup"><span data-stu-id="afba4-127">Restrictions</span></span>  
  
-   <span data-ttu-id="afba4-128">ミラー化できるのはユーザー データベースのみです。</span><span class="sxs-lookup"><span data-stu-id="afba4-128">Only user databases can be mirrored.</span></span> <span data-ttu-id="afba4-129">**master**、 **msdb**、 **tempdb**、または **model** の各データベースはミラー化できません。</span><span class="sxs-lookup"><span data-stu-id="afba4-129">You cannot mirror the **master**, **msdb**, **tempdb**, or **model** databases.</span></span>  
  
-   <span data-ttu-id="afba4-130">データベース ミラーリング セッション中に、ミラー化されるデータベースの名前を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="afba4-130">A mirrored database cannot be renamed during a database mirroring session.</span></span>  
  
-   <span data-ttu-id="afba4-131">データベース ミラーリングは FILESTREAM をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="afba4-131">Database mirroring does not support FILESTREAM.</span></span> <span data-ttu-id="afba4-132">プリンシパル サーバー上に FILESTREAM ファイル グループを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="afba4-132">A FILESTREAM filegroup cannot be created on the principal server.</span></span> <span data-ttu-id="afba4-133">FILESTREAM ファイル グループを含むデータベースに対してデータベース ミラーリングを構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="afba4-133">Database mirroring cannot be configured for a database that contains FILESTREAM filegroups.</span></span>  
  
-   <span data-ttu-id="afba4-134">32 ビット システムの場合、データベース ミラーリングでは、各データベース ミラーリング セッションで使用されるワーカー スレッド数の関係で、サーバー インスタンスあたり最大約 10 個のデータベースをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="afba4-134">On a 32-bit system, database mirroring can support a maximum of about 10 databases per server instance because of the numbers of worker threads that are consumed by each database mirroring session.</span></span>  
  
-   <span data-ttu-id="afba4-135">複数のデータベースにまたがるトランザクションまたは分散トランザクションでは、データベース ミラーリングがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="afba4-135">Database mirroring is not supported with either cross-database transactions or distributed transactions.</span></span> <span data-ttu-id="afba4-136">詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-136">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  

  
##  <a name="recommendations-for-configuring-partner-servers"></a><a name="RecommendationsForPartners"></a><span data-ttu-id="afba4-137">パートナーサーバーの構成に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="afba4-137">Recommendations for Configuring Partner Servers</span></span>  
  
-   <span data-ttu-id="afba4-138">パートナーは、同じ量のワークロードを処理できる同等のシステムで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-138">The partners should run on comparable systems that can handle identical workloads.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="afba4-139">自動フェールオーバーを伴う高い安全性モードを使用する場合は、各フェールオーバー パートナーの通常の負荷が CPU の 50% 未満である必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-139">If you plan to use high-safety mode with automatic failover, the normal load on each failover partner should be less than 50 percent of the CPU.</span></span> <span data-ttu-id="afba4-140">ワークロードによって CPU が過負荷になると、フェールオーバー パートナーがミラーリング セッションで他のサーバー インスタンスに ping を実行できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-140">If your work load overloads the CPU, a failover partner might be unable to ping the other server instances in the mirroring session.</span></span> <span data-ttu-id="afba4-141">これにより、不必要なフェールオーバーが発生します。</span><span class="sxs-lookup"><span data-stu-id="afba4-141">This causes a unnecessary failover.</span></span> <span data-ttu-id="afba4-142">CPU 使用率を 50% 未満に維持できない場合は、自動フェールオーバーを伴わない高い安全性モードか、高パフォーマンス モードを使用することを推奨しています。</span><span class="sxs-lookup"><span data-stu-id="afba4-142">If you cannot keep the CPU usage under 50 percent, we recommend that you use either high-safety mode without automatic failover or high-performance mode.</span></span>  
  
-   <span data-ttu-id="afba4-143">可能であれば、ミラー データベースのパス (ドライブ文字を含む) を、プリンシパル データベースと同一のパスにします。</span><span class="sxs-lookup"><span data-stu-id="afba4-143">If possible, the path (including the drive letter) of the mirror database should be identical to the path of the principal database.</span></span> <span data-ttu-id="afba4-144">ファイル レイアウトが異なる場合は、RESTORE ステートメントに MOVE オプションを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-144">You must include the MOVE option in the RESTORE statement if the file layouts must differ.</span></span> <span data-ttu-id="afba4-145">プリンシパル データベースがドライブ 'F:' 上にあっても、ミラー システムには F: ドライブがない場合などがあります。</span><span class="sxs-lookup"><span data-stu-id="afba4-145">For example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="afba4-146">ミラー データベースの作成時にデータベース ファイルを移動した場合、そのミラー データベースに後でファイルを追加する際に、ミラーリングの中断が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-146">If you move the database files when you create the mirror database, you might be unable to add files to the database later without mirroring being suspended.</span></span>  
  
-   <span data-ttu-id="afba4-147">ミラーリング セッションのすべてのサーバー インスタンスが同じマスター コード ページと照合順序を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-147">All of the server instances in a mirroring session should use the same master code page and collation.</span></span> <span data-ttu-id="afba4-148">異なるマスター コード ページと照合順序を使用すると、ミラーリングの設定中にエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-148">Differences can cause a problem during mirroring setup.</span></span>  
  
-   <span data-ttu-id="afba4-149">必要に応じて、データベースのフェールオーバーにかかる時間を見積もり、必要なパフォーマンスを実現できるようにシステムを構成します。</span><span class="sxs-lookup"><span data-stu-id="afba4-149">Optionally, estimate the time to fail over a database, to make sure that the system configuration will provide the performance you require.</span></span> <span data-ttu-id="afba4-150">詳しくは、「 [役割の交代中に発生するサービスの中断時間の算出 &#40;データベース ミラーリング&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)という処理により、一般的にプリンシパルとミラーの役割を相互交換できます。</span><span class="sxs-lookup"><span data-stu-id="afba4-150">For more information, see [Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="afba4-151">最適なパフォーマンスを得るには、ミラーリングに専用のネットワーク アダプター (ネットワーク インターフェイス カード) を使用します。</span><span class="sxs-lookup"><span data-stu-id="afba4-151">For best performance, use a dedicated network adapter (network interface card) for mirroring.</span></span>  
  
-   <span data-ttu-id="afba4-152">高い安全性モードでデータベース ミラーリングを行う場合、ワイドエリア ネットワーク (WAN) の信頼性が十分かどうかに関する推奨事項はありません。</span><span class="sxs-lookup"><span data-stu-id="afba4-152">We make no recommendations about whether a wide-area network (WAN) is reliable enough for database mirroring in high-safety mode.</span></span> <span data-ttu-id="afba4-153">高い安全性モードで WAN 経由のデータベース ミラーリングを使用する場合、不要なフェールオーバーが自動的に行われる可能性があるため、セッションにミラーリング監視サーバーを追加する方法には注意してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-153">If you decide to use high-safety mode over a WAN, be cautious about how you add a witness to the session, because unwanted automatic failovers can occur.</span></span> <span data-ttu-id="afba4-154">詳細については、このトピックの「 [データベース ミラーリングの配置に関する推奨事項](#RecommendationsForDeploying)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-154">For more information, see [Recommendations for Deploying Database Mirroring](#RecommendationsForDeploying), later in this topic.</span></span>  
  

  
##  <a name="recommendations-for-deploying-database-mirroring"></a><a name="RecommendationsForDeploying"></a><span data-ttu-id="afba4-155">データベースミラーリングの配置に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="afba4-155">Recommendations for Deploying Database Mirroring</span></span>  
 <span data-ttu-id="afba4-156">データベース ミラーリングのパフォーマンスを最適化するには、非同期動作を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-156">Optimal database mirroring performance is obtained by using asynchronous operation.</span></span> <span data-ttu-id="afba4-157">同期動作を使用するミラーリング セッションは、ワークロードが大量のトランザクション ログ データを生成するときに、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="afba4-157">A mirroring session that uses synchronous operation might experience slowed performance when its workload generates large amounts of transaction log data.</span></span>  
  
 <span data-ttu-id="afba4-158">テスト環境ですべての動作モードを調査し、データベース ミラーリングのパフォーマンスを評価することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="afba4-158">In test environments, it is appropriate to explore all the operating modes to evaluate how database mirroring performs.</span></span> <span data-ttu-id="afba4-159">ただし、ミラーリングを運用環境に配置する前に、実際のネットワークの性能を理解することが必要です。</span><span class="sxs-lookup"><span data-stu-id="afba4-159">However, before you deploy mirroring into a production environment, make sure that you understand how the network functions in the real world.</span></span>  
  
 <span data-ttu-id="afba4-160">自動フェールオーバーを伴う高い安全性モードは、ネットワーク障害が発生する可能性を最小限に抑える、専用接続または非常に単純なネットワーク構成を備えた高サービス ネットワーク用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="afba4-160">High-safety mode with automatic failover is designed for a high-service network that has either a dedicated connection or a fairly simple network configuration that minimizes the sources of possible network failures.</span></span> <span data-ttu-id="afba4-161">自動フェールオーバーを伴う高い安全性モードにはこのような質の高いネットワーク環境が不可欠であり、すべてのデータベース ミラーリング セッションに推奨されます。</span><span class="sxs-lookup"><span data-stu-id="afba4-161">Such a high-quality network environment is necessary for high-safety mode with automatic failover and is recommended for all database mirroring sessions.</span></span> <span data-ttu-id="afba4-162">ただし、高パフォーマンス モードと自動フェールオーバーを伴わない高い安全性モードは、ネットワークの信頼性による影響をそれほど受けません。</span><span class="sxs-lookup"><span data-stu-id="afba4-162">However, high-performance mode and high-safety mode without automatic failover are much less affected by network reliability.</span></span>  
  
 <span data-ttu-id="afba4-163">したがって、実稼働環境では、以下の配置ガイドラインに従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="afba4-163">Therefore, for production environments we recommend that you adhere to the following deployment guidelines:</span></span>  
  
1.  <span data-ttu-id="afba4-164">非同期の高パフォーマンス モードで実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="afba4-164">Start running in asynchronous, high-performance mode.</span></span> <span data-ttu-id="afba4-165">このモードは、ネットワーク環境の影響を受けることが最も少なく、ミラーリングの動作を調べるには最善の構成です。</span><span class="sxs-lookup"><span data-stu-id="afba4-165">This mode is the least sensitive to the network environment and provides the best configuration for exploring how mirroring works.</span></span> <span data-ttu-id="afba4-166">帯域幅がミラーリングをサポートすることに確信が持て、ミラーリングの設定および環境における非同期モードのパフォーマンスについて理解できるまでは、システムを非同期で実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="afba4-166">We recommend that you run your system asynchronously until you are confident that your bandwidth supports mirroring and you have developed an understanding of mirroring setup and of the performance of asynchronous mode in your environment.</span></span> <span data-ttu-id="afba4-167">詳しくは、「 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="afba4-167">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="afba4-168">テストの期間をとおして、データベース ミラーリングの障害の原因となるネットワーク エラーをセッションで監視することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="afba4-168">Throughout testing, we recommend that you monitor your sessions for network errors that cause database mirroring to fail.</span></span> <span data-ttu-id="afba4-169">障害の潜在的な原因の詳細については、「 [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-169">For more information about potential sources of failure, see [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md).</span></span> <span data-ttu-id="afba4-170">データベース ミラーリングの監視方法については、「[データベース ミラーリングの監視 &#40;SQL Server&#41;](monitoring-database-mirroring-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afba4-170">For information about how to monitor database mirroring, see [Monitoring Database Mirroring &#40;SQL Server&#41;](monitoring-database-mirroring-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="afba4-171">非同期動作がビジネス ニーズを満たすことが確信できたなら、同期動作を実行してデータ保護の強化を図ることができます。</span><span class="sxs-lookup"><span data-stu-id="afba4-171">When you are confident that asynchronous operation is meeting the business needs, you might want to try synchronous operation to improve your data protection.</span></span> <span data-ttu-id="afba4-172">自分の環境で同期ミラーリングがどのように動作するのかをテストするときは、最初に自動フェールオーバーを伴わない高い安全性モードをテストすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="afba4-172">When you test how synchronous mirroring works in your environment, we recommend that first you test high-safety mode without automatic failover.</span></span> <span data-ttu-id="afba4-173">このテストの主な目的は、同期操作がデータベースのパフォーマンスに与える影響を確認することです。</span><span class="sxs-lookup"><span data-stu-id="afba4-173">The primary purpose of this testing is to see how synchronous operation affects the database performance.</span></span> <span data-ttu-id="afba4-174">詳しくは、「 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="afba4-174">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
3.  <span data-ttu-id="afba4-175">自動フェールオーバーを伴わない高い安全性モードがビジネス ニーズを満たしていること、およびネットワーク エラーによって障害が発生しないことを確認できるまで、自動フェールオーバーは有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="afba4-175">Wait to enable automatic failover until you are confident that high-safety mode without automatic failover is meeting the business needs and that network errors are not causing failures.</span></span> <span data-ttu-id="afba4-176">詳細については、「 [データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="afba4-176">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="afba4-177">参照</span><span class="sxs-lookup"><span data-stu-id="afba4-177">See Also</span></span>  
 <span data-ttu-id="afba4-178">[データベース ミラーリングの設定 &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="afba4-178">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="afba4-179">[データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="afba4-179">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="afba4-180">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="afba4-180">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="afba4-181">データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="afba4-181">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
