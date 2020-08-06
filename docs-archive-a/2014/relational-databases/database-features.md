---
title: データベース機能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 04518abb-8581-47c8-a601-ee9136c3c0eb
author: rothja
ms.author: jroth
ms.openlocfilehash: 56b9f9ba9cc6e11ea82b822ae10b31710c8617b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642124"
---
# <a name="database-features"></a><span data-ttu-id="82464-102">データベース機能</span><span class="sxs-lookup"><span data-stu-id="82464-102">Database Features</span></span>
  <span data-ttu-id="82464-103">このセクションでは、データベース、データベース オブジェクト、データ型、およびデータの操作や管理に使用されるメカニズムに関連する機能およびタスクついて説明します。</span><span class="sxs-lookup"><span data-stu-id="82464-103">This section contains the features and tasks associated with databases, database objects, data types, and the mechanisms used to work with or manage data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82464-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="82464-104">In This Section</span></span>  
  
|||
|--|--|
|[<span data-ttu-id="82464-105">データベース</span><span class="sxs-lookup"><span data-stu-id="82464-105">Databases</span></span>](databases/databases.md)|[<span data-ttu-id="82464-106">SQL Server データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="82464-106">Back Up and Restore of SQL Server Databases</span></span>](backup-restore/back-up-and-restore-of-sql-server-databases.md)|  
|[<span data-ttu-id="82464-107">テーブル</span><span class="sxs-lookup"><span data-stu-id="82464-107">Tables</span></span>](tables/tables.md)|[<span data-ttu-id="82464-108">シーケンス番号</span><span class="sxs-lookup"><span data-stu-id="82464-108">Sequence Numbers</span></span>](sequence-numbers/sequence-numbers.md)|[<span data-ttu-id="82464-109">データの一括インポートと一括エクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-109">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](import-export/bulk-import-and-export-of-data-sql-server.md)|  
|[<span data-ttu-id="82464-110">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-110">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp/in-memory-oltp-in-memory-optimization.md)|[<span data-ttu-id="82464-111">DDL トリガー</span><span class="sxs-lookup"><span data-stu-id="82464-111">DDL Triggers</span></span>](triggers/ddl-triggers.md)|[<span data-ttu-id="82464-112">データ圧縮</span><span class="sxs-lookup"><span data-stu-id="82464-112">Data Compression</span></span>](data-compression/data-compression.md)|  
|[<span data-ttu-id="82464-113">インデックス</span><span class="sxs-lookup"><span data-stu-id="82464-113">Indexes</span></span>](indexes/indexes.md)|[<span data-ttu-id="82464-114">DML トリガー</span><span class="sxs-lookup"><span data-stu-id="82464-114">DML Triggers</span></span>](triggers/dml-triggers.md)|[<span data-ttu-id="82464-115">Transact-SQL での OLE オートメーション オブジェクト</span><span class="sxs-lookup"><span data-stu-id="82464-115">OLE Automation Objects in Transact-SQL</span></span>](stored-procedures/ole-automation-objects-in-transact-sql.md)|  
|[<span data-ttu-id="82464-116">パーティション テーブルとパーティション インデックス</span><span class="sxs-lookup"><span data-stu-id="82464-116">Partitioned Tables and Indexes</span></span>](partitions/partitioned-tables-and-indexes.md)|[<span data-ttu-id="82464-117">シノニム &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-117">Synonyms &#40;Database Engine&#41;</span></span>](synonyms/synonyms-database-engine.md)|[<span data-ttu-id="82464-118">イベント通知</span><span class="sxs-lookup"><span data-stu-id="82464-118">Event Notifications</span></span>](service-broker/event-notifications.md)|  
|[<span data-ttu-id="82464-119">ビュー</span><span class="sxs-lookup"><span data-stu-id="82464-119">Views</span></span>](views/views.md)|[<span data-ttu-id="82464-120">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-120">XML Data &#40;SQL Server&#41;</span></span>](xml/xml-data-sql-server.md)|[<span data-ttu-id="82464-121">パフォーマンスの監視とチューニング</span><span class="sxs-lookup"><span data-stu-id="82464-121">Monitor and Tune for Performance</span></span>](performance/monitor-and-tune-for-performance.md)|  
|[<span data-ttu-id="82464-122">ストアド プロシージャ &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-122">Stored Procedures &#40;Database Engine&#41;</span></span>](stored-procedures/stored-procedures-database-engine.md)|[<span data-ttu-id="82464-123">空間データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-123">Spatial Data &#40;SQL Server&#41;</span></span>](spatial/spatial-data-sql-server.md)||  
|[<span data-ttu-id="82464-124">&#40;SQL Server の検索&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-124">Search &#40;SQL Server&#41;</span></span>](../database-engine/search-sql-server.md)|[<span data-ttu-id="82464-125">バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-125">Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;</span></span>](blob/binary-large-object-blob-data-sql-server.md)||  
|[<span data-ttu-id="82464-126">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="82464-126">User-Defined Functions</span></span>](user-defined-functions/user-defined-functions.md)|[<span data-ttu-id="82464-127">データ層アプリケーション</span><span class="sxs-lookup"><span data-stu-id="82464-127">Data-tier Applications</span></span>](data-tier-applications/data-tier-applications.md)||  
|[<span data-ttu-id="82464-128">統計</span><span class="sxs-lookup"><span data-stu-id="82464-128">Statistics</span></span>](statistics/statistics.md)|[<span data-ttu-id="82464-129">トランザクション ログ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-129">The Transaction Log &#40;SQL Server&#41;</span></span>](logs/the-transaction-log-sql-server.md)||  
|[<span data-ttu-id="82464-130">プラン ガイド</span><span class="sxs-lookup"><span data-stu-id="82464-130">Plan Guides</span></span>](performance/plan-guides.md)|[<span data-ttu-id="82464-131">データベース チェックポイント &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="82464-131">Database Checkpoints &#40;SQL Server&#41;</span></span>](logs/database-checkpoints-sql-server.md)||  
  
  
