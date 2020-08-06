---
title: CPU 使用率の監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], CPU usage
- tuning databases [SQL Server], CPU usage
- processors [SQL Server], monitoring usage
- database performance [SQL Server], CPU usage
- monitoring CPU usage [SQL Server]
- server performance [SQL Server], CPU usage
- database monitoring [SQL Server], CPU usage
- monitoring [SQL Server], CPU usage
- processors [SQL Server]
- CPU [SQL Server], monitoring
- monitoring server performance [SQL Server], CPU usage
ms.assetid: 2a02a3b6-07b2-4ad0-8a24-670414d19812
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f08d49348fd25593f27a87f2b0123f7ce43e35b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739750"
---
# <a name="monitor-cpu-usage"></a><span data-ttu-id="a76d3-102">CPU 使用率の監視</span><span class="sxs-lookup"><span data-stu-id="a76d3-102">Monitor CPU Usage</span></span>
  <span data-ttu-id="a76d3-103">CPU 使用率が通常の範囲内にあるかどうかを確認するため、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを定期的に監視する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a76d3-103">Monitor an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically to determine whether CPU usage rates are within normal ranges.</span></span> <span data-ttu-id="a76d3-104">CPU 使用率が常に高い場合は、CPU のアップグレードまたは多重プロセッサの追加を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a76d3-104">A continually high rate of CPU usage may indicate the need to upgrade the CPU or add multiple processors.</span></span> <span data-ttu-id="a76d3-105">また、CPU 使用率が高い場合、アプリケーションのチューニングや設計に問題がある可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="a76d3-105">Alternatively, a high CPU usage rate may indicate a poorly tuned or designed application.</span></span> <span data-ttu-id="a76d3-106">この場合は、アプリケーションを最適化することで CPU 使用率を下げることができます。</span><span class="sxs-lookup"><span data-stu-id="a76d3-106">Optimizing the application can lower CPU utilization.</span></span>  
  
 <span data-ttu-id="a76d3-107">CPU 使用率を効率よく確認するには、システム モニターの **Processor:% Processor Time** カウンターを使用します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-107">An efficient way to determine CPU usage is to use the **Processor:% Processor Time** counter in System Monitor.</span></span> <span data-ttu-id="a76d3-108">このカウンターは、アイドル状態でないスレッドを実行するために CPU が費やす時間を監視します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-108">This counter monitors the amount of time the CPU spends executing a thread that is not idle.</span></span> <span data-ttu-id="a76d3-109">使用率が常に 80 ～ 90% である場合は、CPU のアップグレードまたはプロセッサの追加が必要です。</span><span class="sxs-lookup"><span data-stu-id="a76d3-109">A consistent state of 80 percent to 90 percent may indicate the need to upgrade your CPU or add more processors.</span></span> <span data-ttu-id="a76d3-110">多重プロセッサ システムでは、各プロセッサについて、このカウンターを個別に監視します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-110">For multiprocessor systems, monitor a separate instance of this counter for each processor.</span></span> <span data-ttu-id="a76d3-111">この値は、特定のプロセッサの処理時間の合計を表します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-111">This value represents the sum of processor time on a specific processor.</span></span> <span data-ttu-id="a76d3-112">すべてのプロセッサの平均値を調べるには、代わりに **System: %Total Processor Time** カウンターを使用します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-112">To determine the average for all processors, use the **System: %Total Processor Time** counter instead.</span></span>  
  
 <span data-ttu-id="a76d3-113">必要に応じて、次のカウンターでプロセッサ使用率を監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="a76d3-113">Optionally, you can also monitor the following counters to monitor processor usage:</span></span>  
  
-   <span data-ttu-id="a76d3-114">**Processor: % Privileged Time**</span><span class="sxs-lookup"><span data-stu-id="a76d3-114">**Processor: % Privileged Time**</span></span>  
  
     <span data-ttu-id="a76d3-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の I/O 要求など、Microsoft Windows のカーネル コマンドの実行にプロセッサが費やす時間の比率を示します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-115">Corresponds to the percentage of time the processor spends on execution of Microsoft Windows kernel commands, such as processing of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I/O requests.</span></span> <span data-ttu-id="a76d3-116">**Physical Disk** カウンターの値が高いときに、このカウンターの値が常に高い場合は、より高速で効率的なディスク サブシステムのインストールを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a76d3-116">If this counter is consistently high when the **Physical Disk** counters are high, consider installing a faster or more efficient disk subsystem.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a76d3-117">カーネルの処理時間をどの程度使用するかは、ディスク コントローラーやドライバーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a76d3-117">Different disk controllers and drivers use different amounts of kernel processing time.</span></span> <span data-ttu-id="a76d3-118">効率のよいコントローラーやドライバーは処理時間をそれほど必要としないため、ユーザー アプリケーションの利用可能な処理時間が多くなり、全体的な処理能力が向上します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-118">Efficient controllers and drivers use less privileged time, leaving more processing time available for user applications, increasing overall throughput.</span></span>  
  
-   <span data-ttu-id="a76d3-119">**Processor: %User Time**</span><span class="sxs-lookup"><span data-stu-id="a76d3-119">**Processor: %User Time**</span></span>  
  
     <span data-ttu-id="a76d3-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]などのユーザー プロセスの実行にプロセッサが費やす時間比率を示します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-120">Corresponds to the percentage of time that the processor spends on executing user processes such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="a76d3-121">**System:Processor Queue Length**</span><span class="sxs-lookup"><span data-stu-id="a76d3-121">**System: Processor Queue Length**</span></span>  
  
     <span data-ttu-id="a76d3-122">プロセッサ時間を待っているスレッドの数を示します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-122">Corresponds to the number of threads waiting for processor time.</span></span> <span data-ttu-id="a76d3-123">プロセスのスレッドが、使用できるよりも多くのプロセッサ サイクルを必要とする場合は、プロセッサのボトルネックが生じます。</span><span class="sxs-lookup"><span data-stu-id="a76d3-123">A processor bottleneck develops when threads of a process require more processor cycles than are available.</span></span> <span data-ttu-id="a76d3-124">複数のプロセスがプロセッサ時間を利用する場合、状況によっては、より高速なプロセッサのインストールが必要になります。</span><span class="sxs-lookup"><span data-stu-id="a76d3-124">If more than a few processes attempt to utilize the processor's time, you might need to install a faster processor.</span></span> <span data-ttu-id="a76d3-125">多重プロセッサ システムを使用している場合は、プロセッサの追加も可能です。</span><span class="sxs-lookup"><span data-stu-id="a76d3-125">Or, if you have a multiprocessor system, you could add a processor.</span></span>  
  
 <span data-ttu-id="a76d3-126">プロセッサ使用率を調べる場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで実行されている作業の種類を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="a76d3-126">When you examine processor usage, consider the type of work that the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs.</span></span> <span data-ttu-id="a76d3-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が集計に関するクエリや、ディスク I/O を必要としないメモリ バインド クエリなどの多数の計算を実行している場合は、100% のプロセッサ時間が使用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a76d3-127">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs many calculations, such as queries involving aggregates or memory-bound queries that require no disk I/O, 100 percent of the processor's time can be used.</span></span> <span data-ttu-id="a76d3-128">これによって他のアプリケーションのパフォーマンスが低下する場合は、ワークロードを変更してみてください。</span><span class="sxs-lookup"><span data-stu-id="a76d3-128">If this causes the performance of other applications to suffer, try changing the workload.</span></span> <span data-ttu-id="a76d3-129">たとえば、そのコンピューターを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの実行専用にします。</span><span class="sxs-lookup"><span data-stu-id="a76d3-129">For example, dedicate the computer to running the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a76d3-130">多数のクライアント要求が処理されている場合に、使用率が 100% 前後の値を示しているとき、プロセスが待ち行列内でプロセッサ時間を待っているために、ボトルネックが生じていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="a76d3-130">Usage rates around 100 percent, where many client requests are being processed, may indicate that processes are queuing up, waiting for processor time, and causing a bottleneck.</span></span> <span data-ttu-id="a76d3-131">この問題を解決するには、より高速なプロセッサを追加します。</span><span class="sxs-lookup"><span data-stu-id="a76d3-131">Resolve the problem by adding faster processors.</span></span>  
  
  
