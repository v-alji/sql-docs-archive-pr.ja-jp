---
title: メモリ最適化テーブルのストレージの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4e6e5f5a931669e2fc07cb957e60fd9c77b9b735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741009"
---
# <a name="configuring-storage-for-memory-optimized-tables"></a><span data-ttu-id="ac615-102">メモリ最適化テーブルのストレージの構成</span><span class="sxs-lookup"><span data-stu-id="ac615-102">Configuring Storage for Memory-Optimized Tables</span></span>
  <span data-ttu-id="ac615-103">記憶域の容量と 1 秒間の入出力操作 (IOPS) を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac615-103">You need to configure storage capacity and input/output operations per second (IOPS).</span></span>  
  
## <a name="storage-capacity"></a><span data-ttu-id="ac615-104">ストレージの容量</span><span class="sxs-lookup"><span data-stu-id="ac615-104">Storage Capacity</span></span>  
 <span data-ttu-id="ac615-105">[メモリ最適化テーブルのメモリ必要量の推定](memory-optimized-tables.md) の情報を使用して、データベースの持続性のあるメモリ最適化テーブルのメモリ内サイズを推定します。</span><span class="sxs-lookup"><span data-stu-id="ac615-105">Use the information in [Estimate Memory Requirements for Memory-Optimized Tables](memory-optimized-tables.md) to estimate the in-memory size of the database's durable memory-optimized tables.</span></span> <span data-ttu-id="ac615-106">インデックスはメモリ最適化テーブルに対して永続化されないため、インデックスのサイズは含めません。</span><span class="sxs-lookup"><span data-stu-id="ac615-106">Because indexes are not persisted for memory-optimized tables, do not include the size of indexes.</span></span> <span data-ttu-id="ac615-107">サイズを確認した後には、持続性のあるメモリ内テーブルのサイズの 4 倍のディスク領域を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac615-107">Once you determine the size, you need to provide disk space that is four times the size of durable, in-memory tables.</span></span>  
  
## <a name="storage-performance"></a><span data-ttu-id="ac615-108">記憶域のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="ac615-108">Storage Performance</span></span>  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] <span data-ttu-id="ac615-109">は、ワークロードのスループットを大幅に上げることができます。</span><span class="sxs-lookup"><span data-stu-id="ac615-109">can significantly increase your workload throughput.</span></span> <span data-ttu-id="ac615-110">したがって、IO がボトルネックになっていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ac615-110">Therefore, it is important to ensure that IO is not a bottleneck.</span></span>  
  
-   <span data-ttu-id="ac615-111">ディスク ベース テーブルをメモリ最適化テーブルに移行するときは、トランザクション ログ アクティビティの増加をサポートできる記憶メディアにトランザクション ログがあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ac615-111">When migrating disk-based tables to memory-optimized tables, make sure that the transaction log is on a storage media that can support increased transaction log activity.</span></span> <span data-ttu-id="ac615-112">たとえば、記憶メディアが 100 MB/秒のトランザクション ログの処理をサポートし、その結果としてメモリ最適化テーブルが 5 倍優れたパフォーマンスをもたらす場合、トランザクション ログ アクティビティがパフォーマンスのボトルネックになることを防ぐために、トランザクション ログの記憶メディアでも、5 倍のパフォーマンス向上をサポートできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac615-112">For example, if your storage media supports transaction log operations at 100 MB/sec, and memory-optimized tables result in five times greater performance, the transaction log's storage media must be able to also support five times performance improvement, to prevent the transaction log activity from becoming a performance bottleneck.</span></span>  
  
-   <span data-ttu-id="ac615-113">メモリ最適化テーブルは、1 つまたは複数のコンテナーに分散されたファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ac615-113">Memory-optimized tables are persisted in files distributed across one or more containers.</span></span> <span data-ttu-id="ac615-114">各コンテナーは、通常、独自のスピンドルにマップする必要があり、増加する記憶域容量とパフォーマンスの向上の両方のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac615-114">Each container should typically be mapped to its own spindle and is used both for increased storage capacity and improved performance.</span></span> <span data-ttu-id="ac615-115">ストレージメディアのシーケンシャル IOPS がトランザクションログのスループットの増加を3倍に対応できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac615-115">You need to ensure that sequential IOPS of the storage media can support a 3 times increase in transaction log throughput.</span></span>  
  
     <span data-ttu-id="ac615-116">たとえば、メモリ最適化テーブルがトランザクションログで 500 MB/sec アクティビティを生成する場合、メモリ最適化テーブルのストレージは 1.5 GB/秒をサポートする必要があります。トランザクションログのスループットの増加を3倍にする必要があることは、データファイルとデルタファイルのペアが最初のデータと共に書き込まれ、その後、マージ操作の一部として読み取り/再書き込みされる必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="ac615-116">For example, if memory-optimized tables generate 500MB/sec of activity in the transaction log, the storage for memory-optimized tables must support 1.5GB/sec. The need to support a 3 times increase in transaction log throughput comes from the observation that the data and delta file pairs are first written with the initial data and then need to be read/re-written as part of a merge operation.</span></span>  
  
     <span data-ttu-id="ac615-117">記憶域のスループットを見積もる際のもう 1 つの要因は、メモリ最適化テーブルの復旧時間です。</span><span class="sxs-lookup"><span data-stu-id="ac615-117">Another factor in estimating throughput for storage is the recovery time for memory-optimized tables.</span></span> <span data-ttu-id="ac615-118">持続性のあるテーブルからのデータは、データベースがアプリケーションで使用される前にメモリに読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac615-118">Data from durable tables must be read into memory before a database is made available to applications.</span></span> <span data-ttu-id="ac615-119">一般的に、メモリ最適化テーブルへのデータの読み込みは IOPS の速度で実行できます。</span><span class="sxs-lookup"><span data-stu-id="ac615-119">Commonly, loading data into memory-optimized tables can be done at the speed of IOPS.</span></span> <span data-ttu-id="ac615-120">それで、持続性のあるメモリ最適化テーブルの合計の記憶域が 60 GB で、1 分でこのデータを読み込めるようにする場合は、記憶域の IOPS を 1 GB/秒に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac615-120">So if the total storage for durable, memory-optimized tables is 60 GB and you want to be able to load this data in 1 minute, the IOPS for the storage must be set at 1 GB/sec.</span></span>  
  
-   <span data-ttu-id="ac615-121">偶数個のスピンドルを使用している場合、コンテナー数の 2 倍を作成し、各ペアを同じスピンドルにマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac615-121">If you have even number of spindles, you should create two times the number of containers, each pair mapped to the same spindle.</span></span> <span data-ttu-id="ac615-122">これは、IOPS および記憶域を分散するために必要です。</span><span class="sxs-lookup"><span data-stu-id="ac615-122">This is needed to spread the IOPS and the storage.</span></span> <span data-ttu-id="ac615-123">詳細については、「[メモリ最適化ファイルグループ](the-memory-optimized-filegroup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac615-123">For more information, see [The Memory Optimized Filegroup](the-memory-optimized-filegroup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac615-124">参照</span><span class="sxs-lookup"><span data-stu-id="ac615-124">See Also</span></span>  
 [<span data-ttu-id="ac615-125">メモリ最適化オブジェクト用ストレージの作成と管理</span><span class="sxs-lookup"><span data-stu-id="ac615-125">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
