---
title: メモリ最適化ファイルグループ | Microsoft Docs
ms.custom: ''
ms.date: 11/19/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a4ab6423159d0ba5a27af152cc5578905f57eec6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645069"
---
# <a name="the-memory-optimized-filegroup"></a><span data-ttu-id="47a3e-102">メモリ最適化ファイルグループ</span><span class="sxs-lookup"><span data-stu-id="47a3e-102">The Memory Optimized Filegroup</span></span>
  <span data-ttu-id="47a3e-103">メモリ最適化テーブルを作成するには、まずメモリ最適化ファイルグループを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-103">To create memory-optimized tables, you must first create a memory-optimized filegroup.</span></span> <span data-ttu-id="47a3e-104">メモリ最適化ファイル グループには 1 つ以上のコンテナーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="47a3e-104">The memory-optimized filegroup holds one or more containers.</span></span> <span data-ttu-id="47a3e-105">各コンテナーには、データ ファイルかデルタ ファイル、あるいはその両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="47a3e-105">Each container contains data files or delta files or both.</span></span>  
  
 <span data-ttu-id="47a3e-106">`SCHEMA_ONLY` テーブルからのデータ行は持続的ではなく、メモリ最適化テーブルに対応するメタデータおよびネイティブ コンパイル ストアド プロシージャは従来型のカタログに格納されますが、メモリ最適化テーブルを含むデータベースを一貫した環境で提供できるように、[!INCLUDE[hek_2](../../includes/hek-2-md.md)] エンジンでは引き続き、`SCHEMA_ONLY` メモリ最適化テーブルに対応するメモリ最適化ファイルグループが必要です。</span><span class="sxs-lookup"><span data-stu-id="47a3e-106">Even though data rows from `SCHEMA_ONLY` tables are not persisted and the metadata for memory-optimized tables and natively compiled stored procedures is stored in the traditional catalogs, the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine still requires a memory-optimized filegroup for `SCHEMA_ONLY` memory-optimized tables to provide a uniform experience for databases with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="47a3e-107">メモリ最適化ファイルグループは FILESTREAM ファイルグループをベースとしていますが、次の違いがあります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-107">The memory-optimized filegroup is based on filestream filegroup, with the following differences:</span></span>  
  
-   <span data-ttu-id="47a3e-108">メモリ最適化ファイルグループは、データベースごとに 1 つだけ作成できます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-108">You can only create one memory-optimized filegroup per database.</span></span> <span data-ttu-id="47a3e-109">memory_optimized_data を含めることにより、このファイルグループに明示的にマークを付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-109">You need to explicitly mark the filegroup as containing memory_optimized_data.</span></span> <span data-ttu-id="47a3e-110">データベースを作成するときにファイルグループを作成することも、後でファイルグループを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-110">You can create the filegroup when you create the database or you can add it later:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   <span data-ttu-id="47a3e-111">MEMORY_OPTIMIZED_DATA ファイルグループに対して、1 つ以上のコンテナーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-111">You need to add one or more containers to the MEMORY_OPTIMIZED_DATA filegroup.</span></span> <span data-ttu-id="47a3e-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="47a3e-112">For example:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   <span data-ttu-id="47a3e-113">メモリ最適化ファイルグループを作成するために、ファイルストリームを有効にする必要はありません ([FILESTREAM の有効化と構成](../blob/enable-and-configure-filestream.md))。</span><span class="sxs-lookup"><span data-stu-id="47a3e-113">You do not need to enable filestream ([Enable and Configure FILESTREAM](../blob/enable-and-configure-filestream.md)) to create a memory-optimized filegroup.</span></span> <span data-ttu-id="47a3e-114">ファイルストリームへのマッピングは、 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] エンジンによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-114">The mapping to filestream is done by the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine.</span></span>  
  
-   <span data-ttu-id="47a3e-115">メモリ最適化ファイルグループに対して、新しいコンテナーを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-115">You can add new containers to a memory-optimized filegroup.</span></span> <span data-ttu-id="47a3e-116">持続性のあるメモリ最適化テーブルに必要なストレージを拡張し、複数のコンテナーに i/o を分散させるために、新しいコンテナーが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-116">You may need a new container to expand the storage needed for durable memory-optimized table and also to distribute I/O across multiple containers.</span></span>  
  
-   <span data-ttu-id="47a3e-117">メモリ最適化ファイルグループでのデータの移動は、AlwaysOn 可用性グループ構成によって最適化されます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-117">Data movement with a memory-optimized filegroup is optimized in an AlwaysOn Availability Group configuration.</span></span> <span data-ttu-id="47a3e-118">セカンダリ レプリカに送信されるファイルストリームのファイルとは異なり、メモリ最適化ファイルグループ内のチェックポイント ファイル (データとデルタの両方) は、セカンダリ レプリカには送信されません。</span><span class="sxs-lookup"><span data-stu-id="47a3e-118">Unlike filestream files that are sent to secondary replicas, the checkpoint files (both data and delta) within the memory-optimized filegroup are not sent to secondary replicas.</span></span> <span data-ttu-id="47a3e-119">データ ファイルとデルタ ファイルは、セカンダリ レプリカのトランザクション ログを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-119">The data and delta files are constructed using the transaction log on the secondary replica.</span></span>  
  
<span data-ttu-id="47a3e-120">メモリ最適化ファイルグループには、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-120">The following limitations of memory-optimized filegroup,</span></span>  
  
-   <span data-ttu-id="47a3e-121">メモリ最適化ファイルグループを作成した後、それを削除する唯一の方法はデータベースを削除することです。</span><span class="sxs-lookup"><span data-stu-id="47a3e-121">Once you create a memory-optimized filegroup, you can only remove it by dropping the database.</span></span> <span data-ttu-id="47a3e-122">運用環境において、メモリ最適化ファイルグループの削除が必要になることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="47a3e-122">In a production environment, it is unlikely that you will need to remove the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="47a3e-123">空ではないコンテナーを削除することや、メモリ最適化ファイルグループ内でデータ ファイルとデルタ ファイルのペアを別のコンテナーに移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="47a3e-123">You cannot drop a non-empty container or move data and delta file pairs to another container in the memory-optimized filegroup.</span></span>  
  
## <a name="configuring-a-memory-optimized-filegroup"></a><span data-ttu-id="47a3e-124">メモリ最適化ファイルグループの構成</span><span class="sxs-lookup"><span data-stu-id="47a3e-124">Configuring a Memory-Optimized Filegroup</span></span>  
<span data-ttu-id="47a3e-125">メモリ最適化ファイルグループ内で複数のコンテナーを作成し、それらを複数のドライブに分散して、データをメモリにストリーミングするための帯域幅をより多く確保することを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="47a3e-125">Consider creating multiple containers in the memory-optimized filegroup and distribute them on different drives to achieve more bandwidth to stream the data into memory.</span></span>  
  
<span data-ttu-id="47a3e-126">記憶域を構成する場合には、持続性のあるメモリ最適化テーブルの 4 倍のサイズの空きディスク領域を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-126">When configuring storage, you must provide free disk space that is four times the size of durable memory-optimized tables.</span></span> <span data-ttu-id="47a3e-127">I/o サブシステムが、ワークロードに必要な IOPS をサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="47a3e-127">Ensure that your I/O subsystem supports the required IOPS for your workload.</span></span> <span data-ttu-id="47a3e-128">データ ファイルとデルタ ファイルのペアが特定の IOPS で作成される場合は、格納操作とマージ操作のために、3 倍の IOPS が必要です。</span><span class="sxs-lookup"><span data-stu-id="47a3e-128">If data and delta file pairs are populated at a given IOPS, you need three times that IOPS to account for storing and merge operations.</span></span> <span data-ttu-id="47a3e-129">メモリ最適化ファイルグループに 1 つ以上のコンテナーを追加する方法で、記憶域容量と IOPS を追加できます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-129">You can add storage capacity and IOPS by adding one or more containers to the memory-optimized filegroup.</span></span>  
  
<span data-ttu-id="47a3e-130">複数のコンテナーと複数のドライブを使用するシナリオでは、データ ファイルとデルタ ファイルはラウンドロビン方式でコンテナーに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-130">In a multiple container, multiple drive scenario, data and delta files are allocated in a round-robin fashion into containers.</span></span> <span data-ttu-id="47a3e-131">最初のデータ ファイルは最初のコンテナーから割り当てられ、デルタ ファイルは次のコンテナーから割り当てられ、というように、この割り当てパターンが繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-131">The first data file is allocated from the first container and the delta file is allocated from the next container and this allocation pattern repeats.</span></span> <span data-ttu-id="47a3e-132">奇数個のドライブがあり、それぞれを 1 個のコンテナーにマップした場合は、この割り当て方法により、データ ファイルとデルタ ファイルが複数のコンテナーに対して均等に分散されます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-132">This allocation scheme distributes data and delta files evenly across containers if you have an odd number of drives, each mapped to one container.</span></span> <span data-ttu-id="47a3e-133">一方、偶数個のドライブがあり、それぞれを 1 個のコンテナーにマップした場合は、データ ファイルが奇数番目のドライブにマップされ、デルタ ファイルが偶数番目のドライブにマップされて不均等な記憶域という結果になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-133">However, if you have an even number of drives, each mapped to a container, it can result in imbalanced storage with data files mapped to odd drives and delta files mapped to even drives.</span></span> <span data-ttu-id="47a3e-134">復旧時の i/o の均衡ストリームを取得するには、次の例に示すように、データファイルとデルタファイルのペアを同じスピンドル/ストレージに配置することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="47a3e-134">To obtain a balanced stream of I/O on recovery, consider placing pairs of data and delta files on the same spindles/storage as described in the example below.</span></span>  

> [!CAUTION]
> <span data-ttu-id="47a3e-135">メモリ最適化ファイルグループに `MAXSIZE` 値が設定されており、チェックポイント ファイルがコンテナーの最大サイズを超えた場合、データベースは SUSPECT 状態になります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-135">If a `MAXSIZE` value is set for the memory-optimized filegroup, and checkpoint files exceed the max size of the container, then the database will become SUSPECT.</span></span>   
> <span data-ttu-id="47a3e-136">この場合は、データベースの OFFLINE や ONLINE への設定を試行しないでください。試行すると、データベースが RECOVERY_PENDING 状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-136">In this case do not attempt to set the database OFFLINE and ONLINE, causing the database to stay in RECOVERY_PENDING state.</span></span>
  
### <a name="example"></a><span data-ttu-id="47a3e-137">例</span><span class="sxs-lookup"><span data-stu-id="47a3e-137">Example</span></span> 
<span data-ttu-id="47a3e-138">2 個のコンテナーを持つメモリ最適化ファイルグループについて考えます。コンテナー 1 は X ドライブにあり、コンテナー 2 は Y ドライブにあります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-138">Consider a memory-optimized filegroup with two containers: container 1 on drive X and container 2 on drives Y.</span></span>  
<span data-ttu-id="47a3e-139">データ ファイルとデルタ ファイルの割り当てはラウンドロビン方式でなされるため、コンテナー 1 にはデータ ファイルのみが格納され、コンテナー 2 にはデルタ ファイルのみが格納されます。このためデータ ファイルがデルタ ファイルよりはるかに大きくなり、記憶域と IOPS の両方に関して継続的に不均等が発生することになります。</span><span class="sxs-lookup"><span data-stu-id="47a3e-139">Since the allocation of data and delta files is done in round-robin fashion, container 1 will only have data files and container 2 will only have delta files, which leads to imbalanced persistence for storage as well as input/output operations per second, as data files are significantly larger than the delta files.</span></span>    
<span data-ttu-id="47a3e-140">データファイルとデルタファイルを複数のドライブ X と Y に均等に分散させるには、2つではなく4つのコンテナーを作成し、最初の2つのコンテナーをドライブ X に、次の2つのコンテナーを Y ドライブにマップします。</span><span class="sxs-lookup"><span data-stu-id="47a3e-140">To distribute data and delta files uniformly across drives X and Y, create four containers instead of two, and map the first two containers to drive X and the next two containers to drive Y.</span></span>  
<span data-ttu-id="47a3e-141">ラウンドロビンによる割り当てでは、最初のデータと最初のデルタファイルはそれぞれ、ドライブ X にマップされるコンテナー-1 とコンテナー2から割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-141">With round-robin allocation, the first data and first delta file will be allocated from container-1 and container-2 respectively, which are mapped to drive X.</span></span>   
<span data-ttu-id="47a3e-142">同様に、次のデータファイルとデルタファイルは、ドライブ Y にマップされている container-3 と container-4 から割り当てられます。これにより、データファイルとデルタファイルを2つのドライブに均等に分散させることができます。</span><span class="sxs-lookup"><span data-stu-id="47a3e-142">Similarly, the next data and delta file will be allocated from container-3 and container-4 which are mapped to drive Y. This allows distributing data and delta files across two drives uniformly.</span></span>  
 
  
## <a name="see-also"></a><span data-ttu-id="47a3e-143">参照</span><span class="sxs-lookup"><span data-stu-id="47a3e-143">See Also</span></span>  
<span data-ttu-id="47a3e-144">[メモリ最適化オブジェクト用ストレージの作成と管理](creating-and-managing-storage-for-memory-optimized-objects.md)   </span><span class="sxs-lookup"><span data-stu-id="47a3e-144">[Creating and Managing Storage for Memory-Optimized Objects](creating-and-managing-storage-for-memory-optimized-objects.md)   </span></span>  
[<span data-ttu-id="47a3e-145">データベース ファイルとファイル グループ</span><span class="sxs-lookup"><span data-stu-id="47a3e-145">Database Files and Filegroups</span></span>](../../relational-databases/databases/database-files-and-filegroups.md)    
  
