---
title: メモリ最適化オブジェクトの持続性の定義 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0fe85fbf-8e8d-4983-96fd-d04b3c7d6d65
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 325f50a74ea75270dd62fc3564200c59255dc6cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633835"
---
# <a name="defining-durability-for-memory-optimized-objects"></a><span data-ttu-id="ba23c-102">メモリ最適化オブジェクトの持続性の定義</span><span class="sxs-lookup"><span data-stu-id="ba23c-102">Defining Durability for Memory-Optimized Objects</span></span>
  <span data-ttu-id="ba23c-103">インメモリ OLTP では、完全な原子性、一貫性、分離性、および完全な持続性 (ACID) の各プロパティが保証されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-103">In-Memory OLTP guarantees full atomicity, consistency, isolation, and full durability (ACID) properties.</span></span> <span data-ttu-id="ba23c-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] およびメモリ最適化テーブルのコンテキストにおける持続性では、次の事項が保証されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-104">Durability in the context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and memory-optimized tables provides following guarantees:</span></span>  
  
 <span data-ttu-id="ba23c-105">トランザクションの持続性</span><span class="sxs-lookup"><span data-stu-id="ba23c-105">Transactional Durability</span></span>  
 <span data-ttu-id="ba23c-106">メモリ最適化テーブルに対して (DDL または DML の) 変更を行った完全に持続性があるトランザクションをコミットする場合、持続性のあるメモリ最適化テーブルに対して行った変更は永久保存されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-106">When you commit a fully durable transaction that made (DDL or DML) changes to a memory-optimized table, the changes made to a durable memory-optimized table are permanent.</span></span>  
  
 <span data-ttu-id="ba23c-107">メモリ最適化テーブルに対して遅延した持続性トランザクションをコミットする場合、トランザクションは、インメモリ トランザクション ログがディスクに保存された後にのみ持続可能になります。</span><span class="sxs-lookup"><span data-stu-id="ba23c-107">When you commit a delayed durable transaction to a memory-optimized table, the transaction becomes durable only after the in-memory transaction log is saved to disk.</span></span>  
  
 <span data-ttu-id="ba23c-108">再起動の持続性</span><span class="sxs-lookup"><span data-stu-id="ba23c-108">Restart Durability</span></span>  
 <span data-ttu-id="ba23c-109">クラッシュまたは計画シャットダウンの後で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再起動する場合、持続性のあるメモリ最適化テーブルは再インスタンス化されて、シャットダウンやクラッシュの前の状態に復元されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-109">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restarts after a crash or planned shutdown, the memory-optimized durable tables are reinstantiated to restore them to the state before the shutdown or crash.</span></span>  
  
 <span data-ttu-id="ba23c-110">メディア障害の持続性</span><span class="sxs-lookup"><span data-stu-id="ba23c-110">Media Failure Durability</span></span>  
 <span data-ttu-id="ba23c-111">失敗または破損したディスクに、持続性のあるメモリ最適化オブジェクトの保存されたコピーが 1 つ以上保持されている場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップおよび復元機能により、新しいメディアのメモリ最適化テーブルが復元されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-111">If a failed or corrupt disk contains one or more persisted copies of durable memory-optimized objects, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore feature restores memory-optimized tables on the new media.</span></span>  
  
 <span data-ttu-id="ba23c-112">メモリ最適化テーブルには持続性のオプションが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="ba23c-112">There are two durability options for memory-optimized tables:</span></span>  
  
 <span data-ttu-id="ba23c-113">SCHEMA_ONLY (持続性のないテーブル)</span><span class="sxs-lookup"><span data-stu-id="ba23c-113">SCHEMA_ONLY (non-durable table)</span></span>  
 <span data-ttu-id="ba23c-114">このオプションは、インデックスを含むテーブル スキーマの持続性を確認します。</span><span class="sxs-lookup"><span data-stu-id="ba23c-114">This option ensures durability of the table schema, including indexes.</span></span> <span data-ttu-id="ba23c-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動すると、持続性のないテーブルが再作成されますが、最初はデータがありません </span><span class="sxs-lookup"><span data-stu-id="ba23c-115">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted, the non-durable table is recreated, but starts with no data.</span></span> <span data-ttu-id="ba23c-116">(これは tempdb のテーブルとは異なり、テーブルとテーブルのデータはどちらも再起動時に失われます)。持続性のないテーブルを作成するための一般的なシナリオは、ETL プロセスのステージング テーブルなどの一時的なデータを格納することです。</span><span class="sxs-lookup"><span data-stu-id="ba23c-116">(This is unlike a table in tempdb, where both the table and its data are lost upon restart.) A typical scenario for creating a non-durable table is to store transient data, such as a staging table for an ETL process.</span></span> <span data-ttu-id="ba23c-117">SCHEMA_ONLY の持続性により、トランザクションのログ記録とチェックポイントの両方が回避されるため、I/O 操作が大幅に減少します。</span><span class="sxs-lookup"><span data-stu-id="ba23c-117">A SCHEMA_ONLY durability avoids both transaction logging and checkpoint, which can significantly reduce I/O operations.</span></span>  
  
 <span data-ttu-id="ba23c-118">SCHEMA_AND_DATA (持続性のあるテーブル)</span><span class="sxs-lookup"><span data-stu-id="ba23c-118">SCHEMA_AND_DATA (durable table)</span></span>  
 <span data-ttu-id="ba23c-119">このオプションは、スキーマとデータの両方の持続性を提供します。</span><span class="sxs-lookup"><span data-stu-id="ba23c-119">This option provides durability of both schema and data.</span></span> <span data-ttu-id="ba23c-120">データ持続性のレベルは、完全に持続性があるトランザクションと持続性に遅延が生じているトランザクションのどちらとしてコミットするかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ba23c-120">The level of data durability depends on whether you commit a transaction as fully durable or with delayed durability.</span></span> <span data-ttu-id="ba23c-121">完全に持続性があるトランザクションでは、ディスク ベース テーブルの場合と同様に、データとスキーマに対して同じ持続性が保証されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-121">Fully durable transactions provide the same durability guarantee for data and schema, similar to a disk-based table.</span></span> <span data-ttu-id="ba23c-122">遅延した持続性ではパフォーマンスが向上しますが、サーバー クラッシュまたはフェールオーバー時にデータが失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba23c-122">Delayed durability will improve performance but can potentially result in data loss in case of a server crash or fail over.</span></span> <span data-ttu-id="ba23c-123">(遅延持続性の詳細については、「 [コントロールのトランザクションの持続性](../logs/control-transaction-durability.md)」を参照してください。)</span><span class="sxs-lookup"><span data-stu-id="ba23c-123">(For more information about delayed durability, see [Control Transaction Durability](../logs/control-transaction-durability.md).)</span></span>  
  
 <span data-ttu-id="ba23c-124">メモリ最適化テーブルのスキーマは、ディスク ベース テーブルの場合と同様に、データベースのプライマリ ファイル グループに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-124">The schema of the memory-optimized table is persisted, similar to disk-based tables, in the primary file group of a database.</span></span>  
  
 <span data-ttu-id="ba23c-125">持続性のあるメモリ最適化テーブル内のデータは、データ ファイルとデルタ ファイルのペアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-125">Data in durable memory-optimized tables is saved in data and delta file pairs.</span></span>  
  
 <span data-ttu-id="ba23c-126">メモリ最適化テーブルで定義されたインデックスは、ストレージではなくメタデータにのみ保持されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-126">The indexes defined in memory-optimized tables persist only in metadata, not in storage.</span></span> <span data-ttu-id="ba23c-127">インデックス構造は、メモリ最適化テーブル読み込みの一部として生成されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-127">Index structures are generated as part of loading memory-optimized tables.</span></span>  
  
 <span data-ttu-id="ba23c-128">行は、DELETE ステートメントによって明示的に、または UPDATE ステートメントによって間接的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-128">Rows are deleted either explicitly by a DELETE statement or indirectly by an UPDATE statement.</span></span> <span data-ttu-id="ba23c-129">UPDATE 操作は削除として実行され、その後に挿入が続きます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-129">An UPDATE operation is executed as a delete followed by an insert.</span></span> <span data-ttu-id="ba23c-130">行を削除しても、データ ファイルに対して変更は行われませんが、削除された行を識別する新しい行が対応するデルタ ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ba23c-130">When a row is deleted, no change is made to a data file but a new row, identifying the deleted row, is appended to the corresponding delta file.</span></span>  
  
 <span data-ttu-id="ba23c-131">復旧操作または復元操作中に、インメモリ OLTP エンジンは物理メモリに読み込むためにデータ ファイルとデルタ ファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="ba23c-131">During recovery or restore operations, the In-Memory OLTP engine reads data and delta files for loading into physical memory.</span></span> <span data-ttu-id="ba23c-132">読み込み時間は次の事項によって決まります。</span><span class="sxs-lookup"><span data-stu-id="ba23c-132">The load time is determined by:</span></span>  
  
-   <span data-ttu-id="ba23c-133">読み込むデータの量。</span><span class="sxs-lookup"><span data-stu-id="ba23c-133">The amount of data to load.</span></span>  
  
-   <span data-ttu-id="ba23c-134">シーケンシャル I/O 帯域幅。</span><span class="sxs-lookup"><span data-stu-id="ba23c-134">Sequential I/O bandwidth.</span></span>  
  
-   <span data-ttu-id="ba23c-135">ファイル コンテナーの数およびプロセッサ コアの数によって決まる、並列処理の次数。</span><span class="sxs-lookup"><span data-stu-id="ba23c-135">Degree of parallelism, determined by number of file containers and processor cores.</span></span>  
  
-   <span data-ttu-id="ba23c-136">再実行される必要があるログのアクティブな部分のログ レコードの量。</span><span class="sxs-lookup"><span data-stu-id="ba23c-136">The amount of log records in the active portion of the log that need to be redone.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba23c-137">参照</span><span class="sxs-lookup"><span data-stu-id="ba23c-137">See Also</span></span>  
 [<span data-ttu-id="ba23c-138">メモリ最適化オブジェクト用ストレージの作成と管理</span><span class="sxs-lookup"><span data-stu-id="ba23c-138">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
