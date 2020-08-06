---
title: バックアップの圧縮 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], backup compression
- backup compression [SQL Server], about backup compression
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- backing up [SQL Server], backup compression
- backup compression [SQL Server]
ms.assetid: 05bc9c4f-3947-4dd4-b823-db77519bd4d2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3291a858d8ef037e7cca92eb2e6abb19aec4da8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632532"
---
# <a name="backup-compression-sql-server"></a><span data-ttu-id="482a0-102">バックアップの圧縮 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="482a0-102">Backup Compression (SQL Server)</span></span>
  <span data-ttu-id="482a0-103">このトピックでは、バックアップの圧縮の制限、パフォーマンス面のトレードオフ、バックアップの圧縮の構成、圧縮比率など、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップの圧縮について説明します。</span><span class="sxs-lookup"><span data-stu-id="482a0-103">This topic describes the compression of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups, including restrictions, performance trade-off of compressing backups, the configuration of backup compression, and the compression ratio.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="482a0-104">バックアップの圧縮をサポートするのエディションについ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="482a0-104">For information which editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support backup compression, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="482a0-105">圧縮されたバックアップは、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の各エディションで復元できます。</span><span class="sxs-lookup"><span data-stu-id="482a0-105">Every edition of [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later can restore a compressed backup.</span></span>  
  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="482a0-106">利点</span><span class="sxs-lookup"><span data-stu-id="482a0-106">Benefits</span></span>  
  
-   <span data-ttu-id="482a0-107">圧縮されたバックアップは、同じデータの圧縮されていないバックアップよりも小さいため、バックアップを圧縮すると一般には必要なデバイス I/O が少なくなり、通常はバックアップの速度が大きく短縮されます。</span><span class="sxs-lookup"><span data-stu-id="482a0-107">Because a compressed backup is smaller than an uncompressed backup of the same data, compressing a backup typically requires less device I/O and therefore usually increases backup speed significantly.</span></span>  
  
     <span data-ttu-id="482a0-108">詳細については、このトピックの「 [バックアップの圧縮がパフォーマンスに与える影響](#PerfImpact)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="482a0-108">For more information, see [Performance Impact of Compressing Backups](#PerfImpact), later in this topic.</span></span>  
  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="482a0-109">制限</span><span class="sxs-lookup"><span data-stu-id="482a0-109">Restrictions</span></span>  
 <span data-ttu-id="482a0-110">圧縮されたバックアップには次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="482a0-110">The following restrictions apply to compressed backups:</span></span>  
  
-   <span data-ttu-id="482a0-111">圧縮されたバックアップと圧縮されていないバックアップを 1 つのメディア セット内に共存させることはできません。</span><span class="sxs-lookup"><span data-stu-id="482a0-111">Compressed and uncompressed backups cannot co-exist in a media set.</span></span>  
  
-   <span data-ttu-id="482a0-112">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、圧縮されたバックアップを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="482a0-112">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot read compressed backups.</span></span>  
  
-   <span data-ttu-id="482a0-113">圧縮された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップのテープを複数の Ntbackup で共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="482a0-113">NTbackups cannot share a tape with compressed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span>  
  
  
##  <a name="performance-impact-of-compressing-backups"></a><a name="PerfImpact"></a> <span data-ttu-id="482a0-114">バックアップの圧縮がパフォーマンスに与える影響</span><span class="sxs-lookup"><span data-stu-id="482a0-114">Performance Impact of Compressing Backups</span></span>  
 <span data-ttu-id="482a0-115">既定の設定では、圧縮によって CPU 使用率が著しく増加し、圧縮処理によって CPU がさらに消費されるために、同時に実行される操作が悪影響を受ける場合があります。</span><span class="sxs-lookup"><span data-stu-id="482a0-115">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="482a0-116">このため、[リソース ガバナー](../resource-governor/resource-governor.md)によって CPU 使用率が制限されるセッションでは、優先度の低い圧縮バックアップを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="482a0-116">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by[Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="482a0-117">詳細については、「 [リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="482a0-117">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
 <span data-ttu-id="482a0-118">バックアップ I/O パフォーマンスの実態を把握するためには、次のようなパフォーマンス カウンターを評価することで、デバイスに対するバックアップ I/O を特定できます。</span><span class="sxs-lookup"><span data-stu-id="482a0-118">To obtain a good picture of your backup I/O performance, you can isolate the backup I/O to or from devices by evaluating the following sorts of performance counters:</span></span>  
  
-   <span data-ttu-id="482a0-119">物理ディスク カウンターなどの Windows I/O パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="482a0-119">Windows I/O performance counters, such as the physical-disk counters</span></span>  
  
-   <span data-ttu-id="482a0-120">**SQLServer:Backup Device** オブジェクトの [Device Throughput Bytes/sec](../performance-monitor/sql-server-backup-device-object.md) カウンター</span><span class="sxs-lookup"><span data-stu-id="482a0-120">The **Device Throughput Bytes/sec** counter of the [SQLServer:Backup Device](../performance-monitor/sql-server-backup-device-object.md) object</span></span>  
  
-   <span data-ttu-id="482a0-121">**SQLServer:Databases** オブジェクトの [Backup/Restore Throughput/sec](../performance-monitor/sql-server-databases-object.md) カウンター</span><span class="sxs-lookup"><span data-stu-id="482a0-121">The **Backup/Restore Throughput/sec** counter of the [SQLServer:Databases](../performance-monitor/sql-server-databases-object.md) object</span></span>  
  
 <span data-ttu-id="482a0-122">Windows カウンターの詳細については、Windows ヘルプを参照してください。</span><span class="sxs-lookup"><span data-stu-id="482a0-122">For information about Windows counters, see Windows help.</span></span> <span data-ttu-id="482a0-123">SQL Server カウンターの使用方法の詳細については、「 [SQL Server オブジェクトの使用](../performance-monitor/use-sql-server-objects.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="482a0-123">For information about how to work with SQL Server counters, see [Use SQL Server Objects](../performance-monitor/use-sql-server-objects.md).</span></span>  
  
  
##  <a name="calculate-the-compression-ratio-of-a-compressed-backup"></a><a name="CompressionRatio"></a> <span data-ttu-id="482a0-124">圧縮されたバックアップの圧縮比率の計算</span><span class="sxs-lookup"><span data-stu-id="482a0-124">Calculate the Compression Ratio of a Compressed Backup</span></span>  
 <span data-ttu-id="482a0-125">バックアップの圧縮比率を計算するには、 **backupset** 履歴テーブルの **backup_size** 列と [compressed_backup_size](/sql/relational-databases/system-tables/backupset-transact-sql) 列にある値を次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="482a0-125">To calculate the compression ratio of a backup, use the values for the backup in the **backup_size** and **compressed_backup_size** columns of the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) history table, as follows:</span></span>  
  
 <span data-ttu-id="482a0-126">**backup_size**:**compressed_backup_size**</span><span class="sxs-lookup"><span data-stu-id="482a0-126">**backup_size**:**compressed_backup_size**</span></span>  
  
 <span data-ttu-id="482a0-127">たとえば、圧縮比率が 3:1 の場合、ディスク領域を約 66% 節約できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="482a0-127">For example, a 3:1 compression ratio indicates that you are saving about 66% on disk space.</span></span> <span data-ttu-id="482a0-128">これらの列に対するクエリを実行するには、次の Transact-SQL ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="482a0-128">To query on these columns, you can use the following Transact-SQL statement:</span></span>  
  
```  
SELECT backup_size/compressed_backup_size FROM msdb..backupset;  
```  
  
 <span data-ttu-id="482a0-129">圧縮されたバックアップの圧縮比率は、圧縮対象のデータによって異なります。</span><span class="sxs-lookup"><span data-stu-id="482a0-129">The compression ratio of a compressed backup depends on the data that has been compressed.</span></span> <span data-ttu-id="482a0-130">実際の圧縮比率は、さまざまな要因の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="482a0-130">A variety of factors can impact the compression ratio obtained.</span></span> <span data-ttu-id="482a0-131">主な要因は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="482a0-131">Major factors include:</span></span>  
  
-   <span data-ttu-id="482a0-132">データの型</span><span class="sxs-lookup"><span data-stu-id="482a0-132">The type of data.</span></span>  
  
     <span data-ttu-id="482a0-133">文字データは、他のデータ型よりも圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="482a0-133">Character data compresses more than other types of data.</span></span>  
  
-   <span data-ttu-id="482a0-134">ページ上の各行のデータの一貫性</span><span class="sxs-lookup"><span data-stu-id="482a0-134">The consistency of the data among rows on a page.</span></span>  
  
     <span data-ttu-id="482a0-135">一般に、ページ内の複数の行でフィールドに同じ値が格納されている場合、その値が大幅に圧縮される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="482a0-135">Typically, if a page contains several rows in which a field contains the same value, significant compression might occur for that value.</span></span> <span data-ttu-id="482a0-136">これに対して、ランダムなデータが格納されたデータベースや、各ページにサイズの大きい行が 1 つだけ含まれているデータベースの場合、圧縮されたバックアップは、圧縮されていないバックアップとそれほど変わらないサイズになります。</span><span class="sxs-lookup"><span data-stu-id="482a0-136">In contrast, for a database that contains random data or that contains only one large row per page, a compressed backup would be almost as large as an uncompressed backup.</span></span>  
  
-   <span data-ttu-id="482a0-137">データが暗号化されているかどうか</span><span class="sxs-lookup"><span data-stu-id="482a0-137">Whether the data is encrypted.</span></span>  
  
     <span data-ttu-id="482a0-138">暗号化されたデータは、暗号化されていない同等のデータより、圧縮比率が大幅に下がります。</span><span class="sxs-lookup"><span data-stu-id="482a0-138">Encrypted data compresses significantly less than equivalent unencrypted data.</span></span> <span data-ttu-id="482a0-139">透過的なデータ暗号化を使用してデータベース全体を暗号化すると、バックアップを圧縮しても、サイズが大幅に減少することはありません。</span><span class="sxs-lookup"><span data-stu-id="482a0-139">If transparent data encryption is used to encrypt an entire database, compressing backups might not reduce their size by much, if at all.</span></span>  
  
-   <span data-ttu-id="482a0-140">データベースが圧縮されているかどうか</span><span class="sxs-lookup"><span data-stu-id="482a0-140">Whether the database is compressed.</span></span>  
  
     <span data-ttu-id="482a0-141">データベースが圧縮されている場合、バックアップを圧縮しても、サイズが大幅に減少することはありません。</span><span class="sxs-lookup"><span data-stu-id="482a0-141">If the database is compressed, compressing backups might not reduce their size by much, if at all.</span></span>  
  
  
##  <a name="allocation-of-space-for-the-backup-file"></a><a name="Allocation"></a> <span data-ttu-id="482a0-142">バックアップ ファイルの使用領域の割り当て</span><span class="sxs-lookup"><span data-stu-id="482a0-142">Allocation of Space for the Backup File</span></span>  
 <span data-ttu-id="482a0-143">圧縮されたバックアップの場合、最終的なバックアップ ファイルのサイズは、データをどれくらい圧縮できるかによりますが、それはバックアップ操作が終了するまで不明です。</span><span class="sxs-lookup"><span data-stu-id="482a0-143">For compressed backups, the size of the final backup file depends on how compressible the data is, and this is unknown before the backup operation finishes.</span></span>  <span data-ttu-id="482a0-144">そのため、既定では、圧縮を使用してデータベースをバックアップする場合、データベース エンジンはバックアップ ファイルのために事前割り当てアルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="482a0-144">Therefore, by default, when backing up a database using compression, the Database Engine uses a pre-allocation algorithm for the backup file.</span></span> <span data-ttu-id="482a0-145">このアルゴリズムでは、バックアップ ファイルに、データベースのサイズに対する定義済みの割合のサイズを事前に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="482a0-145">This algorithm pre-allocates a predefined percentage of the size of the database for the backup file.</span></span> <span data-ttu-id="482a0-146">バックアップ操作中に、より多くの領域が必要になった場合は、データベース エンジンによってファイルが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="482a0-146">If more space is needed during the backup operation, the Database Engine grows the file.</span></span> <span data-ttu-id="482a0-147">バックアップ操作の終了時の最終的なサイズが、割り当てられた領域のサイズを下回る場合は、データベース エンジンによってファイルがバックアップの実際の最終的なサイズに縮小されます。</span><span class="sxs-lookup"><span data-stu-id="482a0-147">If the final size is less than the allocated space, at the end of the backup operation, the Database Engine shrinks the file to the actual final size of the backup.</span></span>  
  
 <span data-ttu-id="482a0-148">バックアップ ファイルが、最終的なサイズに達するために必要な分だけを拡張できるようにするには、トレース フラグ 3042 を使用します。</span><span class="sxs-lookup"><span data-stu-id="482a0-148">To allow the backup file to grow only as needed to reach its final size, use trace flag 3042.</span></span> <span data-ttu-id="482a0-149">トレース フラグ 3042 は、バックアップ操作が既定のバックアップ圧縮の事前割り当てアルゴリズムを使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="482a0-149">Trace flag 3042 causes the backup operation to bypass the default backup compression pre-allocation algorithm.</span></span> <span data-ttu-id="482a0-150">このトレース フラグは、圧縮されたバックアップに実際に必要なサイズだけを割り当てることによって、容量を節約する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="482a0-150">This trace flag is useful if you need to save on space by allocating only the actual size required for the compressed backup.</span></span> <span data-ttu-id="482a0-151">ただし、このトレース フラグを使用すると、わずかなパフォーマンスの低下 (バックアップ操作の期間が長くなる可能性) が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="482a0-151">However, using this trace flag might cause a slight performance penalty (a possible increase in the duration of the backup operation).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="482a0-152">関連タスク</span><span class="sxs-lookup"><span data-stu-id="482a0-152">Related Tasks</span></span>  
  
-   [<span data-ttu-id="482a0-153">バックアップの圧縮の構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="482a0-153">Configure Backup Compression &#40;SQL Server&#41;</span></span>](backup-compression-sql-server.md)  
  
-   [<span data-ttu-id="482a0-154">backup compression default サーバー構成オプションの表示または構成</span><span class="sxs-lookup"><span data-stu-id="482a0-154">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
-   [<span data-ttu-id="482a0-155">リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="482a0-155">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="482a0-156">DBCC TRACEON &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="482a0-156">DBCC TRACEON &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)  
  
-   [<span data-ttu-id="482a0-157">DBCC TRACEOFF &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="482a0-157">DBCC TRACEOFF &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceoff-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="482a0-158">参照</span><span class="sxs-lookup"><span data-stu-id="482a0-158">See Also</span></span>  
 <span data-ttu-id="482a0-159">[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="482a0-159">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="482a0-160">トレース フラグ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="482a0-160">Trace Flags &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
