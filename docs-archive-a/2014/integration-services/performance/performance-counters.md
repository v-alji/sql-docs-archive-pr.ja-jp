---
title: パフォーマンス カウンター | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], performance counters
- performance counters [Integration Services]
- data flow [Integration Services], performance
- counters [Integration Services]
- data flow engine [Integration Services]
ms.assetid: 11e17f4e-72ed-44d7-a71d-a68937a78e4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b20ac056894066114883153030943bec1c05963
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640122"
---
# <a name="performance-counters"></a><span data-ttu-id="286f9-102">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="286f9-102">Performance Counters</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="286f9-103">により、データ フロー エンジンのパフォーマンスを監視するために使用できるパフォーマンス カウンターのセットがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="286f9-103">installs a set of performance counters that you can use to monitor the performance of the data flow engine.</span></span> <span data-ttu-id="286f9-104">たとえば、"Buffers spooled" カウンターを調べると、パッケージの実行中にデータ バッファーがディスクに一時的に書き込まれているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="286f9-104">For example, you can watch the "Buffers spooled" counter to determine whether data buffers are being written to disk temporarily while a package is running.</span></span> <span data-ttu-id="286f9-105">このスワップは、パフォーマンスを低下させると共に、コンピューターのメモリが不足していることを示しています。</span><span class="sxs-lookup"><span data-stu-id="286f9-105">This swapping reduces performance and indicates that the computer has insufficient memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="286f9-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を実行するコンピューターに [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]をインストールした後、コンピューターを [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]にアップグレードすると、アップグレード プロセスにより [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパフォーマンス カウンターがコンピューターから削除されます。</span><span class="sxs-lookup"><span data-stu-id="286f9-106">If you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on a computer that is running [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], and then upgrade that computer to [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)], the upgrade process removes the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] performance counters from the computer.</span></span> <span data-ttu-id="286f9-107">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパフォーマンス カウンターをコンピューターに復元するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップを修復モードで実行してください。</span><span class="sxs-lookup"><span data-stu-id="286f9-107">To restore the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] performance counters on the computer, run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup in repair mode.</span></span>  
  
 <span data-ttu-id="286f9-108">次の表では、パフォーマンス カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="286f9-108">The following table describes the performance counters.</span></span>  
  
|<span data-ttu-id="286f9-109">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="286f9-109">Performance counter</span></span>|<span data-ttu-id="286f9-110">説明</span><span class="sxs-lookup"><span data-stu-id="286f9-110">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="286f9-111">BLOB bytes read</span><span class="sxs-lookup"><span data-stu-id="286f9-111">BLOB bytes read</span></span>|<span data-ttu-id="286f9-112">データ フロー エンジンがすべてのソースから読み取ったバイナリ ラージ オブジェクト (BLOB) データのバイト数。</span><span class="sxs-lookup"><span data-stu-id="286f9-112">The number of bytes of binary large object (BLOB) data that the data flow engine has read from all sources.</span></span>|  
|<span data-ttu-id="286f9-113">BLOB bytes written</span><span class="sxs-lookup"><span data-stu-id="286f9-113">BLOB bytes written</span></span>|<span data-ttu-id="286f9-114">データ フロー エンジンがすべての出力先に書き込んだ BLOB データのバイト数。</span><span class="sxs-lookup"><span data-stu-id="286f9-114">The number of bytes of BLOB data that the data flow engine has written to all destinations.</span></span>|  
|<span data-ttu-id="286f9-115">BLOB files in use</span><span class="sxs-lookup"><span data-stu-id="286f9-115">BLOB files in use</span></span>|<span data-ttu-id="286f9-116">データ フロー エンジンがスプールのために現在使用している BLOB ファイル数。</span><span class="sxs-lookup"><span data-stu-id="286f9-116">The number of BLOB files that the data flow engine currently is using for spooling.</span></span>|  
|<span data-ttu-id="286f9-117">Buffer memory</span><span class="sxs-lookup"><span data-stu-id="286f9-117">Buffer memory</span></span>|<span data-ttu-id="286f9-118">使用中のメモリの量。</span><span class="sxs-lookup"><span data-stu-id="286f9-118">The amount of memory that is in use.</span></span> <span data-ttu-id="286f9-119">この数値には物理メモリと仮想メモリの両方が含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="286f9-119">This may include both physical and virtual memory.</span></span> <span data-ttu-id="286f9-120">数値が物理メモリ容量より大きい場合、メモリ スワップが増加していることを表す **Buffers Spooled** の数も増加します。</span><span class="sxs-lookup"><span data-stu-id="286f9-120">When this number is larger than the amount of physical memory, the **Buffers Spooled** count rises as an indication that memory swapping is increasing.</span></span> <span data-ttu-id="286f9-121">メモリ スワップが増加すると、データ フロー エンジンのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="286f9-121">Increased memory swapping slows performance of the data flow engine.</span></span>|  
|<span data-ttu-id="286f9-122">Buffers in use</span><span class="sxs-lookup"><span data-stu-id="286f9-122">Buffers in use</span></span>|<span data-ttu-id="286f9-123">すべてのデータ フロー コンポーネントおよびデータ フロー エンジンが現在使用している、すべての種類のバッファー オブジェクト数。</span><span class="sxs-lookup"><span data-stu-id="286f9-123">The number of buffer objects, of all types, that all data flow components and the data flow engine is currently using.</span></span>|  
|<span data-ttu-id="286f9-124">Buffers Spooled</span><span class="sxs-lookup"><span data-stu-id="286f9-124">Buffers spooled</span></span>|<span data-ttu-id="286f9-125">ディスクに現在書き込まれているバッファー数。</span><span class="sxs-lookup"><span data-stu-id="286f9-125">The number of buffers currently written to the disk.</span></span> <span data-ttu-id="286f9-126">データ フロー エンジンが使用する物理メモリが不足している場合、現在使用されていないバッファーはディスクに書き込まれ、必要になった時点で再読み込みされます。</span><span class="sxs-lookup"><span data-stu-id="286f9-126">If the data flow engine runs low on physical memory, buffers not currently used are written to disk and then reloaded when needed.</span></span>|  
|<span data-ttu-id="286f9-127">Flat buffer memory</span><span class="sxs-lookup"><span data-stu-id="286f9-127">Flat buffer memory</span></span>|<span data-ttu-id="286f9-128">すべてのフラット バッファーが使用するメモリ総量 (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="286f9-128">The total amount of memory, in bytes, that all flat buffers use.</span></span> <span data-ttu-id="286f9-129">フラット バッファーはコンポーネントがデータの格納に使用するメモリ ブロックです。</span><span class="sxs-lookup"><span data-stu-id="286f9-129">Flat buffers are blocks of memory that a component uses to store data.</span></span> <span data-ttu-id="286f9-130">フラット バッファーはバイト単位でアクセスできる大きなブロックです。</span><span class="sxs-lookup"><span data-stu-id="286f9-130">A flat buffer is a large block of bytes that is accessed byte by byte.</span></span>|  
|<span data-ttu-id="286f9-131">Flat buffers in use</span><span class="sxs-lookup"><span data-stu-id="286f9-131">Flat buffers in use</span></span>|<span data-ttu-id="286f9-132">データ フロー エンジンが使用するフラット バッファー数。</span><span class="sxs-lookup"><span data-stu-id="286f9-132">The number of flat buffers that the Data flow engine uses.</span></span> <span data-ttu-id="286f9-133">フラット バッファーはすべてプライベート バッファーです。</span><span class="sxs-lookup"><span data-stu-id="286f9-133">All flat buffers are private buffers.</span></span>|  
|<span data-ttu-id="286f9-134">Private buffer memory</span><span class="sxs-lookup"><span data-stu-id="286f9-134">Private buffer memory</span></span>|<span data-ttu-id="286f9-135">すべてのプライベート バッファーが使用しているメモリ総量。</span><span class="sxs-lookup"><span data-stu-id="286f9-135">The total amount of memory in use by all private buffers.</span></span> <span data-ttu-id="286f9-136">データ フロー エンジンがデータ フローをサポートするために作成した場合、バッファーはプライベートではありません。</span><span class="sxs-lookup"><span data-stu-id="286f9-136">A buffer is not private if the data flow engine creates it to support data flow.</span></span> <span data-ttu-id="286f9-137">プライベート バッファーは、変換が一時作業のためだけに使用するバッファーです。</span><span class="sxs-lookup"><span data-stu-id="286f9-137">A private buffer is a buffer that a transformation uses for temporary work only.</span></span> <span data-ttu-id="286f9-138">たとえば、集計変換は作業のためにプライベート バッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="286f9-138">For example, the Aggregation transformation uses private buffers to do its work.</span></span>|  
|<span data-ttu-id="286f9-139">Private buffers in use</span><span class="sxs-lookup"><span data-stu-id="286f9-139">Private buffers in use</span></span>|<span data-ttu-id="286f9-140">変換が使用するバッファー数。</span><span class="sxs-lookup"><span data-stu-id="286f9-140">The number of buffers that transformations use.</span></span>|  
|<span data-ttu-id="286f9-141">Rows read</span><span class="sxs-lookup"><span data-stu-id="286f9-141">Rows read</span></span>|<span data-ttu-id="286f9-142">ソースが生成した行数。</span><span class="sxs-lookup"><span data-stu-id="286f9-142">The number of rows that a source produces.</span></span> <span data-ttu-id="286f9-143">この数値には、参照変換が参照テーブルから読み込む行は含まれません。</span><span class="sxs-lookup"><span data-stu-id="286f9-143">The number does not include rows read from reference tables by the Lookup transformation.</span></span>|  
|<span data-ttu-id="286f9-144">Rows written</span><span class="sxs-lookup"><span data-stu-id="286f9-144">Rows written</span></span>|<span data-ttu-id="286f9-145">出力先に出力された行数。</span><span class="sxs-lookup"><span data-stu-id="286f9-145">The number of rows offered to a destination.</span></span> <span data-ttu-id="286f9-146">この数値には、出力先データ ストアに書き込まれた行は含まれません。</span><span class="sxs-lookup"><span data-stu-id="286f9-146">The number does not reflect rows written to the destination data store.</span></span>|  
  
 <span data-ttu-id="286f9-147">Microsoft 管理コンソール (MMC) のパフォーマンス スナップインを使用して、パフォーマンス カウンターの値を取得するログを作成します。</span><span class="sxs-lookup"><span data-stu-id="286f9-147">You use the Performance Microsoft Management Console (MMC) snap-in to create a log that captures performance counters.</span></span>  
  
 <span data-ttu-id="286f9-148">パフォーマンスを向上させる方法については、「 [データ フロー パフォーマンス機能](../data-flow/data-flow-performance-features.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="286f9-148">For information about how to improve performance, see [Data Flow Performance Features](../data-flow/data-flow-performance-features.md).</span></span>  
  
## <a name="obtain-performance-counter-statistics"></a><span data-ttu-id="286f9-149">パフォーマンス カウンター統計の取得</span><span class="sxs-lookup"><span data-stu-id="286f9-149">Obtain Performance Counter Statistics</span></span>  
 <span data-ttu-id="286f9-150">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置された [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトについて、[dm_execution_performance_counters (SSISDB データベース)](/sql/integration-services/functions-dm-execution-performance-counters) 関数を使用してパフォーマンス カウンター統計を取得できます。</span><span class="sxs-lookup"><span data-stu-id="286f9-150">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you can obtain performance counter statistics by using the [dm_execution_performance_counters &#40;SSISDB Database&#41;](/sql/integration-services/functions-dm-execution-performance-counters) function.</span></span>  
  
 <span data-ttu-id="286f9-151">次の例では、ID が 34 である処理中の実行の統計を関数で返します。</span><span class="sxs-lookup"><span data-stu-id="286f9-151">In the following example, the function returns statistics for a running execution with an ID of 34.</span></span>  
  
```  
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
 <span data-ttu-id="286f9-152">次の例では、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーで処理中のすべての実行の統計を関数で返します。</span><span class="sxs-lookup"><span data-stu-id="286f9-152">In the following example, the function returns statistics for all the executions running on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
```  
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="286f9-153">`ssis_admin` データベース ロールのメンバーである場合は、処理中のすべての実行のパフォーマンス統計が返されます。</span><span class="sxs-lookup"><span data-stu-id="286f9-153">If you are a member of the `ssis_admin` database role, performance statistics for all running executions are returned.</span></span>  <span data-ttu-id="286f9-154">`ssis_admin` データベース ロールのメンバーでない場合は、処理中の実行のうち読み取り権限を持つ実行のパフォーマンス統計が返されます。</span><span class="sxs-lookup"><span data-stu-id="286f9-154">If you are not a member of the `ssis_admin` database role, performance statistics for the running executions for which you have read permissions, are returned.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="286f9-155">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="286f9-155">Related Content</span></span>  
  
-   <span data-ttu-id="286f9-156">codeplex.com のツール ( [Business Intelligence Development Studio のための SSIS パフォーマンス ビジュアライゼーション (CodePlex Project)](https://go.microsoft.com/fwlink/?LinkId=146626))</span><span class="sxs-lookup"><span data-stu-id="286f9-156">Tool, [SSIS Performance Visualization for Business Intelligence Development Studio (CodePlex Project)](https://go.microsoft.com/fwlink/?LinkId=146626), on codeplex.com.</span></span>  
  
-   <span data-ttu-id="286f9-157">msdn.microsoft.com のビデオ ( [社内の SSIS パッケージのパフォーマンスの測定と理解 (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=150497))</span><span class="sxs-lookup"><span data-stu-id="286f9-157">Video, [Measuring and Understanding the Performance of Your SSIS Packages in the Enterprise (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=150497), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="286f9-158">support.microsoft.com のサポート技術情報 ( [Windows Server 2008 へのアップグレード後にパフォーマンス モニターで SSIS パフォーマンス カウンターが使用できなくなる](https://go.microsoft.com/fwlink/?LinkId=235319))</span><span class="sxs-lookup"><span data-stu-id="286f9-158">Support article, [The SSIS performance counter is no longer available in the Performance Monitor after you upgrade to Windows Server 2008](https://go.microsoft.com/fwlink/?LinkId=235319), on support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286f9-159">参照</span><span class="sxs-lookup"><span data-stu-id="286f9-159">See Also</span></span>  
 [<span data-ttu-id="286f9-160">プロジェクトとパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="286f9-160">Execution of Projects and Packages</span></span>](../packages/run-integration-services-ssis-packages.md)  
  
  
