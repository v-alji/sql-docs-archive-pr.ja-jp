---
title: ログ配布のセカンダリへのフェールオーバー (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- primary databases [SQL Server]
- secondary data files [SQL Server], manual fail over
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: edfe5d59-4287-49c1-96c9-dd56212027bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 164e2809e4eff5a14ef54124df7c7ca9077793ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718663"
---
# <a name="fail-over-to-a-log-shipping-secondary-sql-server"></a><span data-ttu-id="725c3-102">ログ配布のセカンダリへのフェールオーバー (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="725c3-102">Fail Over to a Log Shipping Secondary (SQL Server)</span></span>
  <span data-ttu-id="725c3-103">ログ配布のセカンダリへのフェールオーバーは、プライマリ サーバー インスタンスが失敗した場合、またはプライマリ サーバー インスタンスにメンテナンスが必要な場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="725c3-103">Failing over to a log shipping secondary is useful if the primary server instance fails or requires maintenance.</span></span>  
  
## <a name="preparing-for-a-controlled-failover"></a><span data-ttu-id="725c3-104">制御されたフェールオーバーの準備</span><span class="sxs-lookup"><span data-stu-id="725c3-104">Preparing for a Controlled Failover</span></span>  
 <span data-ttu-id="725c3-105">プライマリ データベースは最新のバックアップ ジョブの後も更新され続けるため、通常、プライマリ データベースとセカンダリ データベースは同期されていません。</span><span class="sxs-lookup"><span data-stu-id="725c3-105">Typically, the primary and secondary databases are unsynchronized, because the primary database continues to be updated after its latest backup job.</span></span> <span data-ttu-id="725c3-106">また、場合によっては、最新のトランザクション ログのバックアップは、セカンダリ サーバー インスタンスにコピーされていなかったり、コピーされたログのバックアップの一部がセカンダリ データベースにまだ適用されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="725c3-106">Also, in some cases, recent transaction log backups have not been copied to the secondary server instances, or some copied log backups might still not have been applied to the secondary database.</span></span> <span data-ttu-id="725c3-107">可能な場合は、すべてのセカンダリ データベースをプライマリ データベースに同期することから開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="725c3-107">We recommend that you begin by synchronizing all of the secondary databases with the primary database, if possible.</span></span>  
  
 <span data-ttu-id="725c3-108">ログ配布ジョブの詳細については、「 [ログ配布について &#40;SQL Server&#41;](about-log-shipping-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="725c3-108">For information about log shipping jobs, see [About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md).</span></span>  
  
## <a name="failing-over"></a><span data-ttu-id="725c3-109">フェールオーバー</span><span class="sxs-lookup"><span data-stu-id="725c3-109">Failing Over</span></span>  
 <span data-ttu-id="725c3-110">セカンダリ データベースにフェールオーバーするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="725c3-110">To fail over to a secondary database:</span></span>  
  
1.  <span data-ttu-id="725c3-111">バックアップ共有からコピーされていないバックアップ ファイルを、各セカンダリ サーバーのコピー先フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="725c3-111">Copy any uncopied backup files from the backup share to the copy destination folder of each secondary server.</span></span>  
  
2.  <span data-ttu-id="725c3-112">適用されていないトランザクション ログのバックアップを、各セカンダリ データベースに順に適用します。</span><span class="sxs-lookup"><span data-stu-id="725c3-112">Apply any unapplied transaction log backups in sequence to each secondary database.</span></span> <span data-ttu-id="725c3-113">詳細については、「[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="725c3-113">For more information, see [Apply Transaction Log Backups &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="725c3-114">プライマリ データベースにアクセスできる場合は、アクティブなトランザクション ログをバックアップし、そのログのバックアップをセカンダリ データベースに適用します。</span><span class="sxs-lookup"><span data-stu-id="725c3-114">If the primary database is accessible, back up the active transaction log and apply the log backup to the secondary databases.</span></span>  
  
     <span data-ttu-id="725c3-115">元のプライマリ サーバー インスタンスが破損していない場合は、WITH NORECOVERY を使用してプライマリ データベースのトランザクション ログの末尾をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="725c3-115">If the original primary server instance is not damaged, back up the tail of the transaction log of the primary database using WITH NORECOVERY.</span></span> <span data-ttu-id="725c3-116">これにより、データベースは復旧状態で維持されるので、ユーザーは使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="725c3-116">This leaves the database in the restoring state and therefore unavailable to users.</span></span> <span data-ttu-id="725c3-117">最終的には、置換プライマリ データベースからトランザクション ログのバックアップを適用することにより、このデータベースをロールフォワードできるようになります。</span><span class="sxs-lookup"><span data-stu-id="725c3-117">Eventually you will be able to roll this database forward by applying transaction log backups from the replacement primary database.</span></span>  
  
     <span data-ttu-id="725c3-118">詳細については、「[トランザクション ログ バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="725c3-118">For more information, see [Transaction Log Backups &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="725c3-119">セカンダリ サーバーが同期された後は、任意のサーバーのセカンダリ データベースを復旧し、そのサーバー インスタンスにクライアントをリダイレクトすることによって、そのサーバーにフェールオーバーできます。</span><span class="sxs-lookup"><span data-stu-id="725c3-119">After the secondary servers are synchronized, you can fail over to whichever one you prefer by recovering its secondary database and redirecting clients to that server instance.</span></span> <span data-ttu-id="725c3-120">復旧によって、データベースは一貫性のある状態になり、オンラインになります。</span><span class="sxs-lookup"><span data-stu-id="725c3-120">Recovering puts the database into a consistent state and brings it online.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="725c3-121">セカンダリ データベースを使用可能にするときは、そのデータベースのメタデータと元のプライマリ データベースのメタデータに一貫性があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="725c3-121">When you make a secondary database available, you should ensure that its metadata is consistent with the metadata of the original primary database.</span></span> <span data-ttu-id="725c3-122">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="725c3-122">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
5.  <span data-ttu-id="725c3-123">セカンダリ データベースを復旧した後は、そのデータベースが他のセカンダリ データベースのプライマリ データベースとして機能するように再構成できます。</span><span class="sxs-lookup"><span data-stu-id="725c3-123">After you have recovered a secondary database, you can reconfigure it to act as a primary database for other secondary databases.</span></span>  
  
     <span data-ttu-id="725c3-124">他に使用できるセカンダリ データベースがない場合の詳細については、「[ログ配布の構成 &#40;SQL Server&#41;](configure-log-shipping-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="725c3-124">If no other secondary database is available, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="725c3-125">関連タスク</span><span class="sxs-lookup"><span data-stu-id="725c3-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="725c3-126">プライマリ ログ配布サーバーとセカンダリ ログ配布サーバー間でのロールの変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="725c3-126">Change Roles Between Primary and Secondary Log Shipping Servers &#40;SQL Server&#41;</span></span>](change-roles-between-primary-and-secondary-log-shipping-servers-sql-server.md)  
  
-   [<span data-ttu-id="725c3-127">役割の交代後のログインとジョブの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="725c3-127">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="725c3-128">参照</span><span class="sxs-lookup"><span data-stu-id="725c3-128">See Also</span></span>  
 <span data-ttu-id="725c3-129">[ログ配布テーブルとストアド プロシージャ](log-shipping-tables-and-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="725c3-129">[Log Shipping Tables and Stored Procedures](log-shipping-tables-and-stored-procedures.md) </span></span>  
 <span data-ttu-id="725c3-130">[ログ配布について &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="725c3-130">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="725c3-131">ログ末尾のバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="725c3-131">Tail-Log Backups &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)  
  
  
