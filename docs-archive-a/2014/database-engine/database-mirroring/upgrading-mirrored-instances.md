---
title: サーバーインスタンスをアップグレードするときに、ミラー化されたデータベースのダウンタイムを最小限に抑える |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server, rolling upgrade of mirrored databases
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
ms.assetid: 0e73bd23-497d-42f1-9e81-8d5314bcd597
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0a343e6b9e93aa1910c82f436f3a50daf00d57bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639649"
---
# <a name="minimize-downtime-for-mirrored-databases-when-upgrading-server-instances"></a><span data-ttu-id="a6dff-102">サーバー インスタンスのアップグレード時に、ミラー化されたデータベースのダウンタイムを最小化する方法</span><span class="sxs-lookup"><span data-stu-id="a6dff-102">Minimize Downtime for Mirrored Databases When Upgrading Server Instances</span></span>
  <span data-ttu-id="a6dff-103">サーバーインスタンスをにアップグレードする場合 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、*ローリングアップグレード*と呼ばれる順次アップグレードを実行することで、ミラー化された各データベースのダウンタイムを1回の手動フェールオーバーのみに減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="a6dff-103">When upgrading server instances to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can reduce downtime for each mirrored database to only a single manual failover by performing a sequential upgrade, known as a *rolling upgrade*.</span></span> <span data-ttu-id="a6dff-104">ローリング アップグレードは複数の段階から成るプロセスです。最も単純な形式では、ミラーリング セッションで現在ミラー サーバーとして機能しているサーバー インスタンスをアップグレードした後、ミラー化されたデータベースを手動でフェールオーバーし、以前のプリンシパル サーバーをアップグレードして、ミラーリングを再開します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-104">A rolling upgrade is a multi-stage process that in its simplest form involves upgrading the server instance that is currently acting as the mirror server in a mirroring session, then manually failing over the mirrored database, upgrading the former principal server, and resuming mirroring.</span></span> <span data-ttu-id="a6dff-105">実際に実行するプロセスは、動作モードと、アップグレードするサーバー インスタンスで実行しているミラーリング セッションの数やレイアウトによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-105">In practice, the exact process will depend on the operating mode and the number and layout of mirroring session running on the server instances that you are upgrading.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6dff-106">ローリングアップグレードを実行して Service Pack または修正プログラムをインストールする方法については、「[ミラー化されたデータベースのダウンタイムを最小限に抑えてシステムに Service pack をインストール](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6dff-106">For information about performing a rolling upgrade to install a service pack or hotfix, see [Install a Service Pack on a System with Minimal Downtime for Mirrored Databases](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md).</span></span>  
  
 <span data-ttu-id="a6dff-107">**推奨される準備 (ベスト プラクティス)**</span><span class="sxs-lookup"><span data-stu-id="a6dff-107">**Recommended Preparation (Best Practices)**</span></span>  
  
 <span data-ttu-id="a6dff-108">ローリング アップグレードを開始する前に以下を実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a6dff-108">Before starting a rolling upgrade, we recommend that you:</span></span>  
  
1.  <span data-ttu-id="a6dff-109">少なくとも 1 つのミラーリング セッションで試験的に手動フェールオーバーを実行します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-109">Perform a practice manual failover on at least one of your mirroring sessions:</span></span>  
  
    -   [<span data-ttu-id="a6dff-110">データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a6dff-110">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="a6dff-111">[データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="a6dff-111">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a6dff-112">手動フェールオーバーのしくみについては、「[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6dff-112">For information about how manual failover works, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="a6dff-113">データを保護します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-113">Protect your data:</span></span>  
  
    1.  <span data-ttu-id="a6dff-114">すべてのプリンシパル データベースを対象にデータベースの完全バックアップを実行します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-114">Perform a full database backup on every principal database:</span></span>  
  
         <span data-ttu-id="a6dff-115">[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="a6dff-115">[Create a Full Database Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
    2.  <span data-ttu-id="a6dff-116">すべてのプリンシパル データベースで [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-116">Run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on every principal database.</span></span>  
  
 <span data-ttu-id="a6dff-117">**ローリング アップグレードの段階**</span><span class="sxs-lookup"><span data-stu-id="a6dff-117">**Stages of a Rolling Upgrade**</span></span>  
  
 <span data-ttu-id="a6dff-118">ローリング アップグレードの個々の段階は、ミラーリング構成の動作モードによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-118">The specific steps of a rolling upgrade depend on the operating mode of the mirroring configuration.</span></span> <span data-ttu-id="a6dff-119">ただし、基本的な段階は同じです。</span><span class="sxs-lookup"><span data-stu-id="a6dff-119">However, the basic stages are the same.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6dff-120">動作モードの詳細については、「 [データベース ミラーリングの動作モード](database-mirroring-operating-modes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6dff-120">For information about the operating modes, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="a6dff-121">次の図は、動作モードごとにローリング アップグレードの基本的な段階をフローチャートで示したものです。</span><span class="sxs-lookup"><span data-stu-id="a6dff-121">The following illustration is a flowchart that shows the basic stages of a rolling upgrade for each operating mode.</span></span> <span data-ttu-id="a6dff-122">図の後で、対応する各手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-122">The corresponding procedures are described after the illustration.</span></span>  
  
 <span data-ttu-id="a6dff-123">![ローリング アップグレードの手順を示すフローチャート](../media/dbm-rolling-upgrade.gif "ローリング アップグレードの手順を示すフローチャート")</span><span class="sxs-lookup"><span data-stu-id="a6dff-123">![Flowchart showing steps of a rolling upgrade](../media/dbm-rolling-upgrade.gif "Flowchart showing steps of a rolling upgrade")</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a6dff-124">同時実行ミラーリング セッションでは、1 つのサーバー インスタンスが複数の異なるミラーリング ロール (プリンシパル サーバー、ミラー サーバー、またはミラーリング監視サーバー) を実行している場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-124">A server instance might be performing different mirroring roles (principal server, mirror server, or witness) in concurrent mirroring sessions.</span></span> <span data-ttu-id="a6dff-125">この場合は、基本的なローリング アップグレード プロセスを適宜調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-125">In this case, you will have to adapt the basic rolling upgrade process accordingly.</span></span> <span data-ttu-id="a6dff-126">詳細については、「 [データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="a6dff-126">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a><span data-ttu-id="a6dff-127">セッションを高パフォーマンス モードから高い安全性モードに変更するには</span><span class="sxs-lookup"><span data-stu-id="a6dff-127">To change a session from high-performance mode to high-safety mode</span></span>  
  
1.  <span data-ttu-id="a6dff-128">ミラーリング セッションを高パフォーマンス モードで実行している場合は、ローリング アップグレードを実行する前に、動作モードを、自動フェールオーバーを伴わない高い安全性モードに変更します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-128">If a mirroring session is running in high-performance mode, before you perform a rolling upgrade, change the operating mode to high safety without automatic failover.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a6dff-129">ミラー サーバーとプリンシパル サーバーが地理的に離れている場合は、ローリング アップグレードは適しません。</span><span class="sxs-lookup"><span data-stu-id="a6dff-129">If the mirror server is geographically distant from the principal server, a rolling upgrade might be inappropriate.</span></span>  
  
    -   <span data-ttu-id="a6dff-130">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: **[データベースのプロパティ]** ダイアログ ボックスの [[ミラーリング]](../../relational-databases/databases/database-properties-mirroring-page.md) ページで、 **[動作モード]** オプションを **[自動フェールオーバーを伴わない高い安全性 (同期)]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-130">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High safety without automatic failover (synchronous)** by using the [Mirroring Page](../../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span> <span data-ttu-id="a6dff-131">このページにアクセスする方法については、「[データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6dff-131">For information about how to access this page, see [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md).</span></span>  
  
    -   <span data-ttu-id="a6dff-132">[!INCLUDE[tsql](../../includes/tsql-md.md)]: トランザクションの安全性を FULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-132">In [!INCLUDE[tsql](../../includes/tsql-md.md)]: Set transaction safety to FULL.</span></span> <span data-ttu-id="a6dff-133">詳細については、｢[データベース ミラーリング セッションでのトランザクションの安全性の変更 &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6dff-133">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)</span></span>  
  
### <a name="to-remove-a-witness-from-a-session"></a><span data-ttu-id="a6dff-134">ミラーリング監視サーバーをセッションから削除するには</span><span class="sxs-lookup"><span data-stu-id="a6dff-134">To remove a witness from a session</span></span>  
  
1.  <span data-ttu-id="a6dff-135">ミラーリング セッションにミラーリング監視サーバーが存在する場合は、ローリング アップグレードの実行前にミラーリング監視サーバーを削除しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a6dff-135">If a mirroring session involves a witness, we recommend that you remove the witness before you perform a rolling upgrade.</span></span> <span data-ttu-id="a6dff-136">そうしないと、ミラー サーバー インスタンスをアップグレードする際のデータベースの可用性が、プリンシパル サーバー インスタンスに接続されたミラーリング監視サーバーに依存することになります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-136">Otherwise, when the mirror server instance is being upgraded, database availability depends on the witness that remains connected to the principal server instance.</span></span> <span data-ttu-id="a6dff-137">削除したミラーリング監視サーバーは、ローリング アップグレード プロセス中にいつでもアップグレードでき、また、そうすることでデータベースのダウンタイムを最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="a6dff-137">After you remove a witness, you can upgrade it at any time during the rolling upgrade process without risking database downtime.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a6dff-138">詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 (データベース ミラーリング)](quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6dff-138">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
    -   [<span data-ttu-id="a6dff-139">データベース ミラーリング セッションからのミラーリング監視サーバーの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a6dff-139">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-perform-the-rolling-upgrade"></a><span data-ttu-id="a6dff-140">ローリング アップグレードを実行するには</span><span class="sxs-lookup"><span data-stu-id="a6dff-140">To perform the rolling upgrade</span></span>  
  
1.  <span data-ttu-id="a6dff-141">ダウンタイムを最小限に抑えるため、次をお勧めします: ローリング アップグレードを開始する際は、すべてのミラーリング セッションにおいてミラー サーバーとして機能しているミラーリング パートナーから先に更新します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-141">To minimize downtime, we recommend the following: Start the rolling upgrade by updating any mirroring partner that is currently the mirror server in all its mirroring sessions.</span></span> <span data-ttu-id="a6dff-142">場合によっては、この時点で複数のサーバー インスタンスを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-142">You might have to update multiple server instances at this point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a6dff-143">ミラーリング監視サーバーは、ローリング アップグレード プロセス中、いつでもアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="a6dff-143">A witness can be upgraded at any point in the rolling upgrade process.</span></span> <span data-ttu-id="a6dff-144">たとえば、セッション 1 ではミラー サーバーとして、セッション 2 ではミラーリング監視サーバーとして機能しているサーバー インスタンスであれば、今すぐにアップグレードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a6dff-144">For example, if a server instance is a mirror server in Session 1 and is a witness in Session 2, you can upgrade the server instance now.</span></span>  
  
     <span data-ttu-id="a6dff-145">最初にアップグレードするサーバー インスタンスは、ミラーリング セッションが現在どのように構成されているかによって異なります。その指針を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-145">The server instance to upgrade first depends on the current configuration of your mirroring sessions, as follows:</span></span>  
  
    -   <span data-ttu-id="a6dff-146">サーバー インスタンスがそのすべてのミラーリング セッションにおいて既にミラー サーバーとして機能している場合、そのサーバー インスタンスを新しいバージョンにアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="a6dff-146">If any server instance is already the mirror server in all its mirroring sessions, upgrade the server instance to the new version.</span></span>  
  
    -   <span data-ttu-id="a6dff-147">どのサーバー インスタンスもいずれかのミラーリング セッションのプリンシパル サーバーとして機能している場合は、最初にアップグレードするサーバー インスタンスを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-147">If all your server instances are currently the principal server in any mirroring sessions, select one server instance to upgrade first.</span></span> <span data-ttu-id="a6dff-148">次に、選択したサーバー インスタンスの各プリンシパル データベースを手動でフェールオーバーし、そのサーバー インスタンスをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="a6dff-148">Then, manually fail over each of its principal databases and upgrade that server instance.</span></span>  
  
     <span data-ttu-id="a6dff-149">アップグレード後のサーバー インスタンスは、自動的にそれぞれのミラーリング セッションに再度参加します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-149">After being upgraded, a server instance automatically rejoins each of its mirroring sessions.</span></span>  
  
2.  <span data-ttu-id="a6dff-150">前の手順でアップグレードしたミラー サーバー インスタンスのすべてのミラーリング セッションの同期が完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="a6dff-150">For each mirroring session whose mirror server instance has just been upgraded, wait for the session to synchronize.</span></span> <span data-ttu-id="a6dff-151">次に、プリンシパル サーバー インスタンスに接続し、セッションを手動でフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="a6dff-151">Then, connect to the principal server instance, and manually fail over the session.</span></span> <span data-ttu-id="a6dff-152">フェールオーバー時は、アップグレードされたサーバー インスタンスがそのセッションのプリンシパル サーバーになり、以前のプリンシパル サーバーがミラー サーバーになります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-152">On failover, the upgraded server instance becomes the principal server for that session, and the former principal server becomes the mirror server.</span></span>  
  
     <span data-ttu-id="a6dff-153">この手順の目的は、すべてのミラーリング セッションで、パートナー関係にある他方のサーバー インスタンスがミラー サーバーとなるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="a6dff-153">The goal of this step is for another server instance to become the mirror server in every mirroring session in which it is a partner.</span></span>  
  
     <span data-ttu-id="a6dff-154">**アップグレードしたサーバー インスタンスに対するフェールオーバー後の制限**</span><span class="sxs-lookup"><span data-stu-id="a6dff-154">**Restrictions after you failover to an upgraded server instance.**</span></span>  
  
     <span data-ttu-id="a6dff-155">以前のサーバー インスタンスから [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のサーバー インスタンスにフェールオーバーした後は、データベース セッションが中断されます。</span><span class="sxs-lookup"><span data-stu-id="a6dff-155">After failing over from an earlier server instance to a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] server instance, the database session is suspended.</span></span> <span data-ttu-id="a6dff-156">もう一方のパートナーがアップグレードされるまで再開できません。</span><span class="sxs-lookup"><span data-stu-id="a6dff-156">It cannot be resumed until the other partner has been upgraded.</span></span> <span data-ttu-id="a6dff-157">ただし、プリンシパル サーバーは引き続き接続を受け入れ、プリンシパル データベースに対するデータのアクセスや変更は許可されます。</span><span class="sxs-lookup"><span data-stu-id="a6dff-157">However, the principal server is still accepting connections and allowing data access and modifications on the principal database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a6dff-158">新しいミラーリング セッションを確立するには、すべてのサーバー インスタンスが同じバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-158">Establishing a new mirroring session requires that the server instances all be running the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="a6dff-159">フェールオーバー後は、プリンシパルデータベースで[DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)コマンドを実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a6dff-159">After you fail over, we recommend that you run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on theprincipal database.</span></span>  
  
4.  <span data-ttu-id="a6dff-160">すべてのミラーリング セッションにおいて、現在ミラー サーバー (パートナー) となっている各サーバー インスタンスをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="a6dff-160">Upgrade each server instance that is now the mirror server in all mirroring sessions in which it is a partner.</span></span> <span data-ttu-id="a6dff-161">場合によっては、この時点で複数のサーバーを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-161">You might have to update multiple servers at this point.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a6dff-162">複雑なミラーリング構成の場合、一部のサーバー インスタンスが、1 つまたは複数のミラーリング セッションで元のプリンシパル サーバーとして機能している場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-162">In a complex mirroring configuration, some server instance might still be the original principal server in one or more mirroring sessions.</span></span> <span data-ttu-id="a6dff-163">これらのサーバー インスタンスについては、関係するすべてのインスタンスがアップグレードされるまで、手順 2 から手順 4 までを繰り返してください。</span><span class="sxs-lookup"><span data-stu-id="a6dff-163">Repeat steps 2-4 for those server instances until all instances involved are upgraded.</span></span>  
  
5.  <span data-ttu-id="a6dff-164">ミラーリング セッションを再開します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-164">Resume the mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a6dff-165">自動フェールオーバーは、ミラーリング監視サーバーがアップグレードされてミラーリング セッションに戻されるまで機能しません。</span><span class="sxs-lookup"><span data-stu-id="a6dff-165">Automatic failover will not work until the witness has been upgraded and added back into the mirroring session.</span></span>  
  
6.  <span data-ttu-id="a6dff-166">すべてのミラーリング セッションの残りのサーバー インスタンス (ミラーリング監視サーバー) をアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="a6dff-166">Upgrade any remaining server instance that is the witness in all its mirroring sessions.</span></span> <span data-ttu-id="a6dff-167">アップグレードしたミラーリング監視サーバーをミラーリング セッションに再度参加させると、自動フェールオーバーが有効になります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-167">After an upgraded witness rejoins a mirroring session, automatic failover becomes possible again.</span></span> <span data-ttu-id="a6dff-168">場合によっては、この時点で複数のサーバーを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6dff-168">You might have to update multiple servers at this point.</span></span>  
  
### <a name="to-return-a-session-to-high-performance-mode"></a><span data-ttu-id="a6dff-169">セッションを高パフォーマンス モードに戻すには</span><span class="sxs-lookup"><span data-stu-id="a6dff-169">To return a session to high-performance mode</span></span>  
  
1.  <span data-ttu-id="a6dff-170">必要に応じて、高パフォーマンス モードに戻す場合は、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-170">Optionally, return to high-performance mode by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a6dff-171">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページで、[[動作モード]](../../relational-databases/databases/database-properties-mirroring-page.md) オプションを **[高パフォーマンス (非同期)]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-171">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High performance (asynchronous)** by using the [Mirroring Page](../../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="a6dff-172">[!INCLUDE[tsql](../../includes/tsql-md.md)]: [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) を使用してトランザクションの安全性を OFF に設定します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-172">In [!INCLUDE[tsql](../../includes/tsql-md.md)]: Use [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)to set transaction safety to OFF.</span></span>  
  
### <a name="to-add-a-witness-back-into-a-mirroring-session"></a><span data-ttu-id="a6dff-173">ミラーリング監視サーバーをミラーリング セッションに戻すには</span><span class="sxs-lookup"><span data-stu-id="a6dff-173">To add a witness back into a mirroring session</span></span>  
  
1.  <span data-ttu-id="a6dff-174">必要に応じて、高い安全性モードで、各ミラーリング セッションのミラーリング監視サーバーを再度確立します。</span><span class="sxs-lookup"><span data-stu-id="a6dff-174">Optionally, in high-safety mode, reestablish the witness to each mirroring session.</span></span>  
  
     <span data-ttu-id="a6dff-175">**ミラーリング監視サーバーをセッションに戻すには**</span><span class="sxs-lookup"><span data-stu-id="a6dff-175">**To return a witness**</span></span>  
  
    -   [<span data-ttu-id="a6dff-176">データベース ミラーリング監視サーバーを追加または置き換える方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a6dff-176">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="a6dff-177">Windows 認証を使用してデータベースのミラーリング監視を追加する &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a6dff-177">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="a6dff-178">参照</span><span class="sxs-lookup"><span data-stu-id="a6dff-178">See Also</span></span>  
 <span data-ttu-id="a6dff-179">[ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="a6dff-179">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="a6dff-180">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6dff-180">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="a6dff-181">[ミラー化されたデータベースの状態の確認 &#40;SQL Server Management Studio&#41;](view-the-state-of-a-mirrored-database-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a6dff-181">[View the State of a Mirrored Database &#40;SQL Server Management Studio&#41;](view-the-state-of-a-mirrored-database-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="a6dff-182">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a6dff-182">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="a6dff-183">[ミラー化されたデータベースのダウンタイムを最小限に抑えて、システムに Service Pack をインストールする](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md) </span><span class="sxs-lookup"><span data-stu-id="a6dff-183">[Install a Service Pack on a System with Minimal Downtime for Mirrored Databases](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md) </span></span>  
 <span data-ttu-id="a6dff-184">[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a6dff-184">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="a6dff-185">[データベース ミラーリング セッションでのサービスの強制 &#40;Transact-SQL&#41;](force-service-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="a6dff-185">[Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;](force-service-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="a6dff-186">[データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a6dff-186">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="a6dff-187">Database Mirroring Operating Modes</span><span class="sxs-lookup"><span data-stu-id="a6dff-187">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
