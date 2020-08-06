---
title: ミラーリングパフォーマンスメトリックで警告しきい値と警告を使用する (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- thresholds [SQL Server]
- database mirroring [SQL Server], managing in SQL Server Management Studio
- alerts [SQL Server], database mirroring
- database mirroring [SQL Server], monitoring
- warnings [database mirroring]
ms.assetid: 8cdd1515-0bd7-4f8c-a7fc-a33b575e20f6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 908b234143bc7e2140fe1c98d85ba150ea69b28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639636"
---
# <a name="use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server"></a><span data-ttu-id="a67a5-102">ミラーリング パフォーマンス基準の警告しきい値および警告の使用 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a67a5-102">Use Warning Thresholds and Alerts on Mirroring Performance Metrics (SQL Server)</span></span>
  <span data-ttu-id="a67a5-103">このトピックでは、データベース ミラーリング用に警告しきい値を構成および管理できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-103">This topic contains information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events for which warning thresholds can be configured and managed for database mirroring.</span></span> <span data-ttu-id="a67a5-104">データベース ミラーリング モニター、または **sp_dbmmonitorchangealert**、 **sp_dbmmonitorhelpalert**、および **sp_dbmmonitordropalert** の各ストアド プロシージャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-104">You can use the  Database Mirroring Monitor or the **sp_dbmmonitorchangealert**, **sp_dbmmonitorhelpalert**, and **sp_dbmmonitordropalert** stored procedures.</span></span> <span data-ttu-id="a67a5-105">また、データベース ミラーリング イベントの警告の構成についても説明します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-105">This topic also contains information about configuring alerts on database mirroring events.</span></span>  
  
 <span data-ttu-id="a67a5-106">ミラー化されたデータベースに対する監視が確立された後、システム管理者は、複数の主要なパフォーマンス基準に警告しきい値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-106">After monitoring is established for a mirrored database, a system administrator can configure warning thresholds on several key performance metrics.</span></span> <span data-ttu-id="a67a5-107">また、管理者は、これらの基準や他のデータベース ミラーリング イベントに基づいて警告を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-107">Also, an administrator can configure alerts on these and other database mirroring events.</span></span>  
  
 <span data-ttu-id="a67a5-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a67a5-108">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="a67a5-109">パフォーマンス基準と警告しきい値</span><span class="sxs-lookup"><span data-stu-id="a67a5-109">Performance Metrics and Warning Thresholds</span></span>](#PerfMetricsAndWarningThresholds)  
  
-   [<span data-ttu-id="a67a5-110">警告しきい値の設定と管理</span><span class="sxs-lookup"><span data-stu-id="a67a5-110">Setting Up and Managing Warning Thresholds</span></span>](#SetUpManageWarningThresholds)  
  
-   [<span data-ttu-id="a67a5-111">ミラー化されたデータベースに対する警告の使用</span><span class="sxs-lookup"><span data-stu-id="a67a5-111">Using Alerts for a Mirrored Database</span></span>](#UseAlerts)  
  
-   [<span data-ttu-id="a67a5-112">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a67a5-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="performance-metrics-and-warning-thresholds"></a><a name="PerfMetricsAndWarningThresholds"></a><span data-ttu-id="a67a5-113">パフォーマンスメトリックと警告しきい値</span><span class="sxs-lookup"><span data-stu-id="a67a5-113">Performance Metrics and Warning Thresholds</span></span>  
 <span data-ttu-id="a67a5-114">次の表では、警告を構成できるパフォーマンス基準、対応する警告しきい値、および対応するデータベース ミラーリング モニターのラベルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-114">The following table lists the performance metrics for which warnings can be configured, describes the corresponding warning threshold, and lists the corresponding Database Mirroring Monitor label.</span></span>  
  
|<span data-ttu-id="a67a5-115">パフォーマンス基準</span><span class="sxs-lookup"><span data-stu-id="a67a5-115">Performance metric</span></span>|<span data-ttu-id="a67a5-116">警告しきい値</span><span class="sxs-lookup"><span data-stu-id="a67a5-116">Warning threshold</span></span>|<span data-ttu-id="a67a5-117">データベース ミラーリング モデルのラベル</span><span class="sxs-lookup"><span data-stu-id="a67a5-117">Database Mirroring Monitor label</span></span>|  
|------------------------|-----------------------|--------------------------------------|  
|<span data-ttu-id="a67a5-118">未送信のログ</span><span class="sxs-lookup"><span data-stu-id="a67a5-118">Unsent log</span></span>|<span data-ttu-id="a67a5-119">未送信のログのサイズ (KB) を指定します。このサイズを超えると、プリンシパル サーバー インスタンスで警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-119">Specifies how many kilobytes (KB) of unsent log generate a warning on the principal server instance.</span></span> <span data-ttu-id="a67a5-120">この警告は、サイズの観点からデータ損失の可能性を測定するのに役立ち、特に、高パフォーマンス モードに関連しています。</span><span class="sxs-lookup"><span data-stu-id="a67a5-120">This warning helps measure the potential for data loss in terms of KB and is especially relevant for high-performance mode.</span></span> <span data-ttu-id="a67a5-121">パートナーとの通信が切断されたためにミラーリングが一時停止または中断している場合は、高安全モードにも関係します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-121">However, the warning is also relevant for high-safety mode when mirroring is paused or suspended because the partners become disconnected.</span></span>|<span data-ttu-id="a67a5-122">**[未送信のログがしきい値を超えた場合に警告する]**</span><span class="sxs-lookup"><span data-stu-id="a67a5-122">**Warn if the unsent log exceeds the threshold**</span></span>|  
|<span data-ttu-id="a67a5-123">未復元のログ</span><span class="sxs-lookup"><span data-stu-id="a67a5-123">Unrestored log</span></span>|<span data-ttu-id="a67a5-124">未復元のログのサイズ (KB) を指定します。このサイズを超えると、ミラー サーバー インスタンスで警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-124">Specifies how many KB of unrestored log generate a warning on the mirror server instance.</span></span> <span data-ttu-id="a67a5-125">この警告を使用すると、フェールオーバー時間を判断できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-125">This warning helps measure failover time.</span></span> <span data-ttu-id="a67a5-126">*フェールオーバー時間* の大部分は、以前のミラー サーバーの再実行キューに残っているログをロールフォワードする場合に必要となる時間です。この時間にわずかな時間を加えます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-126">*Failover time* consists mainly of the time that the former mirror server requires to roll forward any log remaining in its redo queue, plus a short additional time.</span></span><br /><br /> <span data-ttu-id="a67a5-127">注:自動フェールオーバーの場合、システムがエラーを通知するまでの時間は、フェールオーバー時間に関係ありません。</span><span class="sxs-lookup"><span data-stu-id="a67a5-127">Note: For an automatic failover, the time for the system to notice the error is independent of the failover time.</span></span><br /><br /> <span data-ttu-id="a67a5-128">詳しくは、「 [役割の交代中に発生するサービスの中断時間の算出 &#40;データベース ミラーリング&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)という処理により、一般的にプリンシパルとミラーの役割を相互交換できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-128">For more information, see [Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md).</span></span>|<span data-ttu-id="a67a5-129">**[復元されていないログがしきい値を超えた場合に警告する]**</span><span class="sxs-lookup"><span data-stu-id="a67a5-129">**Warn if the unrestored log exceeds the threshold**</span></span>|  
|<span data-ttu-id="a67a5-130">最も古い未送信のトランザクション</span><span class="sxs-lookup"><span data-stu-id="a67a5-130">Oldest unsent transaction</span></span>|<span data-ttu-id="a67a5-131">送信キュー内にトランザクションを累積できる時間 (分単位) を指定します。この時間を経過すると、プリンシパル サーバー インスタンスで警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-131">Specifies the number of minutes worth of transactions that can accumulate in the send queue before a warning is generated on the principal server instance.</span></span> <span data-ttu-id="a67a5-132">この警告は、時間の観点からデータ損失の可能性を測定するのに役立ち、特に、高パフォーマンス モードに関連しています。</span><span class="sxs-lookup"><span data-stu-id="a67a5-132">This warning helps measure the potential for data loss in terms of time and is especially relevant for high-performance mode.</span></span> <span data-ttu-id="a67a5-133">パートナーとの通信が切断されたためにミラーリングが一時停止または中断している場合は、高安全モードにも関係します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-133">However, the warning is also relevant for high-safety mode when mirroring is paused or suspended because the partners become disconnected.</span></span>|<span data-ttu-id="a67a5-134">**[最も古い未送信のトランザクションの経過期間がしきい値を超えた場合に警告する]**</span><span class="sxs-lookup"><span data-stu-id="a67a5-134">**Warn if the age of the oldest unsent transaction exceeds the threshold**</span></span>|  
|<span data-ttu-id="a67a5-135">ミラー コミットのオーバーヘッド</span><span class="sxs-lookup"><span data-stu-id="a67a5-135">Mirror commit overhead</span></span>|<span data-ttu-id="a67a5-136">許容可能な、トランザクションあたりの平均遅延時間 (ミリ秒単位) を指定します。この時間を経過すると、プリンシパル サーバーで警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-136">Specifies the number of milliseconds of average delay per transaction that are tolerated before a warning is generated on the principal server.</span></span> <span data-ttu-id="a67a5-137">この遅延時間は、ミラー サーバー インスタンスによってトランザクションのログ レコードが再実行キューに書き込まれるのをプリンシパル サーバー インスタンスが待機している間、発生したオーバーヘッドの量になります。</span><span class="sxs-lookup"><span data-stu-id="a67a5-137">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span> <span data-ttu-id="a67a5-138">この値は高安全モードにのみ関係します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-138">This value is relevant only in high-safety mode.</span></span>|<span data-ttu-id="a67a5-139">**[ミラー コミットのオーバーヘッドがしきい値を超えた場合に警告する]**</span><span class="sxs-lookup"><span data-stu-id="a67a5-139">**Warn if the mirror commit overhead exceeds the threshold**</span></span>|  
  
 <span data-ttu-id="a67a5-140">これらのパフォーマンス基準のいずれでも、システム管理者は、ミラー化されたデータベースでしきい値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-140">For any one of these performance metrics, a system administrator can specify a threshold on a mirrored database.</span></span> <span data-ttu-id="a67a5-141">詳細については、このトピックの「 [警告しきい値の設定と管理](#SetUpManageWarningThresholds)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a67a5-141">For more information, see [Setting Up and Managing Warning Thresholds](#SetUpManageWarningThresholds), later in this topic.</span></span>  
  
##  <a name="setting-up-and-managing-warning-thresholds"></a><a name="SetUpManageWarningThresholds"></a><span data-ttu-id="a67a5-142">警告しきい値の設定と管理</span><span class="sxs-lookup"><span data-stu-id="a67a5-142">Setting Up and Managing Warning Thresholds</span></span>  
 <span data-ttu-id="a67a5-143">システム管理者は、主要なミラーリング パフォーマンス基準に 1 つ以上の警告しきい値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-143">A system administrator can configure one or more warning thresholds for the key mirroring performance metrics.</span></span> <span data-ttu-id="a67a5-144">両方のパートナーの特定の警告に対してしきい値を設定し、データベースがフェールオーバーする場合に警告が保持されるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a67a5-144">We recommend setting a threshold for a given warning on both partners to make sure that the warning persists if the database fails over.</span></span> <span data-ttu-id="a67a5-145">各パートナーで適切なしきい値は、そのパートナーのシステムのパフォーマンス機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a67a5-145">The appropriate threshold on each partner depends on the performance capabilities of that partner's system.</span></span>  
  
 <span data-ttu-id="a67a5-146">警告しきい値は、次のいずれかを使用して設定および管理できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-146">Warning thresholds can be configured and managed by using either of the following:</span></span>  
  
-   <span data-ttu-id="a67a5-147">データベース ミラーリング モニター (Database Mirroring Monitor)</span><span class="sxs-lookup"><span data-stu-id="a67a5-147">Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="a67a5-148">データベース ミラーリング モニターでは、管理者は、 **[警告]** タブ ページをクリックして、プリンシパル サーバー インスタンスとミラー サーバー インスタンスの両方で選択したデータベースの警告の現在の構成を同時に確認できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-148">In Database Mirroring Monitor, the administrator can view the current configuration of warnings for a selected database at both the principal and mirror server instances at the same time by selecting the **Warnings** tabbed page.</span></span> <span data-ttu-id="a67a5-149">そのページから、 **[警告しきい値の設定]** ダイアログ ボックスを開き、1 つ以上の警告しきい値を有効にして設定できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-149">From there, the administrator can open the **Set Warning Thresholds** dialog box to enable and configure one or more warning thresholds.</span></span>  
  
     <span data-ttu-id="a67a5-150">データベース ミラーリング モニターのインターフェイスの概要については、「 [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a67a5-150">For an introduction to the Database Mirroring Monitor interface, see [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md).</span></span> <span data-ttu-id="a67a5-151">データベース ミラーリング モニターの起動方法については、「 [データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a67a5-151">For information about launching Database Mirroring Monitor, see [Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="a67a5-152">システム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a67a5-152">System stored procedures</span></span>  
  
     <span data-ttu-id="a67a5-153">次のシステム ストアド プロシージャを使用すると、管理者は、一度に 1 つのパートナーのミラー化されたデータベースで警告しきい値を設定および管理できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-153">The following set of system stored procedures enable an administrator to set up and manage warning thresholds on mirrored databases of one partner at a time.</span></span>  
  
    |<span data-ttu-id="a67a5-154">手順</span><span class="sxs-lookup"><span data-stu-id="a67a5-154">Procedure</span></span>|<span data-ttu-id="a67a5-155">説明</span><span class="sxs-lookup"><span data-stu-id="a67a5-155">Description</span></span>|  
    |---------------|-----------------|  
    |[<span data-ttu-id="a67a5-156">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-156">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql)|<span data-ttu-id="a67a5-157">指定したミラーリングのパフォーマンス基準に対する警告しきい値を追加または変更します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-157">Adds or changes warning threshold for a specified mirroring performance metric.</span></span>|  
    |[<span data-ttu-id="a67a5-158">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-158">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql)|<span data-ttu-id="a67a5-159">データベース ミラーリング監視の主要なパフォーマンス基準の 1 つまたはすべてについて、警告しきい値に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-159">Returns information about warning thresholds on one or all of several key database mirroring monitor performance metrics.</span></span>|  
    |[<span data-ttu-id="a67a5-160">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-160">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql)|<span data-ttu-id="a67a5-161">指定したパフォーマンス基準に対する警告を削除します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-161">Drops the warning for a specified performance metric.</span></span>|  
  
## <a name="performance-threshold-events-sent-to-the-windows-event-log"></a><span data-ttu-id="a67a5-162">Windows イベント ログに送信されるパフォーマンスしきい値イベント</span><span class="sxs-lookup"><span data-stu-id="a67a5-162">Performance-Threshold Events Sent to the Windows Event Log</span></span>  
 <span data-ttu-id="a67a5-163">パフォーマンス基準に警告しきい値を定義する場合、状態テーブルを更新すると、最新の値がそのしきい値に対して評価されます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-163">If warning thresholdis defined for a performance metric, when the status table is updated, the latest value is evaluated against the threshold.</span></span> <span data-ttu-id="a67a5-164">しきい値に達している場合は、更新手順**sp_dbmmonitorupdate**によって、メトリックに関する情報イベント (*パフォーマンスしきい値イベント*) が生成され、イベントが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows イベントログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-164">If the threshold has been reached, the update procedure, **sp_dbmmonitorupdate**, generates an informational event-a *performance-threshold event*- for the metric and writes the event to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows event log.</span></span> <span data-ttu-id="a67a5-165">次の表は、パフォーマンスしきい値イベントのイベント ID を示しています。</span><span class="sxs-lookup"><span data-stu-id="a67a5-165">The following table lists the event IDs of the performance-threshold events.</span></span>  
  
|<span data-ttu-id="a67a5-166">パフォーマンス基準</span><span class="sxs-lookup"><span data-stu-id="a67a5-166">Performance metric</span></span>|<span data-ttu-id="a67a5-167">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a67a5-167">Event ID</span></span>|  
|------------------------|--------------|  
|<span data-ttu-id="a67a5-168">未送信のログ</span><span class="sxs-lookup"><span data-stu-id="a67a5-168">Unsent log</span></span>|<span data-ttu-id="a67a5-169">32042</span><span class="sxs-lookup"><span data-stu-id="a67a5-169">32042</span></span>|  
|<span data-ttu-id="a67a5-170">未復元のログ</span><span class="sxs-lookup"><span data-stu-id="a67a5-170">Unrestored log</span></span>|<span data-ttu-id="a67a5-171">32043</span><span class="sxs-lookup"><span data-stu-id="a67a5-171">32043</span></span>|  
|<span data-ttu-id="a67a5-172">最も古い未送信のトランザクション</span><span class="sxs-lookup"><span data-stu-id="a67a5-172">Oldest unsent transaction</span></span>|<span data-ttu-id="a67a5-173">32040</span><span class="sxs-lookup"><span data-stu-id="a67a5-173">32040</span></span>|  
|<span data-ttu-id="a67a5-174">ミラー コミットのオーバーヘッド</span><span class="sxs-lookup"><span data-stu-id="a67a5-174">Mirror commit overhead</span></span>|<span data-ttu-id="a67a5-175">32044</span><span class="sxs-lookup"><span data-stu-id="a67a5-175">32044</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a67a5-176">管理者は、これらのイベントの 1 つ以上で警告を定義できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-176">An administrator can define alerts on any one or more of these events.</span></span> <span data-ttu-id="a67a5-177">詳細については、このトピックの「 [ミラー化されたデータベースに対する警告の使用](#UseAlerts)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a67a5-177">For more information, see [Using Alerts for a Mirrored Database](#UseAlerts), later in this</span></span>  
>   
>  <span data-ttu-id="a67a5-178">トピック</span><span class="sxs-lookup"><span data-stu-id="a67a5-178">topic.</span></span>  
  
##  <a name="using-alerts-for-a-mirrored-database"></a><a name="UseAlerts"></a><span data-ttu-id="a67a5-179">ミラー化されたデータベースに対する警告の使用</span><span class="sxs-lookup"><span data-stu-id="a67a5-179">Using Alerts for a Mirrored Database</span></span>  
 <span data-ttu-id="a67a5-180">ミラー化されたデータベースを監視する際に重要なのは、重大なデータベース ミラーリング イベントに対して警告を構成することです。</span><span class="sxs-lookup"><span data-stu-id="a67a5-180">An important part of monitoring a mirrored database is configuring alerts on significant database mirro events.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a67a5-181">では、次のようなデータベース ミラーリング イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-181">generates the following types of database mirroring events:</span></span>  
  
-   <span data-ttu-id="a67a5-182">パフォーマンスしきい値イベント</span><span class="sxs-lookup"><span data-stu-id="a67a5-182">Performance threshold events</span></span>  
  
     <span data-ttu-id="a67a5-183">詳細については、このトピックの「Windows イベント ログに送信されるパフォーマンスしきい値イベント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a67a5-183">For more information, see "Performance-Threshold Events Sent to the Windows Event Log" earlier in this topic.</span></span>  
  
-   <span data-ttu-id="a67a5-184">状態変更イベント</span><span class="sxs-lookup"><span data-stu-id="a67a5-184">State-change events</span></span>  
  
     <span data-ttu-id="a67a5-185">データベース ミラーリング セッションの内部状態に変更が生じたときに生成される Windows Management Instrumentation (WMI) イベントです。</span><span class="sxs-lookup"><span data-stu-id="a67a5-185">These are Windows Management Instrumentation (WMI) events that are generated when changes occur in the internal state of a database mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a67a5-186">詳細については、「 [WMI Provider for Server Events の概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a67a5-186">For more information, see [WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md).</span></span>  
  
 <span data-ttu-id="a67a5-187">システム管理者は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントまたは他のアプリケーション ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Operations Manager など) を使用して、これらのイベントに対して警告を構成できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-187">A system administrator can configure alerts on these by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent or other applications, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Operations Manager.</span></span>  
  
 <span data-ttu-id="a67a5-188">データベース ミラーリング イベントで警告を定義する場合は、両方のパートナー サーバー インスタンスで警告しきい値と警告を定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a67a5-188">When you define alerts on database mirroring events, we recommend that you define warning thresholds and alerts at both partner server instances.</span></span> <span data-ttu-id="a67a5-189">個々のイベントはプリンシパル サーバーまたはミラー サーバーのいずれかで生成されますが、各パートナーは常にどちらの役割も実行できます。</span><span class="sxs-lookup"><span data-stu-id="a67a5-189">Individual events are generated at either the principal server or the mirror server, but each partner can perform either role at any time.</span></span> <span data-ttu-id="a67a5-190">フェールオーバー後に警告が動作を続行するには、両方のパートナーで警告を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a67a5-190">To make sure that an alert continues to operate after a failover, the alert must be defined at both partners.</span></span>  
  
 <span data-ttu-id="a67a5-191">詳細については、 [SQL Server Web サイト](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)にあるデータベース ミラーリング イベントの警告に関するホワイト ペーパーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a67a5-191">For more information, see the white paper about alerting on database mirroring events at this [SQL Server Web site](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).</span></span> <span data-ttu-id="a67a5-192">このホワイト ペーパーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用した警告の構成方法、データベース ミラーリングの WMI イベント、およびサンプル スクリプトに関する情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="a67a5-192">This white paper contains information about how to configure alerts using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, the database mirroring WMI events, and sample scripts.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a67a5-193">すべてのミラーリング セッションでは、状態変更イベントに対する警告を送信するようにデータベースを構成することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a67a5-193">For all mirroring sessions, we strongly recommend that you configure the database to send an alert on any state-change events.</span></span> <span data-ttu-id="a67a5-194">状態変更は手動による構成の変更結果として予測される場合を除いて、データを損傷する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a67a5-194">Unless a state change is expected as the result of a manual configuration change, something has occurred that could compromise your data.</span></span> <span data-ttu-id="a67a5-195">データを保護するには、予測されていない状態変更の原因を特定して解決します。</span><span class="sxs-lookup"><span data-stu-id="a67a5-195">To help protect your data, identify and fix the cause of an unexpected state change.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a67a5-196">関連タスク</span><span class="sxs-lookup"><span data-stu-id="a67a5-196">Related Tasks</span></span>  
 <span data-ttu-id="a67a5-197">**SQL Server Management Studio を使用して警告を作成するには**</span><span class="sxs-lookup"><span data-stu-id="a67a5-197">**To create an alert using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="a67a5-198">エラー番号を使用して警告を作成する</span><span class="sxs-lookup"><span data-stu-id="a67a5-198">Create an Alert Using an Error Number</span></span>](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="a67a5-199">Create a WMI Event Alert</span><span class="sxs-lookup"><span data-stu-id="a67a5-199">Create a WMI Event Alert</span></span>](../../ssms/agent/create-a-wmi-event-alert.md)  
  
 <span data-ttu-id="a67a5-200">**データベース ミラーリングを監視するには**</span><span class="sxs-lookup"><span data-stu-id="a67a5-200">**To monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="a67a5-201">データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-201">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="a67a5-202">sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-202">sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql)  
  
-   [<span data-ttu-id="a67a5-203">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-203">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql)  
  
-   [<span data-ttu-id="a67a5-204">sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-204">sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql)  
  
-   [<span data-ttu-id="a67a5-205">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-205">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql)  
  
-   [<span data-ttu-id="a67a5-206">sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-206">sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql)  
  
-   [<span data-ttu-id="a67a5-207">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-207">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql)  
  
-   [<span data-ttu-id="a67a5-208">sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-208">sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql)  
  
-   [<span data-ttu-id="a67a5-209">sp_dbmmonitorresults &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-209">sp_dbmmonitorresults &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql)  
  
-   [<span data-ttu-id="a67a5-210">sp_dbmmonitorupdate &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-210">sp_dbmmonitorupdate &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="a67a5-211">参照</span><span class="sxs-lookup"><span data-stu-id="a67a5-211">See Also</span></span>  
 <span data-ttu-id="a67a5-212">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a67a5-212">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="a67a5-213">データベース ミラーリングの監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a67a5-213">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](monitoring-database-mirroring-sql-server.md)  
  
  