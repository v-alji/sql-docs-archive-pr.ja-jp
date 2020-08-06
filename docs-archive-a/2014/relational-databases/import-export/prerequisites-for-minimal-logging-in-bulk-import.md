---
title: 一括インポートで最小ログ記録を行うための前提条件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- minimal logging [SQL Server]
- logged bulk copy [SQL Server]
- logs [SQL Server], minimal logging
- minimally logged operations [SQL Server]
- bulk importing [SQL Server], minimal logging
ms.assetid: bd1dac6b-6ef8-4735-ad4e-67bb42dc4f66
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4711e25dcfcc99e14894e47166638673c61a6831
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741045"
---
# <a name="prerequisites-for-minimal-logging-in-bulk-import"></a><span data-ttu-id="0a301-102">一括インポートで最小ログ記録を行うための前提条件</span><span class="sxs-lookup"><span data-stu-id="0a301-102">Prerequisites for Minimal Logging in Bulk Import</span></span>
  <span data-ttu-id="0a301-103">完全復旧モデルのデータベースの場合、一括インポート中に実行されるすべての行挿入操作が、トランザクション ログに完全に記録されます。</span><span class="sxs-lookup"><span data-stu-id="0a301-103">For a database under the full recovery model, all row-insert operations that are performed by bulk import are fully logged in the transaction log.</span></span> <span data-ttu-id="0a301-104">完全復旧モデルを使用する場合、大きなデータをインポートするとトランザクション ログがすぐにいっぱいになってしまいます。</span><span class="sxs-lookup"><span data-stu-id="0a301-104">Large data imports can cause the transaction log to fill rapidly if the full recovery model is used.</span></span> <span data-ttu-id="0a301-105">これとは対照的に、単純復旧モデルまたは一括ログ復旧モデルでは、一括インポート操作の最小ログ記録を行うと、一括インポート操作によってログ領域がいっぱいになる可能性が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="0a301-105">In contrast, under the simple recovery model or bulk-logged recovery model, minimal logging of bulk-import operations reduces the possibility that a bulk-import operation will fill the log space.</span></span> <span data-ttu-id="0a301-106">最小ログ記録は完全ログ記録よりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="0a301-106">Minimal logging is also more efficient than full logging.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a301-107">一括ログ復旧モデルは、大量の一括操作中に完全復旧モデルの代わりとして一時的に使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="0a301-107">The bulk-logged recovery model is designed to temporarily replace the full recovery model during large bulk operations.</span></span>  
  
## <a name="table-requirements-for-minimally-logging-bulk-import-operations"></a><span data-ttu-id="0a301-108">一括インポート操作の最小ログ記録のためのテーブルの要件</span><span class="sxs-lookup"><span data-stu-id="0a301-108">Table Requirements for Minimally Logging Bulk-Import Operations</span></span>  
 <span data-ttu-id="0a301-109">最小ログ記録を行うテーブルは、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a301-109">Minimal logging requires that the target table meets the following conditions:</span></span>  
  
-   <span data-ttu-id="0a301-110">テーブルがレプリケート中でないこと。</span><span class="sxs-lookup"><span data-stu-id="0a301-110">The table is not being replicated.</span></span>  
  
-   <span data-ttu-id="0a301-111">(TABLOCK を使用して) テーブル ロックが指定されていること。</span><span class="sxs-lookup"><span data-stu-id="0a301-111">Table locking is specified (using TABLOCK).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a301-112">最小限のログ記録しか行われない一括インポート操作では、データを挿入してもトランザクション ログに記録されませんが、新しいエクステントがテーブルに割り当てられるたびに、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によりエクステントの割り当てがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="0a301-112">Although data insertions are not logged in the transaction log during a minimally logged bulk-import operation, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] still logs extent allocations each time a new extent is allocated to the table.</span></span>  
  
-   <span data-ttu-id="0a301-113">テーブルは、メモリ最適化テーブルではありません。</span><span class="sxs-lookup"><span data-stu-id="0a301-113">Table is not a memory-optimized table.</span></span>  
  
 <span data-ttu-id="0a301-114">あるテーブルの最小ログ記録を行うことができるかどうかは、そのテーブルにインデックスがあるかどうか、また、インデックスが存在する場合はテーブルが空かどうかによっても異なります。</span><span class="sxs-lookup"><span data-stu-id="0a301-114">Whether minimal logging can occur for a table also depends on whether the table is indexed and, if so, whether the table is empty:</span></span>  
  
-   <span data-ttu-id="0a301-115">テーブルにインデックスがない場合、データ ページの最小ログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="0a301-115">If the table has no indexes, data pages are minimally logged.</span></span>  
  
-   <span data-ttu-id="0a301-116">テーブルにクラスター化インデックスがなく、非クラスター化インデックスが 1 つ以上ある場合、データ ページは常に最小ログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="0a301-116">If the table has no clustered index but has one or more nonclustered indexes, data pages are always minimally logged.</span></span> <span data-ttu-id="0a301-117">インデックス ページのログがどのように記録されるかは、テーブルが空かどうかにより異なります。</span><span class="sxs-lookup"><span data-stu-id="0a301-117">How index pages are logged, however, depends on whether the table is empty:</span></span>  
  
    -   <span data-ttu-id="0a301-118">テーブルが空の場合、インデックス ページは最小ログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="0a301-118">If the table is empty, index pages are minimally logged.</span></span>  
  
    -   <span data-ttu-id="0a301-119">テーブルが空ではない場合、インデックス ページは完全ログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="0a301-119">If table is non-empty, index pages are fully logged.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0a301-120">空のテーブルに複数のバッチのデータを一括インポートする場合、最初のバッチについてはインデックス ページとデータ ページの最小ログ記録が行われますが、2 番目以降のバッチはデータ ページのみの最小ログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="0a301-120">If you start with an empty table and bulk import the data in multiple batches, both index and data pages are minimally logged for the first batch, but beginning with the second batch, only data pages are minimally logged.</span></span>  
  
-   <span data-ttu-id="0a301-121">テーブルが空で、クラスター化インデックスがある場合、データ ページとインデックス ページの最小ログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="0a301-121">If the table has a clustered index and is empty, both data and index pages are minimally logged.</span></span> <span data-ttu-id="0a301-122">これと対照的に、空ではないテーブルにクラスター化インデックスがある場合、いずれの復旧モデルであってもデータ ページとインデックス ページの完全ログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="0a301-122">In contrast, if a table has a clustered index and is non-empty, data pages and index pages are both fully logged regardless of the recovery model.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a301-123">空のテーブルにバッチのデータを一括インポートする場合、最初のバッチについてはインデックス ページとデータ ページの最小ログ記録が行われますが、2 番目以降のバッチはデータ ページのみ一括ログ記録が行われます。</span><span class="sxs-lookup"><span data-stu-id="0a301-123">If you start with an empty table and bulk import the data in batches, both index and data pages are minimally logged for the first batch, but from the second batch onwards, only data pages are bulk logged.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a301-124">トランザクション レプリケーションが有効な場合、BULK INSERT 操作は、一括ログ復旧モデルでも完全にログ記録されます。</span><span class="sxs-lookup"><span data-stu-id="0a301-124">When transactional replication is enabled, BULK INSERT operations are fully logged even under the Bulk Logged recovery model.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0a301-125">関連タスク</span><span class="sxs-lookup"><span data-stu-id="0a301-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="0a301-126">データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0a301-126">View or Change the Recovery Model of a Database &#40;SQL Server&#41;</span></span>](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="0a301-127">参照</span><span class="sxs-lookup"><span data-stu-id="0a301-127">See Also</span></span>  
 <span data-ttu-id="0a301-128">[復旧モデル &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0a301-128">[Recovery Models &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="0a301-129">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="0a301-129">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="0a301-130">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a301-130">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="0a301-131">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a301-131">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="0a301-132">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a301-132">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="0a301-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a301-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="0a301-134">[テーブル ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span><span class="sxs-lookup"><span data-stu-id="0a301-134">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span></span>  
 [<span data-ttu-id="0a301-135">INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0a301-135">INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/insert-transact-sql)  
  
  
