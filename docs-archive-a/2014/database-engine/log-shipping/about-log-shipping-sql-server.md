---
title: ログ配布について (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary servers [SQL Server]
- log shipping [SQL Server], jobs
- copy jobs [SQL Server]
- primary databases [SQL Server]
- log shipping [SQL Server], monitoring
- log shipping [SQL Server], about log shipping
- alert jobs [SQL Server]
- availability [SQL Server]
- jobs [SQL Server], log shipping
- monitor servers [SQL Server]
- restore jobs [SQL Server]
- log shipping [SQL Server]
- backup jobs [SQL Server]
- primary servers [SQL Server]
ms.assetid: 55da6b94-3a4b-4bae-850f-4bf7f6e918ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbf36e0ddd94ec0ab0a40a448e50602decfc0645
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714550"
---
# <a name="about-log-shipping-sql-server"></a><span data-ttu-id="12627-102">ログ配布について (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="12627-102">About Log Shipping (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="12627-103">のログ配布を使用すると、トランザクション ログ バックアップを、 *プライマリ サーバー* インスタンスの *プライマリ データベース* から、別の *セカンダリ サーバー* インスタンスの 1 つ以上の *セカンダリ データベース* に自動的に送信できます。</span><span class="sxs-lookup"><span data-stu-id="12627-103">Log shipping allows you to automatically send transaction log backups from a *primary database* on a *primary server* instance to one or more *secondary databases* on separate *secondary server* instances.</span></span> <span data-ttu-id="12627-104">トランザクション ログ バックアップはセカンダリ データベースごとに個別に適用されます。</span><span class="sxs-lookup"><span data-stu-id="12627-104">The transaction log backups are applied to each of the secondary databases individually.</span></span> <span data-ttu-id="12627-105">オプションで用意する 3 台目のサーバー インスタンス ( *監視サーバー*) では、バックアップ操作と復元操作の履歴と状態が記録されます。また、これらの操作がスケジュールどおりに実行されなかった場合に警告を通知することもできます。</span><span class="sxs-lookup"><span data-stu-id="12627-105">An optional third server instance, known as the *monitor server*, records the history and status of backup and restore operations and, optionally, raises alerts if these operations fail to occur as scheduled.</span></span>  
  
 <span data-ttu-id="12627-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="12627-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="12627-107">メリット</span><span class="sxs-lookup"><span data-stu-id="12627-107">Benefits</span></span>](#Benefits)  
  
-   [<span data-ttu-id="12627-108">用語と定義</span><span class="sxs-lookup"><span data-stu-id="12627-108">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="12627-109">ログ配布の概要</span><span class="sxs-lookup"><span data-stu-id="12627-109">Log Shipping Overview</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="12627-110">相互運用性</span><span class="sxs-lookup"><span data-stu-id="12627-110">Interoperability</span></span>](#Interoperability)  
  
-   [<span data-ttu-id="12627-111">関連タスク</span><span class="sxs-lookup"><span data-stu-id="12627-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="12627-112">利点</span><span class="sxs-lookup"><span data-stu-id="12627-112">Benefits</span></span>  
  
-   <span data-ttu-id="12627-113">1 つのプライマリ データベースと 1 つ以上のセカンダリ データベース (それぞれが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の個別のインスタンスに存在) で構成される災害復旧ソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="12627-113">Provides a disaster-recovery solution for a single primary database and one or more secondary databases, each on a separate instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="12627-114">復元ジョブの間のセカンダリ データベースへの制限付きの読み取り専用アクセスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="12627-114">Supports limited read-only access to secondary databases (during the interval between restore jobs).</span></span>  
  
-   <span data-ttu-id="12627-115">プライマリ サーバーでプライマリ データベースのログをバックアップする時点と、セカンダリ サーバーがそのログ バックアップを復元 (適用) する時点との間に生じる遅延時間をユーザーが指定できます。</span><span class="sxs-lookup"><span data-stu-id="12627-115">Allows a user-specified delay between when the primary server backs up the log of the primary database and when the secondary servers must restore (apply) the log backup.</span></span> <span data-ttu-id="12627-116">たとえば、プライマリ データベースでデータが誤って変更された場合などに、長い遅延が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="12627-116">A longer delay can be useful, for example, if data is accidentally changed on the primary database.</span></span> <span data-ttu-id="12627-117">誤った変更にすぐに気付いた場合、遅延があれば、変更が反映される前に、セカンダリ データベースにあるまだ変更されていないデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="12627-117">If the accidental change is noticed quickly, a delay can let you retrieve still unchanged data from a secondary database before the change is reflected there.</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="12627-118">用語と定義</span><span class="sxs-lookup"><span data-stu-id="12627-118">Terms and Definitions</span></span>  
 <span data-ttu-id="12627-119">プライマリ データベース</span><span class="sxs-lookup"><span data-stu-id="12627-119">primary server</span></span>  
 <span data-ttu-id="12627-120">実稼働サーバーである [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="12627-120">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is your production server.</span></span>  
  
 <span data-ttu-id="12627-121">プライマリ データベース</span><span class="sxs-lookup"><span data-stu-id="12627-121">primary database</span></span>  
 <span data-ttu-id="12627-122">別のサーバーにバックアップするプライマリ サーバーのデータベース。</span><span class="sxs-lookup"><span data-stu-id="12627-122">The database on the primary server that you want to back up to another server.</span></span> <span data-ttu-id="12627-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用したログ配布構成の管理は、すべてプライマリ データベースから実行されます。</span><span class="sxs-lookup"><span data-stu-id="12627-123">All administration of the log shipping configuration through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is performed from the primary database.</span></span>  
  
 <span data-ttu-id="12627-124">セカンダリ データベース</span><span class="sxs-lookup"><span data-stu-id="12627-124">secondary server</span></span>  
 <span data-ttu-id="12627-125">プライマリ データベースのウォーム スタンバイ コピーを保持しておく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="12627-125">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where you want to keep a warm standby copy of your primary database.</span></span>  
  
 <span data-ttu-id="12627-126">セカンダリ データベース (secondary database)</span><span class="sxs-lookup"><span data-stu-id="12627-126">secondary database</span></span>  
 <span data-ttu-id="12627-127">プライマリ データベースのウォーム スタンバイ コピー。</span><span class="sxs-lookup"><span data-stu-id="12627-127">The warm standby copy of the primary database.</span></span> <span data-ttu-id="12627-128">セカンダリ データベースは、RECOVERING と STANDBY のどちらかの状態にすることができます。この状態では、データベースを制限付きの読み取り専用アクセスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="12627-128">The secondary database may be in either the RECOVERING state or the STANDBY state, which leaves the database available for limited read-only access.</span></span>  
  
 <span data-ttu-id="12627-129">監視サーバー</span><span class="sxs-lookup"><span data-stu-id="12627-129">monitor server</span></span>  
 <span data-ttu-id="12627-130">ログ配布に関する次の詳細情報をすべて追跡する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のオプションのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="12627-130">An optional instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that tracks all of the details of log shipping, including:</span></span>  
  
-   <span data-ttu-id="12627-131">プライマリ データベースのトランザクション ログが最後にバックアップされた日時</span><span class="sxs-lookup"><span data-stu-id="12627-131">When the transaction log on the primary database was last backed up.</span></span>  
  
-   <span data-ttu-id="12627-132">セカンダリ サーバーでバックアップ ファイルが最後にコピーおよび復元された日時</span><span class="sxs-lookup"><span data-stu-id="12627-132">When the secondary servers last copied and restored the backup files.</span></span>  
  
-   <span data-ttu-id="12627-133">バックアップ障害の警告に関する情報</span><span class="sxs-lookup"><span data-stu-id="12627-133">Information about any backup failure alerts.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="12627-134">監視サーバーは、一度構成すると、最初にログ配布を削除しない限り変更できません。</span><span class="sxs-lookup"><span data-stu-id="12627-134">Once the monitor server has been configured, it cannot be changed without removing log shipping first.</span></span>  
  
 <span data-ttu-id="12627-135">バックアップ ジョブ (backup job)</span><span class="sxs-lookup"><span data-stu-id="12627-135">backup job</span></span>  
 <span data-ttu-id="12627-136">バックアップ操作の実行、ローカル サーバーと監視サーバーへの履歴ログの記録、および古いバックアップ ファイルと履歴情報の削除を行う [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ。</span><span class="sxs-lookup"><span data-stu-id="12627-136">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that  performs the backup operation, logs history to the local server and the monitor server, and deletes old backup files and history information.</span></span> <span data-ttu-id="12627-137">ジョブ カテゴリの "ログ配布のバックアップ" は、ログ配布を有効にしたときにプライマリ サーバー インスタンスで作成されます。</span><span class="sxs-lookup"><span data-stu-id="12627-137">When log shipping is enabled, the job category "Log Shipping Backup" is created on the primary server instance.</span></span>  
  
 <span data-ttu-id="12627-138">コピー ジョブ (copy job)</span><span class="sxs-lookup"><span data-stu-id="12627-138">copy job</span></span>  
 <span data-ttu-id="12627-139">プライマリ サーバーからセカンダリ サーバーの構成可能なコピー先にバックアップ ファイルをコピーし、セカンダリ サーバーと監視サーバーの履歴ログを記録する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ。</span><span class="sxs-lookup"><span data-stu-id="12627-139">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that copies the backup files from the primary server to a configurable destination on the secondary server and logs history on the secondary server and the monitor server.</span></span> <span data-ttu-id="12627-140">ジョブ カテゴリの "ログ配布のコピー" は、データベースでログ配布を有効にしたときに各セカンダリ サーバーのログ配布構成で作成されます。</span><span class="sxs-lookup"><span data-stu-id="12627-140">When log shipping is enabled on a database, the job category "Log Shipping Copy" is created on each secondary server in a log shipping configuration.</span></span>  
  
 <span data-ttu-id="12627-141">復元ジョブ (restore job)</span><span class="sxs-lookup"><span data-stu-id="12627-141">restore job</span></span>  
 <span data-ttu-id="12627-142">コピーされたバックアップ ファイルをセカンダリ データベースに復元する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ。</span><span class="sxs-lookup"><span data-stu-id="12627-142">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that restores the copied backup files to the secondary databases.</span></span> <span data-ttu-id="12627-143">この操作により、ローカル サーバーと監視サーバーの履歴ログが記録され、古いファイルと履歴情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="12627-143">It logs history on the local server and the monitor server, and deletes old files and old history information.</span></span> <span data-ttu-id="12627-144">ジョブ カテゴリの "ログ配布のログ復元" は、データベースでログ配布を有効にしたときにセカンダリ サーバー インスタンスで作成されます。</span><span class="sxs-lookup"><span data-stu-id="12627-144">When log shipping is enabled on a database, the job category "Log Shipping Restore" is created on the secondary server instance.</span></span>  
  
 <span data-ttu-id="12627-145">警告ジョブ (alert job)</span><span class="sxs-lookup"><span data-stu-id="12627-145">alert job</span></span>  
 <span data-ttu-id="12627-146">バックアップと復元操作が指定したしきい値の範囲内で完了しない場合に、プライマリ データベースとセカンダリ データベースに対する警告を通知する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ。</span><span class="sxs-lookup"><span data-stu-id="12627-146">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that raises alerts for primary and secondary databases when a backup or restore operation does not complete successfully within a specified threshold.</span></span> <span data-ttu-id="12627-147">ジョブ カテゴリの "ログ配布の警告" は、データベースでログ配布を有効にしたときに監視サーバー インスタンスで作成されます。</span><span class="sxs-lookup"><span data-stu-id="12627-147">When log shipping is enabled on a database, job category "Log Shipping Alert" is created on the monitor server instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="12627-148">警告 1 件につき警告番号を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12627-148">For each alert, you need to specify an alert number.</span></span> <span data-ttu-id="12627-149">また、警告が発生するとオペレーターに通知されるよう警告を構成してください。</span><span class="sxs-lookup"><span data-stu-id="12627-149">Also, be sure to configure the alert to notify an operator when an alert is raised.</span></span>  
  
##  <a name="log-shipping-overview"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="12627-150">ログ配布の概要</span><span class="sxs-lookup"><span data-stu-id="12627-150">Log Shipping Overview</span></span>  
 <span data-ttu-id="12627-151">ログ配布は、次に示す 3 つの操作から構成されます。</span><span class="sxs-lookup"><span data-stu-id="12627-151">Log shipping consists of three operations:</span></span>  
  
1.  <span data-ttu-id="12627-152">プライマリ サーバー インスタンスでトランザクション ログをバックアップする。</span><span class="sxs-lookup"><span data-stu-id="12627-152">Back up the transaction log at the primary server instance.</span></span>  
  
2.  <span data-ttu-id="12627-153">セカンダリ サーバー インスタンスにトランザクション ログ ファイルをコピーする。</span><span class="sxs-lookup"><span data-stu-id="12627-153">Copy the transaction log file to the secondary server instance.</span></span>  
  
3.  <span data-ttu-id="12627-154">セカンダリ サーバー インスタンスでログ バックアップを復元する。</span><span class="sxs-lookup"><span data-stu-id="12627-154">Restore the log backup on the secondary server instance.</span></span>  
  
 <span data-ttu-id="12627-155">ログは、複数のセカンダリ サーバー インスタンスに配布できます。</span><span class="sxs-lookup"><span data-stu-id="12627-155">The log can be shipped to multiple secondary server instances.</span></span> <span data-ttu-id="12627-156">その場合、操作 2. と操作 3. が各セカンダリ サーバー インスタンスに対して繰り返し実行されます。</span><span class="sxs-lookup"><span data-stu-id="12627-156">In such cases, operations 2 and 3 are duplicated for each secondary server instance.</span></span>  
  
 <span data-ttu-id="12627-157">ログ配布構成は、自動的にはプライマリ サーバーからセカンダリ サーバーにフェールオーバーされません。</span><span class="sxs-lookup"><span data-stu-id="12627-157">A log shipping configuration does not automatically fail over from the primary server to the secondary server.</span></span> <span data-ttu-id="12627-158">プライマリ データベースが使用できなくなった場合は、任意のセカンダリ データベースを手動でオンラインにできます。</span><span class="sxs-lookup"><span data-stu-id="12627-158">If the primary database becomes unavailable, any of the secondary databases can be brought online manually.</span></span>  
  
 <span data-ttu-id="12627-159">セカンダリ データベースをレポート作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="12627-159">You can use a secondary database for reporting purposes.</span></span>  
  
 <span data-ttu-id="12627-160">さらに、ログ配布構成の警告を構成できます。</span><span class="sxs-lookup"><span data-stu-id="12627-160">In addition, you can configure alerts for your log shipping configuration.</span></span>  
  
### <a name="a-typical-log-shipping-configuration"></a><span data-ttu-id="12627-161">通常のログ配布構成</span><span class="sxs-lookup"><span data-stu-id="12627-161">A Typical Log Shipping Configuration</span></span>  
 <span data-ttu-id="12627-162">次の図に、プライマリ サーバー インスタンス、3 台のセカンダリ サーバー インスタンス、および監視サーバー インスタンスを使用するログ配布構成を示します。</span><span class="sxs-lookup"><span data-stu-id="12627-162">The following figure shows a log shipping configuration with the primary server instance, three secondary server instances, and a monitor server instance.</span></span> <span data-ttu-id="12627-163">この図に示されているバックアップ ジョブ、コピー ジョブ、および復元ジョブの実行手順は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="12627-163">The figure illustrates the steps performed by backup, copy, and restorejobs, as follows:</span></span>  
  
1.  <span data-ttu-id="12627-164">プライマリ サーバー インスタンスがバックアップ ジョブを実行し、プライマリ データベースのトランザクション ログをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="12627-164">The primary server instance runs the backup job to back up the transaction log on the primary database.</span></span> <span data-ttu-id="12627-165">このサーバー インスタンスは、次にログ バックアップをプライマリ ログ バックアップ ファイルに配置し、バックアップ フォルダーに送信します。</span><span class="sxs-lookup"><span data-stu-id="12627-165">This server instance then places the log backup into a primary log-backup file, which it sends to the backup folder.</span></span>  <span data-ttu-id="12627-166">この図では、バックアップ フォルダーは共有ディレクトリ ("*バックアップ共有*") にあります。</span><span class="sxs-lookup"><span data-stu-id="12627-166">In this figure, the backup folder is on a shared directory-the *backup share*.</span></span>  
  
2.  <span data-ttu-id="12627-167">3 台のセカンダリ サーバー インスタンスは、それぞれのコピー ジョブを実行し、プライマリ ログ バックアップ ファイルをローカルのコピー先フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="12627-167">Each of the three secondary server instances runs its own copy job to copy the primary log-backup file to its own local destination folder.</span></span>  
  
3.  <span data-ttu-id="12627-168">各セカンダリ サーバー インスタンスは、それぞれの復元ジョブを実行し、ログ バックアップをローカルのコピー先フォルダーからローカル セカンダリ データベースに復元します。</span><span class="sxs-lookup"><span data-stu-id="12627-168">Each secondary server instance runs its own restore job to restore the log backup from the local destination folder onto the local secondary database.</span></span>  
  
 <span data-ttu-id="12627-169">プライマリ サーバー インスタンスおよびセカンダリ サーバー インスタンスは、それぞれの履歴および状態を監視サーバー インスタンスに送信します。</span><span class="sxs-lookup"><span data-stu-id="12627-169">The primary and secondary server instances send their own history and status to the monitor server instance.</span></span>  
  
 <span data-ttu-id="12627-170">![ジョブのバックアップ、コピー、復元を示す構成](../media/ls-typical-configuration.gif "ジョブのバックアップ、コピー、復元を示す構成")</span><span class="sxs-lookup"><span data-stu-id="12627-170">![Configuration showing backup, copy, & restore jobs](../media/ls-typical-configuration.gif "Configuration showing backup, copy, & restore jobs")</span></span>  
  
##  <a name="interoperability"></a><a name="Interoperability"></a> <span data-ttu-id="12627-171">相互運用性</span><span class="sxs-lookup"><span data-stu-id="12627-171">Interoperability</span></span>  
 <span data-ttu-id="12627-172">ログ配布は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の次の機能またはコンポーネントと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="12627-172">Log shipping can be used with the following features or components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="12627-173">ログ配布から AlwaysOn 可用性グループ &#40;SQL Server への移行の前提条件&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-173">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../availability-groups/windows/prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
-   [<span data-ttu-id="12627-174">データベース ミラーリングとログ配布 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-174">Database Mirroring and Log Shipping &#40;SQL Server&#41;</span></span>](../database-mirroring/database-mirroring-and-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="12627-175">ログ配布とレプリケーション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-175">Log Shipping and Replication &#40;SQL Server&#41;</span></span>](log-shipping-and-replication-sql-server.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] <span data-ttu-id="12627-176">とデータベース ミラーリングは、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="12627-176">and database mirroring are mutually exclusive.</span></span> <span data-ttu-id="12627-177">これらの機能のいずれかに対して構成されたデータベースを他の機能用に構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="12627-177">A database that is configured for one of these features cannot be configured for the other.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="12627-178">関連タスク</span><span class="sxs-lookup"><span data-stu-id="12627-178">Related Tasks</span></span>  
  
-   [<span data-ttu-id="12627-179">ログ配布を SQL Server 2014 &#40;Transact-sql&#41;にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="12627-179">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="12627-180">ログ配布の構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-180">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="12627-181">ログ配布構成へのセカンダリ データベースの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-181">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="12627-182">ログ配布構成からのセカンダリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-182">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="12627-183">ログ配布の削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-183">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="12627-184">ログ配布レポートの表示 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-184">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="12627-185">ログ配布の監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-185">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="12627-186">ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-186">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="12627-187">ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-187">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="12627-188">役割の交代後のログインとジョブの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-188">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="12627-189">参照</span><span class="sxs-lookup"><span data-stu-id="12627-189">See Also</span></span>  
 [<span data-ttu-id="12627-190">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="12627-190">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
