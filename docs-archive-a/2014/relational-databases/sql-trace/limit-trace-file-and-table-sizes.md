---
title: トレース ファイルとテーブル サイズの制限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- traces [SQL Server], file size
- size [SQL Server], tables
- file rollover option [SQL Server]
- size [SQL Server], files
ms.assetid: 88c31b02-f44c-4a14-be8b-437f2097de12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7795dfdadb8fb3bbaa1b55dcd5c962d24a7ba29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642724"
---
# <a name="limit-trace-file-and-table-sizes"></a><span data-ttu-id="424ae-102">トレース ファイルとテーブル サイズの制限</span><span class="sxs-lookup"><span data-stu-id="424ae-102">Limit Trace File and Table Sizes</span></span>
  <span data-ttu-id="424ae-103">SQL トレースの結果のサイズは、トレースに含まれているイベント クラスと [!INCLUDE[ssDE](../../includes/ssde-md.md)] の使用方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="424ae-103">SQL Trace results vary in size depending on the event classes that are included in the trace and the way in which the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is used.</span></span> <span data-ttu-id="424ae-104">頻繁に発生するイベント クラスをトレースする場合、最大ファイル サイズまたは最大行数を設定することにより、トレースで収集されるデータの量を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="424ae-104">If you trace event classes that occur frequently, you can minimize the amount of data that the trace collects by setting the maximum file size or the maximum number of rows.</span></span> <span data-ttu-id="424ae-105">最大ファイル サイズまたは最大行数を指定することにより、トレース ファイルまたはテーブルが指定された上限を超えて大きくならないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="424ae-105">By specifying the maximum file size or rows, you ensure that the trace file or table will not grow beyond the specified limit.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="424ae-106">既存のファイルにトレース データを保存する場合、そのファイルにデータを追加するか、またはそのファイルを上書きできます。</span><span class="sxs-lookup"><span data-stu-id="424ae-106">If you save trace data to a file that already exists, you can append data to the file or overwrite the file.</span></span> <span data-ttu-id="424ae-107">ファイルにデータを追加する場合、トレース ファイルが既に指定した最大ファイル サイズに達しているか、または最大ファイル サイズを超えているときは、最大ファイル サイズを増やすか、または新しいファイルを指定するよう通知されます。</span><span class="sxs-lookup"><span data-stu-id="424ae-107">If you choose to append data to the file, and the trace file already meets or exceeds the specified maximum file size, you are notified and given the opportunity either to increase the maximum file size or specify a new file.</span></span> <span data-ttu-id="424ae-108">トレース テーブルについても同じです。</span><span class="sxs-lookup"><span data-stu-id="424ae-108">The same is true for trace tables.</span></span>  
  
## <a name="maximum-file-size"></a><span data-ttu-id="424ae-109">最大ファイル サイズ</span><span class="sxs-lookup"><span data-stu-id="424ae-109">Maximum File Size</span></span>  
 <span data-ttu-id="424ae-110">最大ファイル サイズが指定されたトレースでは、その最大ファイル サイズに達すると、ファイルへのトレース情報の保存が停止されます。</span><span class="sxs-lookup"><span data-stu-id="424ae-110">A trace that has a maximum file size stops saving trace information to the file after the maximum file size has been reached.</span></span> <span data-ttu-id="424ae-111">このオプションを使用すると、イベントをより小さく管理しやすいファイルにグループ化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="424ae-111">This option allows you to group events into smaller, more manageable files.</span></span> <span data-ttu-id="424ae-112">また、ファイル サイズを制限すると、自動トレースをより安全に実行できるようになります。これは、最大ファイル サイズに達するとトレースが停止するためです。</span><span class="sxs-lookup"><span data-stu-id="424ae-112">In addition, limiting file size makes it safer to run unattended traces, because the trace stops when the maximum file size is reached.</span></span> <span data-ttu-id="424ae-113">最大ファイル サイズは、Transact-SQL ストアド プロシージャまたは [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して作成されたトレースに対して設定できます。</span><span class="sxs-lookup"><span data-stu-id="424ae-113">You can set the maximum file size for traces created by means of Transact-SQL stored procedures or by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="424ae-114">最大ファイル サイズ オプションの上限は 1 GB です。</span><span class="sxs-lookup"><span data-stu-id="424ae-114">There is an upper limit of 1 gigabyte (GB) for the maximum file size option.</span></span> <span data-ttu-id="424ae-115">既定の最大ファイル サイズは 5 MB です。</span><span class="sxs-lookup"><span data-stu-id="424ae-115">The default maximum file size is 5 megabytes (MB).</span></span>  
  
### <a name="enabling-file-rollover"></a><span data-ttu-id="424ae-116">ファイルのロールオーバーの有効化</span><span class="sxs-lookup"><span data-stu-id="424ae-116">Enabling File Rollover</span></span>  
 <span data-ttu-id="424ae-117">ファイルのロールオーバー オプションを使用すると、最大ファイル サイズに達したときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって現在のファイルが閉じられ、新しいファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="424ae-117">The file rollover option causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to close the current file and create a new file when the maximum file size is reached.</span></span> <span data-ttu-id="424ae-118">新しいファイルの名前は以前のファイルと同じになりますが、その順番を示すために名前に整数が追加されます。</span><span class="sxs-lookup"><span data-stu-id="424ae-118">The new file has the same name as the previous file, but an integer is appended to the name to indicate its sequence.</span></span> <span data-ttu-id="424ae-119">たとえば、元のトレース ファイルの名前が filename_1.trc である場合、次のトレース ファイルの名前は filename_2.trc になります。</span><span class="sxs-lookup"><span data-stu-id="424ae-119">For example, if the original trace file is named filename_1.trc, the next trace file is filename_2.trc, and so on.</span></span> <span data-ttu-id="424ae-120">新しいロールオーバー ファイルに割り当てられた名前が既存のファイルで既に使用されている場合、その既存のファイルは、読み取り専用でない限り上書きされます。</span><span class="sxs-lookup"><span data-stu-id="424ae-120">If the name assigned to a new rollover file is already used by an existing file, the existing file is overwritten unless it is read only.</span></span> <span data-ttu-id="424ae-121">トレース データをファイルに保存する場合、ファイルのロールオーバー オプションが既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="424ae-121">The file rollover option is enabled by default when you are saving trace data to a file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="424ae-122">ファイルのロールオーバー オプションを有効にすると、トレースは他の方法によって停止されるまで続行されます。</span><span class="sxs-lookup"><span data-stu-id="424ae-122">With the file rollover option on, the trace continues until it is stopped by some other means.</span></span> <span data-ttu-id="424ae-123">ファイル サイズの制限に達した後でトレースを停止するには、ファイルのロールオーバー オプションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="424ae-123">To stop the trace after you have reached the file size limit, disable the file rollover option.</span></span>  
  
 <span data-ttu-id="424ae-124">**トレース ファイルの最大ファイル サイズを設定するには**</span><span class="sxs-lookup"><span data-stu-id="424ae-124">**To set a maximum file size for a trace file**</span></span>  
  
 [<span data-ttu-id="424ae-125">トレース ファイルの最大ファイル サイズの設定 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="424ae-125">Set a Maximum File Size for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
## <a name="maximum-number-of-rows"></a><span data-ttu-id="424ae-126">最大行数</span><span class="sxs-lookup"><span data-stu-id="424ae-126">Maximum Number of Rows</span></span>  
 <span data-ttu-id="424ae-127">最大行数が指定されたトレースでは、その最大行数に達すると、テーブルへのトレース情報の保存が停止されます。</span><span class="sxs-lookup"><span data-stu-id="424ae-127">A trace with a maximum number of rows stops saving trace information to a table after the maximum number of rows has been reached.</span></span> <span data-ttu-id="424ae-128">1 つのイベントによって 1 つの行が構成されるため、このパラメーターでは、収集されるイベント数の制限が設定されます。</span><span class="sxs-lookup"><span data-stu-id="424ae-128">Each event constitutes one row, so this parameter sets a limit on the number of events that are gathered.</span></span> <span data-ttu-id="424ae-129">最大行数を設定すると、自動トレースを実行しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="424ae-129">Setting the maximum number of rows makes it easier to run unattended traces.</span></span> <span data-ttu-id="424ae-130">たとえば、トレース データをテーブルに保存するトレースを開始する必要があるが、ファイルが大きくなりすぎたらトレースを停止する場合、その操作を自動トレースで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="424ae-130">For example, if you need to start a trace that saves trace data to a table, but you want to stop the trace if the table becomes too large, you can do so automatically.</span></span>  
  
 <span data-ttu-id="424ae-131">最大行数を指定し、その最大行数に達した場合、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] が実行されている限りトレースは続行されますが、トレース情報はそれ以上記録されません。</span><span class="sxs-lookup"><span data-stu-id="424ae-131">When the maximum number of rows is specified and the maximum number of rows has been reached, the trace continues to run while [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is running, but the trace information is no longer recorded.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="424ae-132">トレースが停止されるまで、トレース結果の表示が続行されます。</span><span class="sxs-lookup"><span data-stu-id="424ae-132">continues to display the trace results until the trace stops.</span></span>  
  
 <span data-ttu-id="424ae-133">**トレースの最大行数を設定するには**</span><span class="sxs-lookup"><span data-stu-id="424ae-133">**To set a maximum number of rows for a trace**</span></span>  
  
 [<span data-ttu-id="424ae-134">トレース テーブルの最大テーブル サイズの設定 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="424ae-134">Set a Maximum Table Size for a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
## <a name="see-also"></a><span data-ttu-id="424ae-135">参照</span><span class="sxs-lookup"><span data-stu-id="424ae-135">See Also</span></span>  
 [<span data-ttu-id="424ae-136">sp_trace_create &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="424ae-136">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)  
  
  
