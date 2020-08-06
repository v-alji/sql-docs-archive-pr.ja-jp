---
title: 変更の追跡の有効化と無効化 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], disabling
- data changes [SQL Server]
- change tracking [SQL Server], enabling
- tracking data changes [SQL Server]
- change tracking [SQL Server], configuring
- data [SQL Server], changing
ms.assetid: 1c92ec7e-ae53-4498-8bfd-c66a42a24d54
author: rothja
ms.author: jroth
ms.openlocfilehash: 402c63ae03df14e3a725fbc440575f5233d502f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639916"
---
# <a name="enable-and-disable-change-tracking-sql-server"></a><span data-ttu-id="56b4b-102">変更の追跡の有効化と無効化 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="56b4b-102">Enable and Disable Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="56b4b-103">このトピックでは、データベースとテーブルに対する変更の追跡を有効または無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="56b4b-103">This topic describes how to enable and disable change tracking for a database and a table.</span></span>  
  
## <a name="enable-change-tracking-for-a-database"></a><span data-ttu-id="56b4b-104">データベースの変更の追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="56b4b-104">Enable Change Tracking for a Database</span></span>  
 <span data-ttu-id="56b4b-105">変更の追跡を使用するには、あらかじめデータベース レベルで変更の追跡を有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="56b4b-105">Before you can use change tracking, you must enable change tracking at the database level.</span></span> <span data-ttu-id="56b4b-106">次の例では、 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)を使用して変更の追跡を有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="56b4b-106">The following example shows how to enable change tracking by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(CHANGE_RETENTION = 2 DAYS, AUTO_CLEANUP = ON)  
```  
  
 <span data-ttu-id="56b4b-107">変更の追跡は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [[データベースのプロパティ] &#40;[変更の追跡] ページ&#41;](../databases/database-properties-changetracking-page.md) ダイアログ ボックスを使用して有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-107">You can also enable change tracking in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="56b4b-108">変更の追跡を有効にするときに、CHANGE_RETENTION および AUTO_CLEANUP オプションを指定できます。これらの値は、変更の追跡を有効にした後いつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-108">You can specify the CHANGE_RETENTION and AUTO_CLEANUP options when you enable change tracking, and you can change the values at any time after change tracking is enabled.</span></span>  
  
 <span data-ttu-id="56b4b-109">change retention 値は、変更追跡情報を保持する期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="56b4b-109">The change retention value specifies the time period for which change tracking information is kept.</span></span> <span data-ttu-id="56b4b-110">この期間を過ぎると、変更追跡情報は定期的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-110">Change tracking information that is older than this time period is removed periodically.</span></span> <span data-ttu-id="56b4b-111">この値を設定する場合は、アプリケーションとデータベース内のテーブルを同期する間隔を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56b4b-111">When you are setting this value, you should consider how often applications will synchronize with the tables in the database.</span></span> <span data-ttu-id="56b4b-112">保有期間は、同期間隔と同じかそれ以上の長さに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56b4b-112">The specified retention period must be at least as long as the maximum time period between synchronizations.</span></span> <span data-ttu-id="56b4b-113">アプリケーションが変更を取得する間隔の方が長い場合、変更情報の一部が削除済みである可能性があるので、正しくない結果が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="56b4b-113">If an application obtains changes at longer intervals, the results that are returned might be incorrect because some of the change information has probably been removed.</span></span> <span data-ttu-id="56b4b-114">正しくない結果を取得しないようにするために、アプリケーションでは、CHANGE_TRACKING_MIN_VALID_VERSION システム関数を使用して、同期間隔が長すぎないかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-114">To avoid obtaining incorrect results, an application can use the CHANGE_TRACKING_MIN_VALID_VERSION system function to determine whether the interval between synchronizations has been too long.</span></span>  
  
 <span data-ttu-id="56b4b-115">AUTO_CLEANUP オプションは、古い変更追跡情報を削除するクリーンアップ タスクを有効または無効にするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-115">You can use the AUTO_CLEANUP option to enable or disable the cleanup task that removes old change tracking information.</span></span> <span data-ttu-id="56b4b-116">これは、アプリケーションを同期できない一時的な問題が発生しており、保有期間を過ぎた変更追跡情報を削除するプロセスを問題が解決されるまで一時停止する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-116">This can be useful when there is a temporary problem that prevents applications from synchronizing and the process for removing change tracking information older than the retention period must be paused until the problem is resolved.</span></span>  
  
 <span data-ttu-id="56b4b-117">変更の追跡を使用するデータベースについて、以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="56b4b-117">For any database that uses change tracking, be aware of the following:</span></span>  
  
-   <span data-ttu-id="56b4b-118">変更の追跡を使用するには、データベースの互換性レベルを 90 以上に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56b4b-118">To use change tracking, the database compatibility level must be set to 90 or greater.</span></span> <span data-ttu-id="56b4b-119">データベースの互換性レベルが 90 未満の場合でも、変更の追跡は構成できます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-119">If a database has a compatibility level of less than 90, you can configure change tracking.</span></span> <span data-ttu-id="56b4b-120">ただし、変更追跡情報の取得に使用される CHANGETABLE 関数からエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-120">However, the CHANGETABLE function, which is used to obtain change tracking information, will return an error.</span></span>  
  
-   <span data-ttu-id="56b4b-121">スナップショット分離を使用すると、すべての変更追跡情報の一貫性を最も簡単に確保できます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-121">Using snapshot isolation is the easiest way for you to help ensure that all change tracking information is consistent.</span></span> <span data-ttu-id="56b4b-122">このため、データベースのスナップショット分離を ON に設定することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="56b4b-122">For this reason, we strongly recommend that snapshot isolation be set to ON for the database.</span></span> <span data-ttu-id="56b4b-123">詳細については、「[変更の追跡のしくみ &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56b4b-123">For more information, see [Work with Change Tracking &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md).</span></span>  
  
## <a name="enable-change-tracking-for-a-table"></a><span data-ttu-id="56b4b-124">テーブルの変更の追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="56b4b-124">Enable Change Tracking for a Table</span></span>  
 <span data-ttu-id="56b4b-125">変更の追跡は、追跡するテーブルごとに有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="56b4b-125">Change tracking must be enabled for each table that you want tracked.</span></span> <span data-ttu-id="56b4b-126">変更の追跡を有効にすると、DML 操作の影響を受けるテーブル内のすべての行に関する変更追跡情報が保持されます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-126">When change tracking is enabled, change tracking information is maintained for all rows in the table that are affected by a DML operation.</span></span>  
  
 <span data-ttu-id="56b4b-127">次の例では、 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)を使用してテーブルの変更の追跡を有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="56b4b-127">The following example shows how to enable change tracking for a table by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
```sql  
ALTER TABLE Person.Contact  
ENABLE CHANGE_TRACKING  
WITH (TRACK_COLUMNS_UPDATED = ON)  
```  
  
 <span data-ttu-id="56b4b-128">テーブルの変更の追跡は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [[データベースのプロパティ] &#40;[変更の追跡] ページ&#41;](../databases/database-properties-changetracking-page.md) ダイアログ ボックスを使用して有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-128">You can also enable change tracking for a table in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="56b4b-129">TRACK_COLUMNS_UPDATED オプションが ON に設定されている場合、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] によって、どの列が更新されたかという追加情報が内部変更追跡テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-129">When the TRACK_COLUMNS_UPDATED option is set to ON, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] stores extra information about which columns were updated to the internal change tracking table.</span></span> <span data-ttu-id="56b4b-130">列追跡を行うと、アプリケーションは更新された列のみを同期できます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-130">Column tracking can enable an application to synchronize only those columns that were updated.</span></span> <span data-ttu-id="56b4b-131">これにより、効率とパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="56b4b-131">This can improve efficiency and performance.</span></span> <span data-ttu-id="56b4b-132">ただし、列追跡情報を保持すると追加のストレージ オーバーヘッドがかかるので、このオプションは既定では OFF に設定されています。</span><span class="sxs-lookup"><span data-stu-id="56b4b-132">However, because maintaining column tracking information adds some extra storage overhead, this option is set to OFF by default.</span></span>  
  
## <a name="disable-change-tracking-for-a-database-or-table"></a><span data-ttu-id="56b4b-133">データベースまたはテーブルに対する変更の追跡を無効にする</span><span class="sxs-lookup"><span data-stu-id="56b4b-133">Disable Change Tracking for a Database or Table</span></span>  
 <span data-ttu-id="56b4b-134">まず変更の追跡の対象になっているすべてのテーブルの変更の追跡を無効にして、次にデータベースの変更の追跡を OFF に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56b4b-134">Change tracking must first be disabled for all change-tracked tables before change tracking can be set to OFF for the database.</span></span> <span data-ttu-id="56b4b-135">データベース内で変更の追跡が有効になっているテーブルを確認するには、 [sys.change_tracking_tables](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) カタログ ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="56b4b-135">To determine the tables that have change tracking enabled for a database, use the [sys.change_tracking_tables](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) catalog view.</span></span>  
  
 <span data-ttu-id="56b4b-136">データベース内のテーブルで変更が追跡されていなければ、データベースの変更の追跡を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="56b4b-136">When no tables in a database track changes, you can disable change tracking for the database.</span></span> <span data-ttu-id="56b4b-137">次の例では、 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)を使用してデータベースの変更の追跡を無効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="56b4b-137">The following example shows how to disable change tracking for a database by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF  
```  
  
 <span data-ttu-id="56b4b-138">次の例では、 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)を使用してテーブルの変更の追跡を無効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="56b4b-138">The following example shows how to disable change tracking for a table by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
```sql  
ALTER TABLE Person.Contact  
DISABLE CHANGE_TRACKING;  
```  
  
## <a name="see-also"></a><span data-ttu-id="56b4b-139">参照</span><span class="sxs-lookup"><span data-stu-id="56b4b-139">See Also</span></span>  
 <span data-ttu-id="56b4b-140">[[データベースのプロパティ] &#40;[変更の追跡] ページ&#41;](../databases/database-properties-changetracking-page.md) </span><span class="sxs-lookup"><span data-stu-id="56b4b-140">[Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) </span></span>  
 <span data-ttu-id="56b4b-141">[ALTER DATABASE SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="56b4b-141">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="56b4b-142">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span><span class="sxs-lookup"><span data-stu-id="56b4b-142">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span></span>  
 <span data-ttu-id="56b4b-143">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span><span class="sxs-lookup"><span data-stu-id="56b4b-143">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span></span>  
 <span data-ttu-id="56b4b-144">[データ変更の追跡 &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56b4b-144">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="56b4b-145">[変更の追跡について &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56b4b-145">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="56b4b-146">[変更データの処理 &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56b4b-146">[Work with Change Data &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span></span>  
 [<span data-ttu-id="56b4b-147">変更の追跡の管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="56b4b-147">Manage Change Tracking &#40;SQL Server&#41;</span></span>](manage-change-tracking-sql-server.md)  
  
  
