---
title: トランザクションの持続性の制御 | Microsoft Docs
ms.custom: ''
ms.date: 05/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- delayed durability
- Lazy Commit
ms.assetid: 3ac93b28-cac7-483e-a8ab-ac44e1cc1c76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f37bcaf8719f4a2f3b1e7fbca1cf332717bd936e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639508"
---
# <a name="control-transaction-durability"></a><span data-ttu-id="7d1bc-102">トランザクションの持続性の制御</span><span class="sxs-lookup"><span data-stu-id="7d1bc-102">Control Transaction Durability</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7d1bc-103">におけるトランザクションのコミットには、完全持続性、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定値、または遅延持続性 (低速コミットとも呼ばれます) が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-103">transaction commits can be either fully durable, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] default, or delayed durable (also known as lazy commit).</span></span>  
  
 <span data-ttu-id="7d1bc-104">完全持続性トランザクションのコミットは同期的であり、トランザクションのログ レコードがディスクに書き込まれてからコミットが正常完了として報告され、制御がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-104">Fully durable transaction commits are synchronous and report a commit as successful and return control to the client only after the log records for the transaction are written to disk.</span></span> <span data-ttu-id="7d1bc-105">遅延持続性トランザクションのコミットは非同期的であり、トランザクションのログ レコードがディスクに書き込まれる前にコミットが正常完了として報告されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-105">Delayed durable transaction commits are asynchronous and report a commit as successful before the log records for the transaction are written to disk.</span></span> <span data-ttu-id="7d1bc-106">トランザクションを持続可能にするためには、トランザクション ログ エントリをディスクに書き込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-106">Writing the transaction log entries to disk is required for a transaction to be durable.</span></span> <span data-ttu-id="7d1bc-107">遅延持続性トランザクションは、トランザクション ログ エントリがディスクにフラッシュされる時点で持続的になります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-107">Delayed durable transactions become durable when the transaction log entries are flushed to disk.</span></span>  
  
 <span data-ttu-id="7d1bc-108">このトピックでは、遅延持続性トランザクションについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-108">This topic details delayed durable transactions.</span></span>  
  
## <a name="full-vs-delayed-transaction-durability"></a><span data-ttu-id="7d1bc-109">トランザクションの完全持続性と遅延持続性</span><span class="sxs-lookup"><span data-stu-id="7d1bc-109">Full vs. Delayed Transaction Durability</span></span>  
 <span data-ttu-id="7d1bc-110">トランザクションの完全持続性と遅延持続性にはそれぞれ、長所と短所があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-110">Both full and delayed transaction durability have their advantages and disadvantages.</span></span> <span data-ttu-id="7d1bc-111">アプリケーションには、完全持続性トランザクションと遅延持続性トランザクションを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-111">An application can have a mix of fully and delayed durable transactions.</span></span> <span data-ttu-id="7d1bc-112">ビジネス ニーズを慎重に考慮したうえで、それぞれのタイプのトランザクションの適合性を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-112">You should carefully consider your business needs and how each fits into those needs.</span></span>  
  
### <a name="full-transaction-durability"></a><span data-ttu-id="7d1bc-113">トランザクションの完全持続性</span><span class="sxs-lookup"><span data-stu-id="7d1bc-113">Full transaction durability</span></span>  
 <span data-ttu-id="7d1bc-114">完全持続性トランザクションは、クライアントに制御を返す前に、トランザクション ログをディスクに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-114">Fully durable transactions write the transaction log to disk before returning control to the client.</span></span> <span data-ttu-id="7d1bc-115">次のような場合には、完全持続性トランザクションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-115">You should use fully durable transactions whenever:</span></span>  
  
-   <span data-ttu-id="7d1bc-116">システムで、データの損失が許容されない場合。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-116">Your system cannot tolerate any data loss.</span></span>   
    <span data-ttu-id="7d1bc-117">データの一部が失われるケースについては、「 [データが失われるケース](#when-can-i-lose-data) 」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-117">See the section [When can I lose data?](#when-can-i-lose-data) for information on when you can lose some of your data.</span></span>  
  
-   <span data-ttu-id="7d1bc-118">ボトルネックの原因がトランザクション ログの書き込み待機時間ではない場合。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-118">The bottleneck is not due to transaction log write latency.</span></span>  
  
 <span data-ttu-id="7d1bc-119">遅延持続性トランザクションは、トランザクション ログ レコードをメモリに保持してバッチ単位でトランザクション ログ レコードに書き込み、必要な I/O 操作を減らすことによって、ログの I/O による待機時間を短縮します。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-119">Delayed transaction durability reduces the latency due to log I/O by keeping the transaction log records in memory and writing to the transaction log in batches, thus requiring fewer I/O operations.</span></span> <span data-ttu-id="7d1bc-120">遅延持続性トランザクションでは、ログ I/O の競合が減少し、システム内の待機時間を短縮できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-120">Delayed transaction durability potentially reduces log I/O contention, thus reducing waits in the system.</span></span>  
  
 <span data-ttu-id="7d1bc-121">**トランザクションの完全持続性での保証**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-121">**Full Transaction Durability Guarantees**</span></span>  
  
-   <span data-ttu-id="7d1bc-122">トランザクションのコミットが成功した場合、トランザクションによる変更は、システム内の他のトランザクションから認識できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-122">Once transaction commit succeeds, the changes made by the transaction are visible to the other transactions in the system.</span></span> <span data-ttu-id="7d1bc-123">詳細については、「[トランザクション分離レベル](../../database-engine/transaction-isolation-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-123">See the topic [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) for more information.</span></span>  
  
-   <span data-ttu-id="7d1bc-124">持続性はコミット時に保証されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-124">Durability is guaranteed on commit.</span></span> <span data-ttu-id="7d1bc-125">対応するログ レコードがディスクに保存されてからトランザクションのコミットが成功となり、制御がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-125">Corresponding log records are persisted to disk before the transaction commit succeeds and returns control to the client.</span></span>  
  
### <a name="delayed-transaction-durability"></a><span data-ttu-id="7d1bc-126">トランザクションの遅延持続性</span><span class="sxs-lookup"><span data-stu-id="7d1bc-126">Delayed transaction durability</span></span>  
 <span data-ttu-id="7d1bc-127">トランザクションの遅延持続性は、ディスクへのログの非同期書き込みを使用して実現します。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-127">Delayed transaction durability is accomplished using asynchronous log writes to disk.</span></span> <span data-ttu-id="7d1bc-128">トランザクション ログ レコードはバッファーに保持され、バッファーがいっぱいになった場合またはバッファーのフラッシュ イベントが発生した場合に、ディスクに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-128">Transaction log records are kept in a buffer and written to disk when the buffer fills or a buffer flushing event takes place.</span></span> <span data-ttu-id="7d1bc-129">トランザクションの遅延持続性では、次の理由によってシステム内の待機時間と競合の両方が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-129">Delayed transaction durability reduces both latency and contention within the system because:</span></span>  
  
-   <span data-ttu-id="7d1bc-130">トランザクション コミット処理では、ログ IO の完了を待たずに制御がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-130">The transaction commit processing does not wait for log IO to finish and return control to the client.</span></span>  
  
-   <span data-ttu-id="7d1bc-131">同時実行トランザクション間でログ IO の競合が発生する可能性は高くありません。ログ バッファーは大きな単位でディスクにフラッシュできるため、競合が軽減され、スループットを向上できます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-131">Concurrent transactions are less likely to contend for log IO; instead, the log buffer can be flushed to disk in larger chunks, reducing contention, and increasing throughput.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7d1bc-132">ただしログ バッファーがフラッシュされる前にいっぱいになる場合など、コンカレンシーが高い場合は、ログ I/O の競合が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-132">You may still have log I/O contention if there is a high degree of concurrency, particularly if you fill up the log buffer faster than you flush it.</span></span>  
  
 <span data-ttu-id="7d1bc-133">**トランザクションの遅延持続性の利用が適したケース**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-133">**When to use delayed transaction durability**</span></span>  
  
 <span data-ttu-id="7d1bc-134">次のような場合は、トランザクションの遅延持続性の利用が適しています。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-134">Some of the cases in which you could benefit from using delayed transaction durability are:</span></span>  
  
 <span data-ttu-id="7d1bc-135">**ある程度のデータ損失を許容できる場合。** </span><span class="sxs-lookup"><span data-stu-id="7d1bc-135">**You can tolerate some data loss.**</span></span>  
 <span data-ttu-id="7d1bc-136">ある程度のデータ損失を許容できる場合 (データの大部分を確保できていれば個々のレコードがそれほど重要ではない場合など) は、遅延持続性の使用を検討することができます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-136">If you can tolerate some data loss, for example, where individual records are not critical as long as you have most of the data, then delayed durability may be worth considering.</span></span> <span data-ttu-id="7d1bc-137">一切のデータ損失を許容できない場合は、トランザクションの遅延持続性は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-137">If you cannot tolerate any data loss, do not use delayed transaction durability.</span></span>  
  
 <span data-ttu-id="7d1bc-138">**トランザクション ログの書き込みでボトルネックが発生している場合。** </span><span class="sxs-lookup"><span data-stu-id="7d1bc-138">**You are experiencing a bottleneck on transaction log writes.**</span></span>  
 <span data-ttu-id="7d1bc-139">パフォーマンスの問題がトランザクション ログの書き込みにおける待機時間によるものであれば、トランザクションの遅延持続性を使用することがアプリケーションにとってのメリットになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-139">If your performance issues are due to latency in transaction log writes, your application will likely benefit from using delayed transaction durability.</span></span>  
  
 <span data-ttu-id="7d1bc-140">**ワークロードの競合率が高い場合。** </span><span class="sxs-lookup"><span data-stu-id="7d1bc-140">**Your workloads have a high contention rate.**</span></span>  
 <span data-ttu-id="7d1bc-141">競合レベルの高いワークロードがシステムに存在する場合、ロックの解放待ちに多くの時間が消費されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-141">If your system has workloads with a high contention level much time is lost waiting for locks to be released.</span></span> <span data-ttu-id="7d1bc-142">トランザクションの遅延持続性を使用すると、コミット時間を短縮できるため、早くロックを解放でき、結果として高いスループットにつながります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-142">Delayed transaction durability reduces commit time and thus releases locks faster which results in higher throughput.</span></span>  
  
 <span data-ttu-id="7d1bc-143">**トランザクションの遅延持続性での保証**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-143">**Delayed Transaction Durability Guarantees**</span></span>  
  
-   <span data-ttu-id="7d1bc-144">トランザクションのコミットが成功した場合、トランザクションによる変更は、システム内の他のトランザクションから認識できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-144">Once transaction commit succeeds, the changes made by the transaction are visible to the other transactions in the system.</span></span>  
  
-   <span data-ttu-id="7d1bc-145">トランザクションの持続性が保証されるのは、インメモリ トランザクション ログがディスクにフラッシュされた後のみです。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-145">Transaction durability is guaranteed only following a flush of the in-memory transaction log to disk.</span></span> <span data-ttu-id="7d1bc-146">インメモリ トランザクション ログは、次の場合にディスクにフラッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-146">The in-memory transaction log is flushed to disk when:</span></span>  
  
    -   <span data-ttu-id="7d1bc-147">完全持続性トランザクションによって、同じデータベース内で変更が行われ、正常にコミットされた場合。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-147">A fully durable transaction in the same database makes a change in the database and successfully commits.</span></span>  
  
    -   <span data-ttu-id="7d1bc-148">ユーザーがシステム ストアド プロシージャ `sp_flush_log` を正常に実行した場合。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-148">The user executes the system stored procedure `sp_flush_log` successfully.</span></span>  
  
    -   <span data-ttu-id="7d1bc-149">インメモリ トランザクション ログ バッファーがいっぱいになり自動的にディスクにフラッシュされた場合。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-149">The in-memory transaction log buffer fills up and automatically flushes to disk.</span></span>  
  
     <span data-ttu-id="7d1bc-150">完全持続性トランザクションまたは sp_flush_log によって正常コミットされた場合、それより前にコミットされた遅延持続性トランザクションはすべて、持続可能な状態になっています。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-150">If a fully durable transaction or sp_flush_log successfully commit, all previously committed delayed durability transactions have been made durable.</span></span>  
  
 <span data-ttu-id="7d1bc-151">ログは定期的にディスクにフラッシュできます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-151">The log may be flushed to disk periodically.</span></span> <span data-ttu-id="7d1bc-152">ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では持続性トランザクションおよび sp_flush_log 以外に持続性は保証されません。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-152">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not provide any durability guarantees other than durable transactions and sp_flush_log.</span></span>  
  
## <a name="how-to-control-transaction-durability"></a><span data-ttu-id="7d1bc-153">トランザクションの持続性を制御する方法</span><span class="sxs-lookup"><span data-stu-id="7d1bc-153">How to control transaction durability</span></span>  
  
### <a name="database-level-control"></a><span data-ttu-id="7d1bc-154">データベース レベルの制御</span><span class="sxs-lookup"><span data-stu-id="7d1bc-154">Database level control</span></span>  
 <span data-ttu-id="7d1bc-155">DBA は次のステートメントを使用して、トランザクションの遅延持続性をデータベースに対してユーザーが使用できるかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-155">You, the DBA, can control whether users can use delayed transaction durability on a database with the following statement.</span></span> <span data-ttu-id="7d1bc-156">遅延持続性の設定は ALTER DATABASE で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-156">You must set the delayed durability setting with ALTER DATABASE.</span></span>  
  
```sql  
ALTER DATABASE ... SET DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
```  
  
 `DISABLED`  
 <span data-ttu-id="7d1bc-157">[既定値] この設定では、コミット レベルの設定 (DELAYED_DURABILITY=[ON | OFF]) に関係なく、データベースに対してコミットされたトランザクションにはすべて完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-157">[default] With this setting, all transactions that commit on the database are fully durable, regardless of the commit level setting (DELAYED_DURABILITY=[ON | OFF]).</span></span> <span data-ttu-id="7d1bc-158">ストアド プロシージャの変更および再コンパイルの必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-158">There is no need for stored procedure change and recompilation.</span></span> <span data-ttu-id="7d1bc-159">この設定により、遅延持続性によるリスクを負うことなく、すべてのデータを持続可能にできます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-159">This allows you to ensure that no data is ever put at risk by delayed durability.</span></span>  
  
 `ALLOWED`  
 <span data-ttu-id="7d1bc-160">この設定では、各トランザクションの持続性がトランザクション レベル (DELAYED_DURABILITY = { *OFF* | ON }) で決定されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-160">With this setting, each transaction's durability is determined at the transaction level - DELAYED_DURABILITY = { *OFF* | ON }.</span></span> <span data-ttu-id="7d1bc-161">詳細については、「 [Atomic ブロックレベルの制御-ネイティブコンパイルストアドプロシージャ](#atomic-block-level-control---natively-compiled-stored-procedures)」と「[コミットレベル制御-transact-sql](#commit-level-control---t-sql) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-161">See [Atomic block level control - Natively Compiled Stored Procedures](#atomic-block-level-control---natively-compiled-stored-procedures) and [COMMIT level control - Transact-SQL](#commit-level-control---t-sql) for more information.</span></span>  
  
 `FORCED`  
 <span data-ttu-id="7d1bc-162">この設定では、データベースにコミットされるすべてのトランザクションに遅延持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-162">With this setting, every transaction that commits on the database is delayed durable.</span></span> <span data-ttu-id="7d1bc-163">トランザクションで完全持続性 (DELAYED_DURABILITY = OFF) が指定された場合も、指定がまったく行われていない場合も、遅延持続性トランザクションになります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-163">Whether the transaction specifies fully durable (DELAYED_DURABILITY = OFF) or makes no specification, the transaction is delayed durable.</span></span> <span data-ttu-id="7d1bc-164">データベースに対してトランザクションの遅延持続性が役立ち、アプリケーション コードの変更を行わない場合に、この設定を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-164">This setting is useful when delayed transaction durability is useful for a database and you do not want to change any application code.</span></span>  
  
### <a name="atomic-block-level-control---natively-compiled-stored-procedures"></a><span data-ttu-id="7d1bc-165"> ATOMIC ブロック レベルの制御 - ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="7d1bc-165">Atomic block level control - Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="7d1bc-166">次のコードは、ATOMIC ブロック内で使用します。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-166">The following code goes inside the atomic block.</span></span>  
  
```sql  
DELAYED_DURABILITY = { OFF | ON }  
```  
  
 `OFF`  
 <span data-ttu-id="7d1bc-167">[既定値] トランザクションに完全持続性が適用されます。ただし、データベース オプション DELAYED_DURABLITY = FORCED が有効であれば、コミットは非同期的であり、遅延持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-167">[default] The transaction is fully durable, unless the database option DELAYED_DURABLITY = FORCED is in effect, in which case the commit is asynchronous and thus delayed durable.</span></span> <span data-ttu-id="7d1bc-168">詳細については、「 [データベース レベルの制御](#database-level-control) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-168">See [Database level control](#database-level-control) for more information.</span></span>  
  
 `ON`  
 <span data-ttu-id="7d1bc-169">トランザクションに遅延持続性が適用されます。ただし、データベース オプション DELAYED_DURABLITY = DISABLED が有効であれば、コミットは同期的であり、完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-169">The transaction is delayed durable, unless the database option DELAYED_DURABLITY = DISABLED is in effect, in which case the commit is synchronous and thus fully durable.</span></span>  <span data-ttu-id="7d1bc-170">詳細については、「 [データベース レベルの制御](#database-level-control) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-170">See [Database level control](#database-level-control) for more information.</span></span>  
  
 <span data-ttu-id="7d1bc-171">**コード例:**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-171">**Example Code:**</span></span>  
  
```sql  
CREATE PROCEDURE <procedureName> ...  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    DELAYED_DURABILITY = ON,  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'English'  
    ...  
)  
END  
```  
  
### <a name="table-1-durability-in-atomic-blocks"></a><span data-ttu-id="7d1bc-172">表 1:ATOMIC ブロックの持続性</span><span class="sxs-lookup"><span data-stu-id="7d1bc-172">Table 1: Durability in Atomic Blocks</span></span>  
  
|<span data-ttu-id="7d1bc-173">ATOMIC ブロックの持続性オプション</span><span class="sxs-lookup"><span data-stu-id="7d1bc-173">Atomic block durability option</span></span>|<span data-ttu-id="7d1bc-174">既存のトランザクションが存在しない場合</span><span class="sxs-lookup"><span data-stu-id="7d1bc-174">No existing transaction</span></span>|<span data-ttu-id="7d1bc-175">処理中の (完全持続性または遅延持続性) トランザクションが存在する場合</span><span class="sxs-lookup"><span data-stu-id="7d1bc-175">Transaction in process (fully or delayed durable)</span></span>|  
|------------------------------------|-----------------------------|---------------------------------------------------------|  
|`DELAYED_DURABILITY = OFF`|<span data-ttu-id="7d1bc-176">ATOMIC ブロックで、新しい完全持続性トランザクションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-176">Atomic block starts a new fully durable transaction.</span></span>|<span data-ttu-id="7d1bc-177">ATOMIC ブロックで、既存のトランザクションにセーブポイントが作成され、新しいトランザクションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-177">Atomic block creates a save point in the existing transaction, then begins the new transaction.</span></span>|  
|`DELAYED_DURABILITY = ON`|<span data-ttu-id="7d1bc-178">ATOMIC ブロックで、新しい遅延持続性トランザクションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-178">Atomic block starts a new delayed durable transaction.</span></span>|<span data-ttu-id="7d1bc-179">ATOMIC ブロックで、既存のトランザクションにセーブポイントが作成され、新しいトランザクションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-179">Atomic block creates a save point in the existing transaction, then begins the new transaction.</span></span>|  
  
### <a name="commit-level-control---t-sql"></a><span data-ttu-id="7d1bc-180">コミットレベルの制御-(T-sql)</span><span class="sxs-lookup"><span data-stu-id="7d1bc-180">COMMIT level control - (T-SQL)</span></span>
 <span data-ttu-id="7d1bc-181">COMMIT 構文は、トランザクションの遅延持続性を適用できるように拡張されています。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-181">The COMMIT syntax is extended so you can force delayed transaction durability.</span></span> <span data-ttu-id="7d1bc-182">DELAYED_DURABILITY がデータベース レベルで DISABLED または FORCED に設定されている場合 (上記を参照)、この COMMIT オプションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-182">If DELAYED_DURABILITY is DISABLED or FORCED at the database level (see above) this COMMIT option is ignored.</span></span>  
  
```sql  
COMMIT [ { TRAN | TRANSACTION } ] [ transaction_name | @tran_name_variable ] ] [ WITH ( DELAYED_DURABILITY = { OFF | ON } ) ]  
  
```  
  
 `OFF`  
 <span data-ttu-id="7d1bc-183">[既定値] トランザクションの COMMIT に完全持続性が適用されます。ただし、データベース オプション DELAYED_DURABLITY = FORCED が有効であれば、COMMIT は非同期的であり、遅延持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-183">[default] The transaction COMMIT is fully durable, unless the database option DELAYED_DURABLITY = FORCED is in effect, in which case the COMMIT is asynchronous and thus delayed durable.</span></span> <span data-ttu-id="7d1bc-184">詳細については、「 [データベース レベルの制御](#database-level-control) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-184">See [Database level control](#database-level-control) for more information.</span></span>  
  
 `ON`  
 <span data-ttu-id="7d1bc-185">トランザクションの COMMIT に遅延持続性が適用されます。ただし、データベース オプション DELAYED_DURABLITY = DISABLED が有効であれば、COMMIT は同期的であり、完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-185">The transaction COMMIT is delayed durable, unless the database option DELAYED_DURABLITY = DISABLED is in effect, in which case the COMMIT is synchronous and thus fully durable.</span></span> <span data-ttu-id="7d1bc-186">詳細については、「 [データベース レベルの制御](#database-level-control) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-186">See [Database level control](#database-level-control) for more information.</span></span>  
  
### <a name="summary-of-options-and-their-interactions"></a><span data-ttu-id="7d1bc-187">オプションとその作用の概要</span><span class="sxs-lookup"><span data-stu-id="7d1bc-187">Summary of options and their interactions</span></span>  
 <span data-ttu-id="7d1bc-188">このテーブルは、データベース レベルの遅延持続性設定とコミット レベルの設定の相互作用をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-188">This table summarizes the interactions between database level delayed durability settings and commit level settings.</span></span> <span data-ttu-id="7d1bc-189">データベース レベルの設定はコミット レベルの設定よりも常に優先されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-189">Database level settings always take precedence over commit level settings.</span></span>  
  
|<span data-ttu-id="7d1bc-190">COMMIT の設定/データベースの設定</span><span class="sxs-lookup"><span data-stu-id="7d1bc-190">COMMIT setting/Database setting</span></span>|<span data-ttu-id="7d1bc-191">DELAYED_DURABILITY = DISABLED</span><span class="sxs-lookup"><span data-stu-id="7d1bc-191">DELAYED_DURABILITY = DISABLED</span></span>|<span data-ttu-id="7d1bc-192">DELAYED_DURABILITY = ALLOWED</span><span class="sxs-lookup"><span data-stu-id="7d1bc-192">DELAYED_DURABILITY = ALLOWED</span></span>|<span data-ttu-id="7d1bc-193">DELAYED_DURABILITY = FORCED</span><span class="sxs-lookup"><span data-stu-id="7d1bc-193">DELAYED_DURABILITY = FORCED</span></span>|  
|--------------------------------------|-------------------------------------|------------------------------------|-----------------------------------|  
|<span data-ttu-id="7d1bc-194">`DELAYED_DURABILITY = OFF` データベース レベル トランザクション。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-194">`DELAYED_DURABILITY = OFF` Database level transactions.</span></span>|<span data-ttu-id="7d1bc-195">トランザクションに完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-195">Transaction is fully durable.</span></span>|<span data-ttu-id="7d1bc-196">トランザクションに完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-196">Transaction is fully durable.</span></span>|<span data-ttu-id="7d1bc-197">トランザクションに遅延持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-197">Transaction is delayed durable.</span></span>|  
|<span data-ttu-id="7d1bc-198">`DELAYED_DURABILITY = ON` データベース レベル トランザクション。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-198">`DELAYED_DURABILITY = ON` Database level transactions.</span></span>|<span data-ttu-id="7d1bc-199">トランザクションに完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-199">Transaction is fully durable.</span></span>|<span data-ttu-id="7d1bc-200">トランザクションに遅延持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-200">Transaction is delayed durable.</span></span>|<span data-ttu-id="7d1bc-201">トランザクションに遅延持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-201">Transaction is delayed durable.</span></span>|  
|<span data-ttu-id="7d1bc-202">`DELAYED_DURABILITY = OFF` 複数データベース間トランザクションまたは分散トランザクション。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-202">`DELAYED_DURABILITY = OFF` Cross database or distributed transaction.</span></span>|<span data-ttu-id="7d1bc-203">トランザクションに完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-203">Transaction is fully durable.</span></span>|<span data-ttu-id="7d1bc-204">トランザクションに完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-204">Transaction is fully durable.</span></span>|<span data-ttu-id="7d1bc-205">トランザクションに完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-205">Transaction is fully durable.</span></span>|  
|<span data-ttu-id="7d1bc-206">`DELAYED_DURABILITY = ON` 複数データベース間トランザクションまたは分散トランザクション。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-206">`DELAYED_DURABILITY = ON` Cross database or distributed transaction.</span></span>|<span data-ttu-id="7d1bc-207">トランザクションに完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-207">Transaction is fully durable.</span></span>|<span data-ttu-id="7d1bc-208">トランザクションに完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-208">Transaction is fully durable.</span></span>|<span data-ttu-id="7d1bc-209">トランザクションに完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-209">Transaction is fully durable.</span></span>|  
  
## <a name="how-to-force-a-transaction-log-flush"></a><span data-ttu-id="7d1bc-210">トランザクション ログのフラッシュを強制する方法</span><span class="sxs-lookup"><span data-stu-id="7d1bc-210">How to force a transaction log flush</span></span>  
 <span data-ttu-id="7d1bc-211">強制的にトランザクション ログをディスクにフラッシュするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-211">There are two means to force flush the transaction log to disk.</span></span>  
  
-   <span data-ttu-id="7d1bc-212">同じデータベースを変更する完全持続性トランザクションを実行する。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-212">Execute any fully durable transaction that alters the same database.</span></span> <span data-ttu-id="7d1bc-213">これにより、それまでにコミット済みの遅延持続性トランザクションのログ レコードがすべて強制的にディスクにフラッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-213">This forces a flush of the log records of all preceding committed delayed durability transactions to disk.</span></span>  
  
-   <span data-ttu-id="7d1bc-214">システム ストアド プロシージャ `sp_flush_log`を実行する。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-214">Execute the system stored procedure `sp_flush_log`.</span></span> <span data-ttu-id="7d1bc-215">このプロシージャにより、それまでにコミット済みの遅延持続性トランザクションのログ レコードがすべて強制的にディスクにフラッシュされます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-215">This procedure forces a flush of the log records of all preceding committed delayed durable transactions to disk.</span></span> <span data-ttu-id="7d1bc-216">詳細については、「[sys.sp_flush_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-216">For more information see [sys.sp_flush_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql).</span></span>  
  
##  <a name="delayed-durability-and-other-sql-server-features"></a><span data-ttu-id="7d1bc-217">遅延持続性とその他の SQL Server 機能</span><span class="sxs-lookup"><span data-stu-id="7d1bc-217">Delayed durability and other SQL Server features</span></span>  
 <span data-ttu-id="7d1bc-218">**変更の追跡と変更データ キャプチャ**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-218">**Change tracking and change data capture**</span></span>  
 <span data-ttu-id="7d1bc-219">変更の追跡を有効にしたすべてのトランザクションには、完全持続可能性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-219">All transactions with change tracking are fully durable.</span></span> <span data-ttu-id="7d1bc-220">変更の追跡が有効なテーブルに対して書き込み操作を行うトランザクションには、変更追跡プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-220">A transaction has the change tracking property if it does any write operations to tables that are enabled for change tracking.</span></span> <span data-ttu-id="7d1bc-221">変更データ キャプチャ (CDC) を使用するデータベースの場合、遅延持続は使用できません。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-221">The use of delayed durability is not supported for databases which use change data capture (CDC).</span></span>   
  
 <span data-ttu-id="7d1bc-222">**クラッシュ後の復旧**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-222">**Crash recovery**</span></span>  
 <span data-ttu-id="7d1bc-223">一貫性は保証されますが、コミット済みの遅延持続性トランザクションから変更内容が失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-223">Consistency is guaranteed, but some changes from delayed durable transactions that have committed may be lost.</span></span>  
  
 <span data-ttu-id="7d1bc-224">**複数データベース間と DTC**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-224">**Cross-database and DTC**</span></span>  
 <span data-ttu-id="7d1bc-225">複数データベース間トランザクションまたは分散トランザクションの場合、データベースまたはトランザクションのコミット設定に関係なく、トランザクションには完全持続性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-225">If a transaction is cross-database or distributed, if is fully durable, regardless of any database or transaction commit setting.</span></span>  
  
 <span data-ttu-id="7d1bc-226">**AlwaysOn 可用性グループとミラーリング**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-226">**Always On Availability Groups and Mirroring**</span></span>  
 <span data-ttu-id="7d1bc-227">遅延持続性トランザクションでは、プライマリまたはいずれかのセカンダリに関する持続性は保証されません。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-227">Delayed durable transactions do not guarantee any durability on either the primary or any of the secondaries.</span></span> <span data-ttu-id="7d1bc-228">また、セカンダリでのトランザクションに関するナレッジは保証されません。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-228">In addition, they do not guarantee any knowledge about the transaction at the secondary.</span></span> <span data-ttu-id="7d1bc-229">コミット後、同期セカンダリからの受信確認を受信する前に、制御がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-229">After commit, control is returned to the client before any acknowledgement is received from any synchronous secondary.</span></span>  
  
 <span data-ttu-id="7d1bc-230">**フェールオーバー クラスタリング**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-230">**Failover clustering**</span></span>  
 <span data-ttu-id="7d1bc-231">遅延持続性トランザクションによる書き込みの一部が失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-231">Some delayed durable transaction writes might be lost.</span></span>  
  
 <span data-ttu-id="7d1bc-232">**トランザクション レプリケーション**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-232">**Transaction Replication**</span></span>  
 <span data-ttu-id="7d1bc-233">遅延持続性トランザクションは、トランザクション レプリケーションではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-233">Delayed durable transactions is not supported with Transactional Replication.</span></span>  
  
 <span data-ttu-id="7d1bc-234">**ログ配布**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-234">**Log shipping**</span></span>  
 <span data-ttu-id="7d1bc-235">配信されるログに含まれるのは、持続可能な状態になったトランザクションのみです。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-235">Only transactions that have been made durable are included in the log that is shipped.</span></span>  
  
 <span data-ttu-id="7d1bc-236">**ログ バックアップ**</span><span class="sxs-lookup"><span data-stu-id="7d1bc-236">**Log Backup**</span></span>  
 <span data-ttu-id="7d1bc-237">バックアップに含まれるのは、持続可能な状態になったトランザクションのみです。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-237">Only transactions that have been made durable are included in the backup.</span></span>  
  
## <a name="when-can-i-lose-data"></a><span data-ttu-id="7d1bc-238">データが失われるケース</span><span class="sxs-lookup"><span data-stu-id="7d1bc-238">When can I lose data?</span></span>  
 <span data-ttu-id="7d1bc-239">遅延持続性をテーブルに実装する場合、状況によってはデータが失われる可能性があることを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-239">If you implement delayed durability on any of your tables, you should understand that certain circumstances can lead to data loss.</span></span> <span data-ttu-id="7d1bc-240">一切のデータ損失を許容できない場合は、テーブルに対して遅延持続性は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-240">If you cannot tolerate any data loss, you should not use delayed durability on your tables.</span></span>  
  
### <a name="catastrophic-events"></a><span data-ttu-id="7d1bc-241">重大なイベント</span><span class="sxs-lookup"><span data-stu-id="7d1bc-241">Catastrophic events</span></span>  
 <span data-ttu-id="7d1bc-242">サーバー クラッシュなどの重大なイベントが発生すると、ディスクに保存されていないすべてのコミット済みトランザクションのデータが失われます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-242">In the case of a catastrophic event, like a server crash, you will lose the data for all committed transactions that have not been saved to disk.</span></span> <span data-ttu-id="7d1bc-243">遅延持続性トランザクションは、データベース内のいずれかのテーブル (持続性のあるメモリ最適化テーブルまたはディスク ベース テーブル) に対して完全持続性トランザクションが実行されるか、 `sp_flush_log` が呼び出されるたびに、ディスクに保存されます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-243">Delayed durable transactions are saved to disk whenever a fully durable transaction is executed against any table (durable memory-optimized or disk-based) in the database, or `sp_flush_log` is called.</span></span> <span data-ttu-id="7d1bc-244">遅延持続性トランザクションを使用している場合、定期的に更新するか定期的に `sp_flush_log` を呼び出すことができる小さいテーブルをデータベース内に作成して、未処理のコミット済みトランザクションすべてを保存できます。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-244">If you are using delayed durable transactions, you may want to create a small table in the database that you can periodically update or periodically call `sp_flush_log` to save all outstanding committed transactions.</span></span> <span data-ttu-id="7d1bc-245">トランザクション ログもいっぱいになるたびにフラッシュされますが、それを予測するのは難しく、制御は不可能です。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-245">The transaction log also flushes whenever it becomes full, but that is hard to predict and impossible to control.</span></span>  
  
### <a name="sql-server-shutdown-and-restart"></a><span data-ttu-id="7d1bc-246">SQL Server のシャットダウンと再起動</span><span class="sxs-lookup"><span data-stu-id="7d1bc-246">SQL Server shutdown and restart</span></span>  
 <span data-ttu-id="7d1bc-247">遅延持続性の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の予期しないシャットダウンと予期されたシャットダウン/再起動に違いはありません。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-247">For delayed durability, there is no difference between an unexpected shutdown and an expected shutdown/restart of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7d1bc-248">重大なイベントと同様に、データ損失に対する計画を立てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-248">Like catastrophic events, you should plan for data loss.</span></span> <span data-ttu-id="7d1bc-249">計画されたシャットダウン/再起動では、ディスクに書き込まれていない一部のトランザクションが最初にディスクに保存される場合がありますが、それを予期することはできません。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-249">In a planned shutdown/restart some transactions that have not been written to disk may first be saved to disk, but you should not plan on it.</span></span> <span data-ttu-id="7d1bc-250">計画されているかどうかに関係なく、シャットダウン/再起動によって重大なイベントと同様にデータが失われるものとして計画してください。</span><span class="sxs-lookup"><span data-stu-id="7d1bc-250">Plan as though a shutdown/restart, whether planned or unplanned, loses the data the same as a catastrophic event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1bc-251">参照</span><span class="sxs-lookup"><span data-stu-id="7d1bc-251">See Also</span></span>  
 <span data-ttu-id="7d1bc-252">[トランザクション分離レベル](../../database-engine/transaction-isolation-levels.md) </span><span class="sxs-lookup"><span data-stu-id="7d1bc-252">[Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) </span></span>  
 [<span data-ttu-id="7d1bc-253">メモリ最適化テーブルのトランザクション分離レベルに関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="7d1bc-253">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../in-memory-oltp/memory-optimized-tables.md)  
  
  
