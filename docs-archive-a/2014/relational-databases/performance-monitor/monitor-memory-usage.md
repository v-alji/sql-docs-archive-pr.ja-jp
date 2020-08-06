---
title: メモリ使用率の監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- tuning databases [SQL Server], memory
- monitoring server performance [SQL Server], memory usage
- isolating memory [SQL Server]
- paging rate [SQL Server]
- memory [SQL Server], monitoring usage
- monitoring [SQL Server], memory usage
- low-memory conditions
- database monitoring [SQL Server], memory usage
- available memory [SQL Server]
- page faults [SQL Server]
- monitoring performance [SQL Server], memory usage
- server performance [SQL Server], memory
ms.assetid: 1aee3933-a11c-4b87-91b7-32f5ea38c87f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1986d9576f9b067cad18f27d4febbf097ed52703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739739"
---
# <a name="monitor-memory-usage"></a><span data-ttu-id="6cf09-102">メモリ使用率の監視</span><span class="sxs-lookup"><span data-stu-id="6cf09-102">Monitor Memory Usage</span></span>
  <span data-ttu-id="6cf09-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを定期的に監視し、メモリ使用率が通常の範囲内であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-103">Monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically to confirm that memory usage is within typical ranges.</span></span>  
  
 <span data-ttu-id="6cf09-104">メモリの少ない状況を監視するには、次のオブジェクト カウンターを使用します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-104">To monitor for a low-memory condition, use the following object counters:</span></span>  
  
-   <span data-ttu-id="6cf09-105">**Memory:Available Bytes**</span><span class="sxs-lookup"><span data-stu-id="6cf09-105">**Memory: Available Bytes**</span></span>  
  
-   <span data-ttu-id="6cf09-106">**Memory:Pages/sec**</span><span class="sxs-lookup"><span data-stu-id="6cf09-106">**Memory: Pages/sec**</span></span>  
  
 <span data-ttu-id="6cf09-107">**Available Bytes** カウンターは、プロセスで現在使用できるメモリのバイト数を示します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-107">The **Available Bytes** counter indicates how many bytes of memory are currently available for use by processes.</span></span> <span data-ttu-id="6cf09-108">**Pages/sec** カウンターは、ハード ページ フォールトのためにディスクから取り出されたページ数や、ページ フォールトによって作業セット内の領域を解放するためにディスクに書き込まれたページ数を示します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-108">The **Pages/sec** counter indicates the number of pages that either were retrieved from disk due to hard page faults or written to disk to free space in the working set due to page faults.</span></span>  
  
 <span data-ttu-id="6cf09-109">**Available Bytes** カウンターの値が低い場合、コンピューターのメモリが全体的に不足しているか、アプリケーションがメモリを解放していないことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="6cf09-109">Low values for the **Available Bytes** counter can indicate that there is an overall shortage of memory on the computer or that an application is not releasing memory.</span></span> <span data-ttu-id="6cf09-110">**Pages/sec** カウンターの値が高い場合、ページングが過剰であることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="6cf09-110">A high rate for the **Pages/sec** counter could indicate excessive paging.</span></span> <span data-ttu-id="6cf09-111">ディスク利用状況がページングによるものかどうかを確認するには、**Memory:Page Faults/sec** カウンターを監視します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-111">Monitor the **Memory: Page Faults/sec** counter to make sure that the disk activity is not caused by paging.</span></span>  
  
 <span data-ttu-id="6cf09-112">コンピューターに十分なメモリがある場合でも、ページングとページ フォールトが低い率で発生することは問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="6cf09-112">A low rate of paging (and hence page faults) is typical, even if the computer has plenty of available memory.</span></span> <span data-ttu-id="6cf09-113">Microsoft Windows Virtual Memory Manager (VMM) では、プロセスの作業セットのサイズを小さくするときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と他のプロセスからページを取得します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-113">The Microsoft Windows Virtual Memory Manager (VMM) takes pages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and other processes as it trims the working-set sizes of those processes.</span></span> <span data-ttu-id="6cf09-114">この VMM の動作が、ページ フォールトの原因になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6cf09-114">This VMM activity tends to cause page faults.</span></span> <span data-ttu-id="6cf09-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または他のプロセスが過剰なページングの原因であるかどうかを判断するには、**Process:Page Faults/sec** カウンター ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス インスタンス) を監視します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-115">To determine whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or another process is the cause of excessive paging, monitor the **Process: Page Faults/sec** counter for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process instance.</span></span>  
  
 <span data-ttu-id="6cf09-116">過剰なページングの解決方法の詳細については、Windows オペレーティング システムのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cf09-116">For more information about resolving excessive paging, see the Windows operating system documentation.</span></span>  
  
## <a name="isolating-memory-used-by-sql-server"></a><span data-ttu-id="6cf09-117">SQL Server が使用するメモリの分離</span><span class="sxs-lookup"><span data-stu-id="6cf09-117">Isolating Memory Used by SQL Server</span></span>  
 <span data-ttu-id="6cf09-118">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は使用可能なシステム リソースに基づいて、必要なメモリを動的に変更します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-118">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] changes its memory requirements dynamically, on the basis of available system resources.</span></span> <span data-ttu-id="6cf09-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により多くのメモリが必要な場合は、空き物理メモリが使用可能かどうかを調べるためにオペレーティング システムに問い合わせ、使用可能なメモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-119">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] needs more memory, it queries the operating system to determine whether free physical memory is available and uses the available memory.</span></span> <span data-ttu-id="6cf09-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、現在割り当てられているメモリが必要ない場合は、そのメモリをオペレーティング システムに対して解放します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-120">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not need the memory currently allocated to it, it releases the memory to the operating system.</span></span> <span data-ttu-id="6cf09-121">ただし、**minservermemory** および **maxservermemory** サーバー構成オプションを使用して、オプションをオーバーライドしてメモリを動的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6cf09-121">However, you can override the option to dynamically use memory by using the **minservermemory**, and **maxservermemory** server configuration options.</span></span> <span data-ttu-id="6cf09-122">詳細については、「 [サーバー メモリ オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cf09-122">For more information, see [Server Memory Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
 <span data-ttu-id="6cf09-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用されるメモリの量を監視するには、次のパフォーマンス カウンターを調べます。</span><span class="sxs-lookup"><span data-stu-id="6cf09-123">To monitor the amount of memory that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses, examine the following performance counters:</span></span>  
  
-   <span data-ttu-id="6cf09-124">**Process:Working Set**</span><span class="sxs-lookup"><span data-stu-id="6cf09-124">**Process: Working Set**</span></span>  
  
-   <span data-ttu-id="6cf09-125">**SQL Server:Buffer Manager:Buffer Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="6cf09-125">**SQL Server: Buffer Manager: Buffer Cache Hit Ratio**</span></span>  
  
-   <span data-ttu-id="6cf09-126">**SQL Server:Buffer Manager:Database Pages**</span><span class="sxs-lookup"><span data-stu-id="6cf09-126">**SQL Server: Buffer Manager: Database Pages**</span></span>  
  
-   <span data-ttu-id="6cf09-127">**SQL Server:Memory Manager:Total Server Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="6cf09-127">**SQL Server: Memory Manager: Total Server Memory (KB)**</span></span>  
  
 <span data-ttu-id="6cf09-128">**WorkingSet** カウンターは、プロセスが使用しているメモリの量を示します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-128">The **WorkingSet** counter shows the amount of memory that is used by a process.</span></span> <span data-ttu-id="6cf09-129">この数値が **min server memory** および **max server memory** サーバー オプションで設定したメモリの量を常に下回っている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は過剰なメモリを使用するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="6cf09-129">If this number is consistently below the amount of memory that is set by the **min server memory** and **max server memory** server options, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use too much memory.</span></span>  
  
 <span data-ttu-id="6cf09-130">**Buffer Cache Hit Ratio** カウンターは、アプリケーション固有のカウンターです。</span><span class="sxs-lookup"><span data-stu-id="6cf09-130">The **Buffer Cache Hit Ratio** counter is specific to an application.</span></span> <span data-ttu-id="6cf09-131">適切な値は 90% 以上です。</span><span class="sxs-lookup"><span data-stu-id="6cf09-131">However, a rate of 90 percent or higher is desirable.</span></span> <span data-ttu-id="6cf09-132">値が常に 90% より大きくなるまで、メモリを追加してください。</span><span class="sxs-lookup"><span data-stu-id="6cf09-132">Add more memory until the value is consistently greater than 90 percent.</span></span> <span data-ttu-id="6cf09-133">90% より大きい値は、90% を超えるデータ要求がデータ キャッシュで処理できたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="6cf09-133">A value greater than 90 percent indicates that more than 90 percent of all requests for data were satisfied from the data cache.</span></span>  
  
 <span data-ttu-id="6cf09-134">**TotalServerMemory (KB)** カウンターがコンピューターの物理メモリ容量に比べて常に高い場合、より多くのメモリが必要であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="6cf09-134">If the **TotalServerMemory (KB)** counter is consistently high compared to the amount of physical memory in the computer, it may indicate that more memory is required.</span></span>  
  
## <a name="determining-current-memory-allocation"></a><span data-ttu-id="6cf09-135">現在のメモリ割り当ての特定</span><span class="sxs-lookup"><span data-stu-id="6cf09-135">Determining Current Memory Allocation</span></span>  
 <span data-ttu-id="6cf09-136">次のクエリでは、現在割り当てられているメモリに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="6cf09-136">The following query returns information about currently allocated memory.</span></span>  
  
```  
SELECT  
(physical_memory_in_use_kb/1024) AS Memory_usedby_Sqlserver_MB,  
(locked_page_allocations_kb/1024) AS Locked_pages_used_Sqlserver_MB,  
(total_virtual_address_space_kb/1024) AS Total_VAS_in_MB,  
process_physical_memory_low,  
process_virtual_memory_low  
FROM sys.dm_os_process_memory;  
```  
  
  
