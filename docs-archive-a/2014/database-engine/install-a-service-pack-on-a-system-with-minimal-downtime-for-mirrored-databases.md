---
title: ミラー化されたデータベースのダウンタイムを最小限に抑えて、システムに Service Pack をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- hotfixes [SQL Server]
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
- service packs [SQL Server]
- upgrading mirrored database systems
- upgrading SQL Server, mirrored databases
ms.assetid: bdc63142-027d-4ead-9d3e-147331387ef5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e878d31ec926f8b2cc460854f422b4d01d32d414
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718693"
---
# <a name="install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases"></a><span data-ttu-id="1c237-102">ミラー化されたデータベースのダウンタイムを最小限に抑えた Service Pack のシステムへのインストール</span><span class="sxs-lookup"><span data-stu-id="1c237-102">Install a Service Pack on a System with Minimal Downtime for Mirrored Databases</span></span>
  <span data-ttu-id="1c237-103">このトピックでは、Service Pack および修正プログラムをインストールする際に、ミラー化されたデータベースのダウンタイムを最小限に抑える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c237-103">This topic describes how to minimize downtime for mirrored databases when you install service packs and hotfixes.</span></span> <span data-ttu-id="1c237-104">このプロセスには、データベース ミラーリングに参加している [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のインスタンスを順次アップグレードする処理が伴います。</span><span class="sxs-lookup"><span data-stu-id="1c237-104">This process involves sequentially upgrading the instances of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] that are participating in database mirroring.</span></span> <span data-ttu-id="1c237-105">この形式の更新プログラム (*ローリングアップデート*と呼ばれます) によって、ダウンタイムが1つのフェールオーバーのみに短縮されます。</span><span class="sxs-lookup"><span data-stu-id="1c237-105">This form of update, which is known as a *rolling update*, reduces downtime to only a single failover.</span></span> <span data-ttu-id="1c237-106">ただし、ミラー サーバーとプリンシパル サーバーが地理的に離れている高パフォーマンス モードのセッションでは、ローリング アップデートは適しません。</span><span class="sxs-lookup"><span data-stu-id="1c237-106">Note that for high-performance mode sessions in which the mirror server is geographically distant from the principal server, a rolling update might be inappropriate.</span></span>  
  
 <span data-ttu-id="1c237-107">ローリング アップデートは、次の複数の段階から成るプロセスです。</span><span class="sxs-lookup"><span data-stu-id="1c237-107">A rolling update is a multi-stage process that consists of the following stages:</span></span>  
  
-   <span data-ttu-id="1c237-108">データを保護する。</span><span class="sxs-lookup"><span data-stu-id="1c237-108">Protect your data.</span></span>  
  
-   <span data-ttu-id="1c237-109">セッションにミラーリング監視サーバーが含まれる場合は、ミラーリング監視サーバーを削除しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c237-109">If the session includes a witness, we recommend that you remove the witness.</span></span> <span data-ttu-id="1c237-110">そうしないと、ミラー サーバー インスタンスをアップデートする際のデータベースの可用性が、プリンシパル サーバー インスタンスに接続されたミラーリング監視サーバーに依存することになります。</span><span class="sxs-lookup"><span data-stu-id="1c237-110">Otherwise, when the mirror server instance is being updated, database availability depends on the witness that remains connected to the principal server instance.</span></span> <span data-ttu-id="1c237-111">削除したミラーリング監視サーバーは、ローリング アップデート プロセス中にいつでもアップデートでき、また、そうすることでデータベースのダウンタイムを最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="1c237-111">After you remove a witness, you can update it at any time during the rolling update process without risking database downtime.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c237-112">詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 (データベース ミラーリング)](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c237-112">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="1c237-113">セッションが高パフォーマンス モードで動作している場合は、動作モードを高い安全性モードに変更する。</span><span class="sxs-lookup"><span data-stu-id="1c237-113">If a session is running in high-performance mode, change the operating mode to high-safety mode.</span></span>  
  
-   <span data-ttu-id="1c237-114">データベース ミラーリングに参加している各サーバー インスタンスをアップデートする。</span><span class="sxs-lookup"><span data-stu-id="1c237-114">Update each server instance that is involved in database mirroring.</span></span> <span data-ttu-id="1c237-115">ローリング アップデートでは、現在ミラー サーバーであるサーバー インスタンスをアップグレードし、ミラー化された各データベースを手動でフェールオーバーして、さらに、元はプリンシパル サーバーであった (新しいミラー サーバーになる) サーバー インスタンスをアップグレードする作業が伴います。</span><span class="sxs-lookup"><span data-stu-id="1c237-115">A rolling update involves upgrading the server instance that is currently the mirror server, manually failing over each of its mirrored databases, and upgrading the server instance that was first the principal server (and is now the new mirror server).</span></span> <span data-ttu-id="1c237-116">この時点で、ミラーリングを再開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c237-116">At this point, you will have to resume mirroring.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c237-117">ローリング アップデートを開始する前に、少なくとも 1 つのミラーリング セッションで試験的に手動フェールオーバーを実行しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c237-117">Before starting a rolling update, we recommend that you perform a practice manual failover on at least one of your mirroring sessions.</span></span>  
  
-   <span data-ttu-id="1c237-118">必要に応じて、高パフォーマンス モードに戻す。</span><span class="sxs-lookup"><span data-stu-id="1c237-118">Revert to high-performance mode, if it is required.</span></span>  
  
-   <span data-ttu-id="1c237-119">必要に応じて、ミラーリング監視サーバーをミラーリング セッションに戻す。</span><span class="sxs-lookup"><span data-stu-id="1c237-119">Return the witness to the mirroring session, if it is required.</span></span>  
  
 <span data-ttu-id="1c237-120">ここでは、各段階の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c237-120">The procedures for these stages are described here.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1c237-121">同時実行ミラーリング セッションでは、1 つのサーバー インスタンスが複数の異なるミラーリング ロール (プリンシパル サーバー、ミラー サーバー、またはミラーリング監視サーバー) を実行している場合があります。</span><span class="sxs-lookup"><span data-stu-id="1c237-121">A server instance might be performing different mirroring roles (principal server, mirror server, or witness) in concurrent mirroring sessions.</span></span> <span data-ttu-id="1c237-122">この場合は、基本的なローリング アップデート プロセスを適宜調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c237-122">In this case, you will have to adapt the basic rolling update process accordingly.</span></span>  
  
### <a name="to-protect-your-data-before-an-update-a-best-practice"></a><span data-ttu-id="1c237-123">アップデート前にデータを保護するには (ベスト プラクティス)</span><span class="sxs-lookup"><span data-stu-id="1c237-123">To protect your data before an update (a best practice)</span></span>  
  
1.  <span data-ttu-id="1c237-124">すべてのプリンシパルデータベースでデータベースの完全バックアップを実行します。</span><span class="sxs-lookup"><span data-stu-id="1c237-124">Perform a full database backup on every principal database.</span></span>  
  
     <span data-ttu-id="1c237-125">**データベースをバックアップするには**</span><span class="sxs-lookup"><span data-stu-id="1c237-125">**To back up a database**</span></span>  
  
    -   <span data-ttu-id="1c237-126">[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="1c237-126">[Create a Full Database Backup &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1c237-127">すべてのプリンシパル データベースで [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1c237-127">Run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on every principal database.</span></span>  
  
### <a name="to-remove-a-witness-from-a-session"></a><span data-ttu-id="1c237-128">ミラーリング監視サーバーをセッションから削除するには</span><span class="sxs-lookup"><span data-stu-id="1c237-128">To remove a witness from a session</span></span>  
  
1.  <span data-ttu-id="1c237-129">ミラーリング セッションにミラーリング監視サーバーが存在する場合は、ローリング アップデートの実行前にミラーリング監視サーバーを削除しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c237-129">If a mirroring session involves a witness, we recommend that you remove the witness before you perform a rolling update.</span></span>  
  
     <span data-ttu-id="1c237-130">**ミラーリング監視サーバーを削除するには**</span><span class="sxs-lookup"><span data-stu-id="1c237-130">**To remove the witness**</span></span>  
  
    -   [<span data-ttu-id="1c237-131">データベース ミラーリング セッションからのミラーリング監視サーバーの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c237-131">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a><span data-ttu-id="1c237-132">セッションを高パフォーマンス モードから高い安全性モードに変更するには</span><span class="sxs-lookup"><span data-stu-id="1c237-132">To change a session from high-performance mode to high-safety mode</span></span>  
  
1.  <span data-ttu-id="1c237-133">ミラーリング セッションを高パフォーマンス モードで実行している場合は、ローリング アップデートを実行する前に、動作モードを、自動フェールオーバーを伴わない高い安全性モードに変更します。</span><span class="sxs-lookup"><span data-stu-id="1c237-133">If a mirroring session is running in high-performance mode, before you perform a rolling update, change the operating mode to high safety without automatic failover.</span></span> <span data-ttu-id="1c237-134">以下のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="1c237-134">Use one of the following methods:</span></span>  
  
    -   <span data-ttu-id="1c237-135">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: **[データベースのプロパティ]** ダイアログ ボックスの [[ミラーリング]](../relational-databases/databases/database-properties-mirroring-page.md) ページで、 **[動作モード]** オプションを **[自動フェールオーバーを伴わない高い安全性 (同期)]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="1c237-135">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High safety without automatic failover (synchronous)** by using the [Mirroring Page](../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span> <span data-ttu-id="1c237-136">このページにアクセスする方法については、「[データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c237-136">For information about how to access this page, see [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md).</span></span>  
  
    -   <span data-ttu-id="1c237-137">[!INCLUDE[tsql](../includes/tsql-md.md)]: トランザクションの安全性を FULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="1c237-137">In [!INCLUDE[tsql](../includes/tsql-md.md)]: Set transaction safety to FULL.</span></span> <span data-ttu-id="1c237-138">詳細については、｢[データベース ミラーリング セッションでのトランザクションの安全性の変更 &#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c237-138">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
### <a name="to-perform-the-rolling-update"></a><span data-ttu-id="1c237-139">ローリング アップデートを実行するには</span><span class="sxs-lookup"><span data-stu-id="1c237-139">To perform the rolling update</span></span>  
  
1.  <span data-ttu-id="1c237-140">ローリング アップデートを開始する際は、ダウンタイムを最小限に抑えるため、すべてのミラーリング セッションにおいてミラー サーバーとして機能しているミラーリング パートナーから先に更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c237-140">To minimize downtime, we recommend the following: Start the rolling update by updating any mirroring partner that is currently the mirror server in all its mirroring sessions.</span></span> <span data-ttu-id="1c237-141">場合によっては、この時点で複数のサーバー インスタンスを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c237-141">You might have to update multiple server instances at this point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c237-142">ミラーリング監視サーバーは、ローリング アップデート プロセス中、いつでもアップデートできます。</span><span class="sxs-lookup"><span data-stu-id="1c237-142">A witness can be updated at any point in the rolling update process.</span></span> <span data-ttu-id="1c237-143">たとえば、セッション 1 ではミラー サーバーとして、セッション 2 ではミラーリング監視サーバーとして機能しているサーバー インスタンスであれば、今すぐにアップデートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1c237-143">For example, if a server instance is a mirror server in Session 1 and is a witness in Session 2, you can update the server instance now.</span></span>  
  
     <span data-ttu-id="1c237-144">最初にアップデートするサーバー インスタンスは、ミラーリング セッションが現在どのように構成されているかによって異なります。その指針を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1c237-144">The server instance to update first depends on the current configuration of your mirroring sessions, as follows:</span></span>  
  
    -   <span data-ttu-id="1c237-145">サーバー インスタンスがそのすべてのミラーリング セッションにおいて既にミラー サーバーとして機能している場合、そのサーバー インスタンスに Service Pack または修正プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="1c237-145">If any server instance is already the mirror server in all of its mirroring sessions, install the service pack or the hotfix on that server instance.</span></span>  
  
    -   <span data-ttu-id="1c237-146">どのサーバー インスタンスもいずれかのミラーリング セッションのプリンシパル サーバーとして機能している場合は、最初にアップデートするサーバー インスタンスを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="1c237-146">If all of your server instances are currently the principal server in any mirroring sessions, select one server instance to update first.</span></span> <span data-ttu-id="1c237-147">次に、選択したサーバー インスタンスの各プリンシパル データベースを手動でフェールオーバーし、Service Pack または修正プログラムをインストールしてそのサーバー インスタンスをアップデートします。</span><span class="sxs-lookup"><span data-stu-id="1c237-147">Then, manually fail over each of its principal databases and update that server instance by installing the service pack or the hotfix.</span></span>  
  
     <span data-ttu-id="1c237-148">アップデート後のサーバー インスタンスは、自動的にそれぞれのミラーリング セッションに再度参加します。</span><span class="sxs-lookup"><span data-stu-id="1c237-148">After being updated, a server instance automatically rejoins each of its mirroring sessions.</span></span>  
  
     <span data-ttu-id="1c237-149">**手動フェールオーバーを実行するには**</span><span class="sxs-lookup"><span data-stu-id="1c237-149">**To perform a manual failover**</span></span>  
  
    -   [<span data-ttu-id="1c237-150">データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1c237-150">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="1c237-151">[データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;Transact-SQL&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="1c237-151">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md).</span></span>  
  
     <span data-ttu-id="1c237-152">手動フェールオーバーのしくみについては、「[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c237-152">For information about how manual failover works, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1c237-153">前の手順でアップデートしたミラー サーバー インスタンスのすべてのミラーリング セッションの同期が完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="1c237-153">For each mirroring session whose mirror server instance has just been updated, wait for the session to synchronize.</span></span> <span data-ttu-id="1c237-154">次に、プリンシパル サーバー インスタンスに接続し、セッションを手動でフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="1c237-154">Then, connect to the principal server instance, and manually fail over the session.</span></span> <span data-ttu-id="1c237-155">フェールオーバー時は、アップデートされたサーバー インスタンスがそのセッションのプリンシパル サーバーになり、以前のプリンシパル サーバーがミラー サーバーになります。</span><span class="sxs-lookup"><span data-stu-id="1c237-155">On failover, the updated server instance becomes the principal server for that session, and the former principal server becomes the mirror server.</span></span>  
  
     <span data-ttu-id="1c237-156">この手順の目的は、すべてのミラーリング セッションで、パートナー関係にある他方のサーバー インスタンスがミラー サーバーとなるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="1c237-156">The goal of this step is for another server instance to become the mirror server in every mirroring session in which it is a partner.</span></span>  
  
3.  <span data-ttu-id="1c237-157">フェールオーバー後は、プリンシパル データベースに対して [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) コマンドを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c237-157">After you fail over, we recommend that you run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on the principal database.</span></span>  
  
4.  <span data-ttu-id="1c237-158">すべてのミラーリング セッションで、ミラー サーバー (パートナー) になった各サーバー インスタンスに Service Pack または修正プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="1c237-158">Install the service pack or the hotfix on each server instance that is now the mirror server in all mirroring sessions in which it is a partner.</span></span> <span data-ttu-id="1c237-159">場合によっては、この時点で複数のサーバーを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c237-159">You might have to update multiple servers at this point.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1c237-160">複雑なミラーリング構成の場合、一部のサーバー インスタンスが、1 つまたは複数のミラーリング セッションで元のプリンシパル サーバーとして機能している場合があります。</span><span class="sxs-lookup"><span data-stu-id="1c237-160">In a complex mirroring configuration, some server instance might still be the original principal server in one or more mirroring sessions.</span></span> <span data-ttu-id="1c237-161">関連するすべてのインスタンスが更新されるまで、これらのサーバーインスタンスに対して手順2-4 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1c237-161">Repeat steps 2-4 for those server instances until all instances involved are updated.</span></span>  
  
5.  <span data-ttu-id="1c237-162">ミラーリング セッションを再開します。</span><span class="sxs-lookup"><span data-stu-id="1c237-162">Resume the mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c237-163">自動フェールオーバーは、ミラーリング監視サーバーがアップデートされるまで機能しません。</span><span class="sxs-lookup"><span data-stu-id="1c237-163">Automatic failover will not work until the witness has been updated.</span></span>  
  
6.  <span data-ttu-id="1c237-164">すべてのミラーリング セッションの残りのサーバー インスタンス (ミラーリング監視サーバー) に Service Pack または修正プログラムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="1c237-164">Install the service packs or hotfixes on any remaining server instance that is the witness in all its mirroring sessions.</span></span> <span data-ttu-id="1c237-165">アップデートしたミラーリング監視サーバーをミラーリング セッションに再度参加させると、自動フェールオーバーが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1c237-165">After an updated witness rejoins a mirroring session, automatic failover becomes possible again.</span></span> <span data-ttu-id="1c237-166">場合によっては、この時点で複数のサーバーを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c237-166">You might have to update multiple servers at this point.</span></span>  
  
### <a name="to-return-a-session-to-high-performance-mode"></a><span data-ttu-id="1c237-167">セッションを高パフォーマンス モードに戻すには</span><span class="sxs-lookup"><span data-stu-id="1c237-167">To return a session to high-performance mode</span></span>  
  
1.  <span data-ttu-id="1c237-168">必要に応じて、高パフォーマンス モードに戻す場合は、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="1c237-168">Optionally, return to high-performance mode by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="1c237-169">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページで、[[動作モード]](../relational-databases/databases/database-properties-mirroring-page.md) オプションを **[高パフォーマンス (非同期)]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="1c237-169">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High performance (asynchronous)** by using the [Mirroring Page](../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="1c237-170">[!INCLUDE[tsql](../includes/tsql-md.md)]: [ALTER database](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)を使用して、トランザクションの安全性を OFF に設定します。</span><span class="sxs-lookup"><span data-stu-id="1c237-170">In [!INCLUDE[tsql](../includes/tsql-md.md)]: Use [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) to set transaction safety to OFF.</span></span>  
  
### <a name="to-return-a-witness-to-a-mirroring-session"></a><span data-ttu-id="1c237-171">ミラーリング監視サーバーをミラーリングセッションに戻すには</span><span class="sxs-lookup"><span data-stu-id="1c237-171">To return a witness to a mirroring session</span></span>  
  
1.  <span data-ttu-id="1c237-172">必要に応じて、高い安全性モードで、各ミラーリング セッションのミラーリング監視サーバーを再度確立します。</span><span class="sxs-lookup"><span data-stu-id="1c237-172">Optionally, in high-safety mode, reestablish the witness to each mirroring session.</span></span>  
  
     <span data-ttu-id="1c237-173">**ミラーリング監視サーバーを削除するには**</span><span class="sxs-lookup"><span data-stu-id="1c237-173">**To reestablish the witness**</span></span>  
  
    -   [<span data-ttu-id="1c237-174">データベース ミラーリング監視サーバーを追加または置き換える方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1c237-174">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="1c237-175">Windows 認証を使用してデータベースのミラーリング監視を追加する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1c237-175">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring/add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="1c237-176">参照</span><span class="sxs-lookup"><span data-stu-id="1c237-176">See Also</span></span>  
 <span data-ttu-id="1c237-177">[ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="1c237-177">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="1c237-178">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1c237-178">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="1c237-179">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c237-179">[Database Mirroring &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="1c237-180">[データベース ミラーリングの動作モード](database-mirroring/database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="1c237-180">[Database Mirroring Operating Modes](database-mirroring/database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="1c237-181">[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c237-181">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="1c237-182">[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1c237-182">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="1c237-183">ミラー化されたデータベースの状態の確認 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1c237-183">View the State of a Mirrored Database &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/view-the-state-of-a-mirrored-database-sql-server-management-studio.md)  
  
  
