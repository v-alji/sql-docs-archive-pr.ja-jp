---
title: メモリ不足の問題の解決 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5f57725d559b0cd62679550e2bb7c04dbd7e2bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639518"
---
# <a name="resolve-out-of-memory-issues"></a><span data-ttu-id="6336e-102">メモリ不足の問題の解決</span><span class="sxs-lookup"><span data-stu-id="6336e-102">Resolve Out Of Memory Issues</span></span>
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="6336e-103">では、さまざまな形で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]より多くのメモリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="6336e-103">uses more memory and in different ways than does [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6336e-104">インストールして [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 用に割り当てたメモリ量が、ニーズの拡大に合わなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6336e-104">It is possible that the amount of memory you installed and allocated for [!INCLUDE[hek_2](../../includes/hek-2-md.md)] becomes inadequate for your growing needs.</span></span> <span data-ttu-id="6336e-105">その場合は、メモリが不足する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6336e-105">If so, you could run out of memory.</span></span> <span data-ttu-id="6336e-106">このトピックでは、OOM 状態から回復する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6336e-106">This topic covers how to recover from an OOM situation.</span></span> <span data-ttu-id="6336e-107">多数の OOM 状態を回避するのに役立つガイドについては、「 [メモリ使用量の監視とトラブルシューティング](monitor-and-troubleshoot-memory-usage.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-107">See [Monitor and Troubleshoot Memory Usage](monitor-and-troubleshoot-memory-usage.md) for guidance that can help you avoid many OOM situations.</span></span>  
  
## <a name="covered-in-this-topic"></a><span data-ttu-id="6336e-108">このトピックの内容</span><span class="sxs-lookup"><span data-stu-id="6336e-108">Covered in this topic</span></span>  
  
|<span data-ttu-id="6336e-109">トピック</span><span class="sxs-lookup"><span data-stu-id="6336e-109">Topic</span></span>|<span data-ttu-id="6336e-110">概要</span><span class="sxs-lookup"><span data-stu-id="6336e-110">Overview</span></span>|  
|-----------|--------------|  
| [<span data-ttu-id="6336e-111">OOM によるデータベース復元の障害を解決する</span><span class="sxs-lookup"><span data-stu-id="6336e-111">Resolve database restore failures due to OOM</span></span>](#resolve-database-restore-failures-due-to-oom) |<span data-ttu-id="6336e-112">"リソース プール ' *\<resourcePoolName>* ' 内のメモリ不足が原因で、データベース ' *\<databaseName>* ' の復元操作に失敗しました。" というエラー メッセージが表示された場合の対処方法。</span><span class="sxs-lookup"><span data-stu-id="6336e-112">What to do if you get the error message, "Restore operation failed for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'."</span></span>|  
| [<span data-ttu-id="6336e-113">低メモリまたは OOM 状態によるワークロードへの影響を解決する</span><span class="sxs-lookup"><span data-stu-id="6336e-113">Resolve impact of low memory or OOM conditions on the workload</span></span>](#resolve-impact-of-low-memory-or-oom-conditions-on-the-workload)|<span data-ttu-id="6336e-114">低メモリの問題によるパフォーマンス低下が見つかった場合の対処方法。</span><span class="sxs-lookup"><span data-stu-id="6336e-114">What to do if you find low memory issues are negatively impacting performance.</span></span>|  
| [<span data-ttu-id="6336e-115">十分なメモリがある状況でのメモリ不足によるページの割り当てエラーを解決する</span><span class="sxs-lookup"><span data-stu-id="6336e-115">Resolve page allocation failures due to insufficient memory when sufficient memory is available</span></span>](#resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available) |<span data-ttu-id="6336e-116">操作に十分なメモリがあるにもかかわらず、"リソース プール ' *\<resourcePoolName>* ' のメモリが不足しているため、データベース ' *\<databaseName>* ' のページ割り当ては禁止されています。</span><span class="sxs-lookup"><span data-stu-id="6336e-116">What to do if you get the error message, "Disallowing page allocations for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'.</span></span> <span data-ttu-id="6336e-117">..." というエラー メッセージが発生した場合の対処方法。</span><span class="sxs-lookup"><span data-stu-id="6336e-117">..." when available memory is sufficient for the operation.</span></span>|  
  
## <a name="resolve-database-restore-failures-due-to-oom"></a><span data-ttu-id="6336e-118">OOM によるデータベース復元の障害を解決する</span><span class="sxs-lookup"><span data-stu-id="6336e-118">Resolve database restore failures due to OOM</span></span>  
 <span data-ttu-id="6336e-119">データベースを復元しようとすると、" *\<databaseName>* リソースプール ' ' のメモリが不足しているため、データベース ' ' の復元操作に失敗しました。" というエラーメッセージが表示されることがあり *\<resourcePoolName>* ます。データベースを正常に復元するには、使用可能なメモリを増やして、メモリ不足の問題を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6336e-119">When you attempt to restore a database you may get the error message: "Restore operation failed for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'." Before you can successfully restore the database you must resolve the insufficient memory issue by making more memory available.</span></span>  
  
 <span data-ttu-id="6336e-120">OOM による復旧エラーを解決するには、次の方法のいずれかまたはすべてを使用して、復旧操作で使用できるメモリを一時的に増やします。</span><span class="sxs-lookup"><span data-stu-id="6336e-120">To resolve recovery failure due to OOM increase available memory using any or al of these means to temporarily increase memory available for the recovery operation.</span></span>  
  
-   <span data-ttu-id="6336e-121">実行中のアプリケーションを一時的に閉じます。</span><span class="sxs-lookup"><span data-stu-id="6336e-121">Temporarily close running applications.</span></span>   
    <span data-ttu-id="6336e-122">Visual Studio、Internet Explorer、OneNote など、実行中のアプリケーションを 1 つ以上閉じることにより、これらのアプリケーションによって使用されていたメモリを復元操作で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6336e-122">By closing one or more running applications, such as Visual Studio, Internet Explorer, OneNote, and others, you make the memory they were using available for the restore operation.</span></span> <span data-ttu-id="6336e-123">閉じたアプリケーションは、復元操作の正常完了後に再起動できます。</span><span class="sxs-lookup"><span data-stu-id="6336e-123">You can restart them following the successful restore.</span></span>  
  
-   <span data-ttu-id="6336e-124">MAX_MEMORY_PERCENT の値を増やします。</span><span class="sxs-lookup"><span data-stu-id="6336e-124">Increase the value of MAX_MEMORY_PERCENT.</span></span>   
    <span data-ttu-id="6336e-125">このコード スニペットでは、リソース プール PoolHk の MAX_MEMORY_PERCENT を変更して、インストールされているメモリの 70% に設定します。</span><span class="sxs-lookup"><span data-stu-id="6336e-125">This code snippet changes MAX_MEMORY_PERCENT for the resource pool PoolHk to 70% of installed memory.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6336e-126">サーバーが VM 上で実行されており、専用用途ではない場合は、MIN_MEMORY_PERCENT を MAX_MEMORY_PERCENT と同じ値に設定してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-126">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT to the same value as MAX_MEMORY_PERCENT.</span></span>   
    > <span data-ttu-id="6336e-127">詳細については、「[ベストプラクティス: VM 環境でのインメモリ OLTP の使用](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-127">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
    ```sql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     <span data-ttu-id="6336e-128">MAX_MEMORY_PERCENT の最大値については、「[メモリ最適化テーブルとインデックスで使用可能なメモリの割合](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-128">For information on maximum values for MAX_MEMORY_PERCENT see the topic section [Percent of memory available for memory-optimized tables and indexes](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)</span></span>
  
-   <span data-ttu-id="6336e-129">**max server memory** を再構成します。</span><span class="sxs-lookup"><span data-stu-id="6336e-129">Reconfigure **max server memory**.</span></span>  
    <span data-ttu-id="6336e-130">**max server memory** の構成については、「 [メモリ構成オプションを使用したサーバー パフォーマンスの最適化](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6336e-130">For information on configuring **max server memory** see the topic [Optimizing Server Performance Using Memory Configuration Options](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).</span></span>  
  
## <a name="resolve-impact-of-low-memory-or-oom-conditions-on-the-workload"></a><span data-ttu-id="6336e-131">低メモリまたは OOM 状態によるワークロードへの影響を解決する</span><span class="sxs-lookup"><span data-stu-id="6336e-131">Resolve impact of low memory or OOM conditions on the workload</span></span>  
 <span data-ttu-id="6336e-132">言うまでもなく、低メモリまたは OOM (メモリ不足) の状態にならないことがベストです。</span><span class="sxs-lookup"><span data-stu-id="6336e-132">Obviously, it is best to not get into a low memory or OOM (Out of Memory) situation.</span></span> <span data-ttu-id="6336e-133">適切なプラン作成と監視によって、OOM 状態を回避することができます。</span><span class="sxs-lookup"><span data-stu-id="6336e-133">Good planning and monitoring can help avoid OOM situations.</span></span> <span data-ttu-id="6336e-134">ただし、最適なプランを作成しても、実際に起こることを予測できるとは限らず、結果として低メモリまたは OOM の状態になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6336e-134">Still, the best planning does not always foresee what actually happens and you might end up with low memory or OOM.</span></span> <span data-ttu-id="6336e-135">OOM からの復旧には、次の 2 段階があります。</span><span class="sxs-lookup"><span data-stu-id="6336e-135">There are two steps to recovering from OOM:</span></span>  
  
1.  [<span data-ttu-id="6336e-136">DAC (専用管理者接続) を開く</span><span class="sxs-lookup"><span data-stu-id="6336e-136">Open a DAC (Dedicated Administrator Connection)</span></span>](#open-a-dac-dedicated-administrator-connection) 
  
2.  [<span data-ttu-id="6336e-137">修正措置を行う</span><span class="sxs-lookup"><span data-stu-id="6336e-137">Take corrective action</span></span>](#take-corrective-action) 
  
### <a name="open-a-dac-dedicated-administrator-connection"></a><span data-ttu-id="6336e-138">DAC (専用管理者接続) を開く</span><span class="sxs-lookup"><span data-stu-id="6336e-138">Open a DAC (Dedicated Administrator Connection)</span></span>  
 <span data-ttu-id="6336e-139">Microsoft SQL Server は、専用管理者接続 (DAC) を提供します。</span><span class="sxs-lookup"><span data-stu-id="6336e-139">Microsoft SQL Server provides a dedicated administrator connection (DAC).</span></span> <span data-ttu-id="6336e-140">DAC を使用すると、サーバーが他のクライアント接続に応答しない場合でも、SQL Server データベース エンジンの実行中のインスタンスにアクセスして、サーバーの問題をトラブルシューティングすることができます。</span><span class="sxs-lookup"><span data-stu-id="6336e-140">The DAC allows an administrator to access a running instance of SQL Server Database Engine to troubleshoot problems on the server-even when the server is unresponsive to other client connections.</span></span> <span data-ttu-id="6336e-141">DAC は、 `sqlcmd` ユーティリティおよび SQL Server Management Studio (SSMS) を介して利用できます。</span><span class="sxs-lookup"><span data-stu-id="6336e-141">The DAC is available through the `sqlcmd` utility and SQL Server Management Studio (SSMS).</span></span>  
  
 <span data-ttu-id="6336e-142">`sqlcmd` および DAC の使用方法については、「 [専用管理者接続の使用](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6336e-142">For guidance on using `sqlcmd` and DAC see [Using a Dedicated Administrator Connection](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span> <span data-ttu-id="6336e-143">SSMS を介して DAC を使用する方法については、「 [SQL Server Management Studio で専用管理者接続を使用する方法](https://msdn.microsoft.com/library/ms178068.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6336e-143">For guidance on using DAC through SSMS see [How to: Use the Dedicated Administrator Connection with SQL Server Management Studio](https://msdn.microsoft.com/library/ms178068.aspx).</span></span>  
  
### <a name="take-corrective-action"></a><span data-ttu-id="6336e-144">修正措置を行う</span><span class="sxs-lookup"><span data-stu-id="6336e-144">Take corrective action</span></span>  
 <span data-ttu-id="6336e-145">OOM 状態を解決するには、使用率を削減して既存メモリを解放するか、インメモリ テーブルに使用できるメモリ量を増やす必要があります。</span><span class="sxs-lookup"><span data-stu-id="6336e-145">To resolve your OOM condition you need to either free up existing memory by reducing usage, or make more memory available to your in-memory tables.</span></span>  
  
#### <a name="free-up-existing-memory"></a><span data-ttu-id="6336e-146">既存メモリを解放する</span><span class="sxs-lookup"><span data-stu-id="6336e-146">Free up existing memory</span></span>  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a><span data-ttu-id="6336e-147">メモリ最適化テーブルの不要な行を削除し、ガベージ コレクションを待機する</span><span class="sxs-lookup"><span data-stu-id="6336e-147">Delete non-essential memory optimized table rows and wait for garbage collection</span></span>  
 <span data-ttu-id="6336e-148">メモリ最適化テーブルから、不要な行を削除できます。</span><span class="sxs-lookup"><span data-stu-id="6336e-148">You can remove non-essential rows from a memory optimized table.</span></span> <span data-ttu-id="6336e-149">ガベージ コレクターによって、これらの行で使用されていたメモリが使用可能メモリに返されます。</span><span class="sxs-lookup"><span data-stu-id="6336e-149">The garbage collector returns the memory used by these rows to available memory.</span></span> <span data-ttu-id="6336e-150">.</span><span class="sxs-lookup"><span data-stu-id="6336e-150">.</span></span> <span data-ttu-id="6336e-151">インメモリ OLTP エンジンは、ガベージ行を積極的に回収します。</span><span class="sxs-lookup"><span data-stu-id="6336e-151">In-memory OLTP engine collects garbage rows aggressively.</span></span> <span data-ttu-id="6336e-152">ただし、実行時間が長いトランザクションではガベージ コレクションが行われないことがあります。</span><span class="sxs-lookup"><span data-stu-id="6336e-152">However, a long running transaction can prevent garbage collection.</span></span> <span data-ttu-id="6336e-153">たとえば、5 分間実行されているトランザクションの場合、トランザクションがアクティブな状態で更新操作または削除操作によって作成された行バージョンは、ガベージ コレクションで回収することができません。</span><span class="sxs-lookup"><span data-stu-id="6336e-153">For example, if you have a transaction that runs for 5 minutes, any row versions created due to update/delete operations while the transaction was active can't be garbage collected.</span></span>  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a><span data-ttu-id="6336e-154">1 つ以上の行をディスク ベース テーブルに移動する</span><span class="sxs-lookup"><span data-stu-id="6336e-154">Move one or more rows to a disk-based table</span></span>  
 <span data-ttu-id="6336e-155">TechNet の次の資料では、メモリ最適化テーブルからディスク ベース テーブルに行を移動する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="6336e-155">The following TechNet articles provide guidance on moving rows from a memory-optimized table to a disk-based table.</span></span>  
  
-   <span data-ttu-id="6336e-156">[アプリケーション レベルのパーティション分割](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="6336e-156">[Application-Level Partitioning](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)</span></span>  
  
-   <span data-ttu-id="6336e-157">[メモリ最適化テーブルのパーティション分割に関するアプリケーションのパターン](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="6336e-157">[Application Pattern for Partitioning Memory-Optimized Tables](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)</span></span>  
  
#### <a name="increase-available-memory"></a><span data-ttu-id="6336e-158">使用可能なメモリを増やす</span><span class="sxs-lookup"><span data-stu-id="6336e-158">Increase available memory</span></span>  
  
##### <a name="increase-value-of-max_memory_percent-on-the-resource-pool"></a><span data-ttu-id="6336e-159">リソース プールの MAX_MEMORY_PERCENT 値を増やす</span><span class="sxs-lookup"><span data-stu-id="6336e-159">Increase value of MAX_MEMORY_PERCENT on the resource pool</span></span>  
 <span data-ttu-id="6336e-160">インメモリ テーブル用に名前付きリソース プールを作成していない場合は、作成して [!INCLUDE[hek_2](../../includes/hek-2-md.md)] データベースをバインドします。</span><span class="sxs-lookup"><span data-stu-id="6336e-160">If you have not created a named resource pool for your in-memory tables you should do that and bind your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] databases to it.</span></span> <span data-ttu-id="6336e-161">[データベースを作成してリソース プールにバインドする方法については、「](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) メモリ最適化テーブルを持つデータベースのリソース プールへのバインド [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-161">See the topic [Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) for guidance on creating and binding your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] databases to a resource pool.</span></span>  
  
 <span data-ttu-id="6336e-162">[!INCLUDE[hek_2](../../includes/hek-2-md.md)] データベースがリソース プールにバインドされている場合は、プールがアクセスできるメモリのパーセントを増やせることがあります。</span><span class="sxs-lookup"><span data-stu-id="6336e-162">If your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] database is bound to a resource pool you may be able to increase the percent of memory the pool can access.</span></span> <span data-ttu-id="6336e-163">リソース プールの MIN_MEMORY_PERCENT および MAX_MEMORY_PERCENT の値を変更する方法については、サブトピック「 [既存のプール内での MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT の変更](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6336e-163">See the sub-topic [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) for guidance on changing the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT for a resource pool.</span></span>  
  
 <span data-ttu-id="6336e-164">MAX_MEMORY_PERCENT の値を増やします。</span><span class="sxs-lookup"><span data-stu-id="6336e-164">Increase the value of MAX_MEMORY_PERCENT.</span></span>   
<span data-ttu-id="6336e-165">このコード スニペットでは、リソース プール PoolHk の MAX_MEMORY_PERCENT を変更して、インストールされているメモリの 70% に設定します。</span><span class="sxs-lookup"><span data-stu-id="6336e-165">This code snippet changes MAX_MEMORY_PERCENT for the resource pool PoolHk to 70% of installed memory.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6336e-166">サーバーが VM 上で実行されており、専用用途ではない場合は、MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT を同じ値に設定してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-166">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value.</span></span>   
> <span data-ttu-id="6336e-167">詳細については、「[ベストプラクティス: VM 環境でのインメモリ OLTP の使用](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-167">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
```sql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="6336e-168">MAX_MEMORY_PERCENT の最大値については、「 [メモリ最適化テーブルおよびインデックスで使用可能なメモリの割合](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6336e-168">For information on maximum values for MAX_MEMORY_PERCENT see the topic section [Percent of memory available for memory-optimized tables and indexes](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes).</span></span>  
  
##### <a name="install-additional-memory"></a><span data-ttu-id="6336e-169">追加メモリをインストールする</span><span class="sxs-lookup"><span data-stu-id="6336e-169">Install additional memory</span></span>  
 <span data-ttu-id="6336e-170">可能であれば、最終的に最上のソリューションは、追加の物理メモリをインストールすることです。</span><span class="sxs-lookup"><span data-stu-id="6336e-170">Ultimately the best solution, if possible, is to install additional physical memory.</span></span> <span data-ttu-id="6336e-171">その場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でそれ以上のメモリが必要である可能性は低いため、新しくインストールされたメモリのすべてがリソース プールで使用可能でない場合はそれを活用して、MAX_MEMORY_PERCENT 値 (サブトピック「[既存のプール内での MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT の変更](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)」を参照) も増やせる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6336e-171">If you do this, remember that you will probably be able to also increase the value of MAX_MEMORY_PERCENT (see the sub-topic [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)) since [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] won't likely need more memory, allowing you to make most if not all of the newly installed memory available to the resource pool.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6336e-172">サーバーが VM 上で実行されており、専用用途ではない場合は、MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT を同じ値に設定してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-172">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value.</span></span>   
> <span data-ttu-id="6336e-173">詳細については、「[ベストプラクティス: VM 環境でのインメモリ OLTP の使用](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-173">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
## <a name="resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available"></a><span data-ttu-id="6336e-174">十分なメモリがある状況でのメモリ不足によるページの割り当てエラーを解決する</span><span class="sxs-lookup"><span data-stu-id="6336e-174">Resolve page allocation failures due to insufficient memory when sufficient memory is available</span></span>  
 <span data-ttu-id="6336e-175">"リソースプール ' ' のメモリが不足しているため、データベース ' ' のページ割り当てを禁止して *\<databaseName>* います。" というエラーメッセージが表示された場合 *\<resourcePoolName>* 。</span><span class="sxs-lookup"><span data-stu-id="6336e-175">If you get the error message, "Disallowing page allocations for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'.</span></span> <span data-ttu-id="6336e-176"><https://go.microsoft.com/fwlink/?LinkId=330673>詳細については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6336e-176">See '<https://go.microsoft.com/fwlink/?LinkId=330673>' for more information."</span></span> <span data-ttu-id="6336e-177">エラー ログに記録される場合は、原因として、リソース ガバナーが無効になっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6336e-177">in the error log when the available physical memory is sufficient to allocate the page, it may be due to a disabled Resource Governor.</span></span> <span data-ttu-id="6336e-178">リソース ガバナーが無効になっていると、MEMORYBROKER_FOR_RESERVE によって擬似的なメモリ不足が引き起こされます。</span><span class="sxs-lookup"><span data-stu-id="6336e-178">When the Resource Governor is disabled MEMORYBROKER_FOR_RESERVE induces artificial memory pressure.</span></span>  
  
 <span data-ttu-id="6336e-179">これを解決するには、リソース ガバナーを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6336e-179">To resolve this you need to enable the Resource Governor.</span></span>  
  
 <span data-ttu-id="6336e-180">オブジェクト エクスプローラー、リソース ガバナーのプロパティ、または Transact-SQL を使用してリソース ガバナーを有効にする方法や、制限事項と制約事項については、「 [リソース ガバナーの有効化](https://technet.microsoft.com/library/bb895149.aspx) 」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6336e-180">See [Enable Resource Governor](https://technet.microsoft.com/library/bb895149.aspx) for information on Limits and Restrictions as well as guidance on enabling Resource Governor using Object Explorer, Resource Governor properties, or Transact-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6336e-181">参照</span><span class="sxs-lookup"><span data-stu-id="6336e-181">See Also</span></span>  
 <span data-ttu-id="6336e-182">[インメモリ OLTP のメモリ管理](../../database-engine/managing-memory-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="6336e-182">[Managing Memory for In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="6336e-183">[メモリ使用量の監視とトラブルシューティング](monitor-and-troubleshoot-memory-usage.md) </span><span class="sxs-lookup"><span data-stu-id="6336e-183">[Monitor and Troubleshoot Memory Usage](monitor-and-troubleshoot-memory-usage.md) </span></span>  
 <span data-ttu-id="6336e-184">[データベースを作成してリソース プールにバインドする方法については、「](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="6336e-184">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span></span>  
 [<span data-ttu-id="6336e-185">ベストプラクティス: VM 環境でのインメモリ OLTP の使用</span><span class="sxs-lookup"><span data-stu-id="6336e-185">Best Practices: Using In-Memory OLTP in a VM environment</span></span>](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)  
  
  
