---
title: メモリ最適化テーブルを使用したトランザクション分離レベルのガイドライン |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e365e9ca-c34b-44ae-840c-10e599fa614f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 834c5950a8f8b0ddf8854d06c6fb1073a264fc22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716598"
---
# <a name="guidelines-for-transaction-isolation-levels-with-memory-optimized-tables"></a><span data-ttu-id="1f955-102">メモリ最適化テーブルのトランザクション分離レベルに関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="1f955-102">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>
  <span data-ttu-id="1f955-103">多くのシナリオでは、トランザクション分離レベルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f955-103">In many scenarios, you must specify the transaction isolation level.</span></span> <span data-ttu-id="1f955-104">メモリ最適化テーブルのトランザクション分離は、ディスク ベース テーブルとは異なります。</span><span class="sxs-lookup"><span data-stu-id="1f955-104">Transaction isolation for memory-optimized tables differs from disk-based tables.</span></span>  
  
 <span data-ttu-id="1f955-105">トランザクション分離レベルを指定するために必要な条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f955-105">Requirements for specifying transaction isolation level:</span></span>  
  
-   <span data-ttu-id="1f955-106">トランザクション分離レベルは、ネイティブ コンパイル ストアド プロシージャの中身を構成する ATOMIC ブロックに必要なオプションです。</span><span class="sxs-lookup"><span data-stu-id="1f955-106">TRANSACTION ISOLATION LEVEL is a required option for the ATOMIC block comprising the content of a natively compiled stored procedure.</span></span>  
  
-   <span data-ttu-id="1f955-107">複数のコンテナーにまたがるトランザクションで分離レベルを使用することには制約があるため、解釈された [!INCLUDE[tsql](../includes/tsql-md.md)] でメモリ最適化テーブルを使用する場合には、そのテーブルへのアクセスに使用する分離レベルを指定するテーブル ヒントを併用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="1f955-107">Because of restrictions on isolation level use in cross-container transactions, uses of memory-optimized tables in interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] must often be accompanied by a table hint specifying the isolation level used to access the table.</span></span> <span data-ttu-id="1f955-108">分離レベルのヒントと複数コンテナーにまたがるトランザクションの詳細については、「[トランザクション分離レベル](../../2014/database-engine/transaction-isolation-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f955-108">For more information about isolation level hints and cross-container transactions, see [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).</span></span>  
  
-   <span data-ttu-id="1f955-109">必要なトランザクション分離レベルは、明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f955-109">The desired transaction isolation level must be explicitly declared.</span></span> <span data-ttu-id="1f955-110">ロック ヒント (XLOCK など) を使用してトランザクションの特定の行またはテーブルの分離を保証することはできません。</span><span class="sxs-lookup"><span data-stu-id="1f955-110">It is not possible to use locking hints (such as XLOCK) to guarantee the isolation of certain rows or tables in the transaction.</span></span>  
  
-   <span data-ttu-id="1f955-111">データベースにアクセスするアプリケーションでは、決定的なトランザクションの失敗を引き起こす競合、検証の失敗、およびコミット依存関係の失敗に起因するエラーを処理するための再試行ロジックを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f955-111">The application accessing the database should implement retry logic to deal with errors resulting from transaction-dooming conflicts, validation failures, and commit-dependency failures.</span></span> <span data-ttu-id="1f955-112">コミット依存関係の失敗は、読み取り専用トランザクションでも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1f955-112">Note that commit dependency failures can occur even with read-only transactions.</span></span>  
  
-   <span data-ttu-id="1f955-113">実行時間の長いトランザクションは、メモリ最適化テーブルでは避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f955-113">Long-running transactions should be avoided with memory-optimized tables.</span></span> <span data-ttu-id="1f955-114">このようなトランザクションによって、競合とその後のトランザクション終了の可能性が高まります。</span><span class="sxs-lookup"><span data-stu-id="1f955-114">Such transactions increase the likelihood of conflicts and subsequent transaction terminations.</span></span> <span data-ttu-id="1f955-115">実行時間が長いトランザクションは、ガベージ コレクションが遅延する原因にもなります。</span><span class="sxs-lookup"><span data-stu-id="1f955-115">A long-running transaction also defers garbage collection.</span></span> <span data-ttu-id="1f955-116">トランザクションの実行時間が長くなるほど、最近削除された行のバージョンがインメモリ OLTP で保持される時間も長くなります。これにより、新しいトランザクションの参照パフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1f955-116">The longer a transaction runs, the longer In-Memory OLTP keeps recently deleted row versions, which can decrease lookup performance for new transactions.</span></span>  
  
 <span data-ttu-id="1f955-117">ディスク ベース テーブルでは通常、トランザクションの分離にロックおよびブロックを使用しています。</span><span class="sxs-lookup"><span data-stu-id="1f955-117">Disk-based tables typically rely on locking and blocking for transaction isolation.</span></span> <span data-ttu-id="1f955-118">メモリ最適化テーブルでは、複数バージョン管理および競合検出を使用して分離を確実なものにしています。</span><span class="sxs-lookup"><span data-stu-id="1f955-118">Memory-optimized tables rely on multi-versioning and conflict detection to guarantee isolation.</span></span> <span data-ttu-id="1f955-119">詳細については、[メモリ最適化テーブルのトランザクション](../relational-databases/in-memory-oltp/memory-optimized-tables.md)での競合検出、検証、コミットの依存関係の確認に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f955-119">For details, see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="1f955-120">ディスク ベース テーブルでは、SNAPSHOT および READ_COMMITTED_SNAPSHOT の 2 つの分離レベルによる複数バージョン管理が可能です。</span><span class="sxs-lookup"><span data-stu-id="1f955-120">Disk-based tables do allow multi-versioning with the isolation levels SNAPSHOT and READ_COMMITTED_SNAPSHOT.</span></span> <span data-ttu-id="1f955-121">メモリ最適化テーブルでは、REPEATABLE READ と SERIALIZABLE も含め、すべての分離レベルが複数バージョン ベースになっています。</span><span class="sxs-lookup"><span data-stu-id="1f955-121">For memory-optimized tables all isolation levels are multi-version based, including REPEATABLE READ and SERIALIZABLE.</span></span>  
  
## <a name="types-of-transactions"></a><span data-ttu-id="1f955-122">トランザクションの種類</span><span class="sxs-lookup"><span data-stu-id="1f955-122">Types of Transactions</span></span>  
 <span data-ttu-id="1f955-123">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のクエリはいずれも、トランザクションのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="1f955-123">Every query in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] runs in the context of a transaction.</span></span>  
  
 <span data-ttu-id="1f955-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のトランザクションの種類は、3 つに分けることができます。</span><span class="sxs-lookup"><span data-stu-id="1f955-124">There are three types of transactions in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="1f955-125">自動コミット トランザクション。</span><span class="sxs-lookup"><span data-stu-id="1f955-125">Autocommit transactions.</span></span> <span data-ttu-id="1f955-126">アクティブなトランザクション コンテキストがなく、暗黙のトランザクションがセッションで ON に設定されていない場合には、各クエリに独自のトランザクション コンテキストがあります。</span><span class="sxs-lookup"><span data-stu-id="1f955-126">If there is no active transaction context and implicit transactions are not set to ON in the session, each query has its own transaction context.</span></span> <span data-ttu-id="1f955-127">トランザクションは、ステートメントの実行が開始されると開始となり、ステートメントが終了すると終了します。</span><span class="sxs-lookup"><span data-stu-id="1f955-127">The transaction starts when the statement starts execution, and completes when the statement finishes.</span></span>  
  
-   <span data-ttu-id="1f955-128">明示的なトランザクション。</span><span class="sxs-lookup"><span data-stu-id="1f955-128">Explicit transactions.</span></span> <span data-ttu-id="1f955-129">ユーザーは、明示的に BEGIN TRAN または BEGIN ATOMIC を使用してトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1f955-129">The user starts the transaction through an explicit BEGIN TRAN or BEGIN ATOMIC.</span></span> <span data-ttu-id="1f955-130">トランザクションは、対応する COMMIT および ROLLBACK、または (ATOMIC ブロックの場合には) END によって完了します。</span><span class="sxs-lookup"><span data-stu-id="1f955-130">The transaction is completed following the corresponding COMMIT and ROLLBACK or END (in the case of an atomic block).</span></span>  
  
-   <span data-ttu-id="1f955-131">暗黙のトランザクション。</span><span class="sxs-lookup"><span data-stu-id="1f955-131">Implicit transactions.</span></span> <span data-ttu-id="1f955-132">IMPLICIT_TRANSACTIONS オプションが ON に設定されていると、ユーザーがステートメントを実行し、アクティブなトランザクション コンテキストが存在しない場合にはいつでも、暗黙的にトランザクションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1f955-132">When the option IMPLICIT_TRANSACTIONS is set to ON, a transaction is started implicitly whenever the user executes a statement and there is no active transaction context.</span></span> <span data-ttu-id="1f955-133">この種のトランザクションは、明示的に COMMIT および ROLLBACK を使用することによって完了します。</span><span class="sxs-lookup"><span data-stu-id="1f955-133">The transaction is completed through an explicit COMMIT and ROLLBACK.</span></span>  
  
## <a name="baseline-read-committed-isolation"></a><span data-ttu-id="1f955-134">ベースラインとしての READ COMMITTED 分離</span><span class="sxs-lookup"><span data-stu-id="1f955-134">Baseline READ COMMITTED Isolation</span></span>  
 <span data-ttu-id="1f955-135">READ COMMITTED は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定の分離レベルです。</span><span class="sxs-lookup"><span data-stu-id="1f955-135">READ COMMITTED is the default isolation level in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f955-136">分離レベル READ COMMITTED は、トランザクションが、現在のトランザクションの外部で実行された変更に起因する、コミットされていないデータを認識しないことを保証します。</span><span class="sxs-lookup"><span data-stu-id="1f955-136">The isolation level READ COMMITTED guarantees that transactions do not see any uncommitted data from changes outside the current transaction.</span></span> <span data-ttu-id="1f955-137">つまり、トランザクションは、データベースにコミットされたデータ、または現在のトランザクションによって変更されたデータだけを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="1f955-137">In other words, the transaction only reads data which has either been committed to the database, or has been changed by the current transaction.</span></span>  
  
 <span data-ttu-id="1f955-138">メモリ最適化テーブルでサポートされる分離レベルは、すべて READ COMMITTED が保証されています。</span><span class="sxs-lookup"><span data-stu-id="1f955-138">All isolation levels supported for memory-optimized tables provide the read committed guarantee.</span></span> <span data-ttu-id="1f955-139">このため、トランザクションによってさらに厳密な保証が求められるのでなければ、メモリ最適化テーブルでサポートされる分離レベルのどれを使用してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="1f955-139">Therefore, if the transaction does not require stronger guarantees, you can use any of the isolation levels supported for memory-optimized tables.</span></span> <span data-ttu-id="1f955-140">SNAPSHOT では、使用するシステム リソースが分離レベルのうち最も少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="1f955-140">SNAPSHOT uses the fewest system resources, compared to other isolation levels.</span></span>  
  
 <span data-ttu-id="1f955-141">SNAPSHOT 分離レベル (メモリ最適化テーブルでサポートされる分離レベルのうち、最も低いレベル) による保証には、READ COMMITTED の保証が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1f955-141">The guarantee provided by the SNAPSHOT isolation level (the lowest level of isolation supported for memory-optimized tables) includes the guarantees of READ COMMITTED.</span></span> <span data-ttu-id="1f955-142">トランザクションの各ステートメントでは、同一で一貫性のあるバージョンのデータベースを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="1f955-142">Every statement in the transaction reads the same, consistent version of the database.</span></span> <span data-ttu-id="1f955-143">トランザクションによって読み取られる行がいずれもデータベースにコミットされるだけでなく、すべての読み取り操作で同じトランザクションによって変更が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1f955-143">Not only are all the rows read by the transaction committed to the database, also all the read operations see the set of changes made by the same set of transactions.</span></span>  
  
 <span data-ttu-id="1f955-144">**ガイドライン**: READ COMMITTED 分離保証のみが必要な場合は、ネイティブコンパイルストアドプロシージャでスナップショット分離を使用し、解釈されたを通じてメモリ最適化テーブルにアクセスし [!INCLUDE[tsql](../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1f955-144">**Guideline**: If only the READ COMMITTED isolation guarantee is required, use SNAPSHOT isolation with natively compiled stored procedures and for accessing memory-optimized tables through interpreted [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1f955-145">自動コミット トランザクションでは、分離レベル READ COMMITTED が暗黙的にメモリ最適化テーブルの SNAPSHOT にマッピングされています。</span><span class="sxs-lookup"><span data-stu-id="1f955-145">For autocommit transactions, the isolation level READ COMMITTED is implicitly mapped to SNAPSHOT for memory-optimized tables.</span></span> <span data-ttu-id="1f955-146">このため、TRANSACTION ISOLATION LEVEL セッションの設定が READ COMMITTED に設定されている場合には、メモリ最適化テーブルにアクセスするときにテーブル ヒントを使用して分離レベルを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1f955-146">Therefore, if the TRANSACTION ISOLATION LEVEL session setting is set to READ COMMITTED, it is not necessary to specify the isolation level through a table hint when accessing memory-optimized tables.</span></span>  
  
 <span data-ttu-id="1f955-147">以下の自動コミット トランザクションの例では、アドホック バッチの一環としてメモリ最適化テーブル Customers と通常のテーブル [Order History] の間の結合を表示しています。</span><span class="sxs-lookup"><span data-stu-id="1f955-147">The following autocommit transaction example shows a join between a memory-optimized table Customers and a regular table [Order History], as part of an ad hoc batch:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;  
GO  
SELECT *   
FROM dbo.Customers AS c   
LEFT JOIN dbo.[Order History] AS oh   
    ON c.customer_id = oh.customer_id;  
```  
  
 <span data-ttu-id="1f955-148">以下の明示的トランザクションまたは暗黙的トランザクションの例でも同じ結合を示していますが、今回は明示的なユーザー トランザクションを使用しています。</span><span class="sxs-lookup"><span data-stu-id="1f955-148">The following explicit or implicit transactions example shows the same join, but this time in an explicit user transaction.</span></span> <span data-ttu-id="1f955-149">テーブル ヒント WITH (SNAPSHOT) で示すように、メモリ最適化テーブル Customers が SNAPSHOT 分離レベルでアクセスされています。これに対して、通常のテーブル [Order History] は、READ COMMITTED 分離レベルでアクセスされています。</span><span class="sxs-lookup"><span data-stu-id="1f955-149">The memory-optimized table Customers is accessed under snapshot isolation, as indicated through the table hint WITH (SNAPSHOT), and the regular table [Order History] is accessed under read committed isolation:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
GO  
BEGIN TRAN  
SELECT * FROM dbo.Customers c with (SNAPSHOT)   
LEFT JOIN dbo.[Order History] oh   
    ON c.customer_id=oh.customer_id  
...  
COMMIT  
```  
  
### <a name="operational-differences"></a><span data-ttu-id="1f955-150">動作の違い</span><span class="sxs-lookup"><span data-stu-id="1f955-150">Operational Differences</span></span>  
 <span data-ttu-id="1f955-151">ディスク ベース テーブルを使用するアプリケーションが使用している主な実装は、READ COMMITTED 保証のほかに 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="1f955-151">Besides the read committed guarantee, there are also two key implementation details that applications using disk-based tables may rely on.</span></span> <span data-ttu-id="1f955-152">READ COMMITTED 分離を使用してアクセスするディスク ベース テーブルを SNAPSHOT 分離を使用してアクセスするメモリ最適化テーブルに変換するときには、以下の 2 点に注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="1f955-152">Be aware of the following when converting a disk-based table that is accessed using READ COMMITTED isolation to a memory-optimized table that is accessed using SNAPSHOT isolation:</span></span>  
  
-   <span data-ttu-id="1f955-153">ディスク ベース テーブルに READ COMMITTED 分離レベルを実装した場合 (READ_COMMITTED_SNAPSHOT はオフと想定) には、読み取りと書き込みの間の競合を防ぐためにロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f955-153">The implementation of the READ COMMITTED isolation level for disk-based tables (assuming READ_COMMITTED_SNAPSHOT is OFF) uses locks to prevent conflicts between readers and writers.</span></span> <span data-ttu-id="1f955-154">書き込み側が行の更新を開始するときに、ロックを取得します。トランザクションがコミットされるまで、このロックは解放されません。</span><span class="sxs-lookup"><span data-stu-id="1f955-154">When a writer starts updating a row, it takes a lock and does not release the lock until the transaction is committed.</span></span> <span data-ttu-id="1f955-155">読み取り操作はすべてブロックされ、書き込みトランザクションがコミットされるまで待機することになります。</span><span class="sxs-lookup"><span data-stu-id="1f955-155">Any read operations are blocked and will wait for the write transaction to commit.</span></span>  
  
     <span data-ttu-id="1f955-156">一部のアプリケーションでは、書き込み側がコミットするまでの間、読み取り側が常に待機することが想定されています。特に、アプリケーション層で 2 つのトランザクションを同期させる場合です。</span><span class="sxs-lookup"><span data-stu-id="1f955-156">Some applications may assume readers always wait for writers to commit, particularly if there is any synchronization between the two transactions in the application tier.</span></span>  
  
     <span data-ttu-id="1f955-157">**ガイドライン:** アプリケーションは、ブロック動作に依存することはできません。</span><span class="sxs-lookup"><span data-stu-id="1f955-157">**Guideline:** Applications cannot rely on blocking behavior.</span></span> <span data-ttu-id="1f955-158">アプリケーションが同時実行トランザクション間の同期を必要とする場合、そのようなロジックをアプリケーション層またはデータベース層に実装するには、 [sp_getapplock &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f955-158">If an application needs synchronization between concurrent transactions, such logic can be implemented in the application tier or in the database tier, through [sp_getapplock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql).</span></span>  
  
-   <span data-ttu-id="1f955-159">READ COMMITTED 分離を使用するトランザクションでは、各ステートメントでデータベースの行の最新のバージョンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f955-159">In transactions that use READ COMMITTED isolation, each statement sees the most recent version of the rows in the database.</span></span> <span data-ttu-id="1f955-160">このため、以降のステートメントでは、データベースの状態が変化することになります。</span><span class="sxs-lookup"><span data-stu-id="1f955-160">Therefore, subsequent statements see changes in the state of the database.</span></span>  
  
     <span data-ttu-id="1f955-161">新しい行が見つかるまで WHILE ループを使用してテーブルをポーリングする方法は、この前提を使用するアプリケーション パターンの一例です。</span><span class="sxs-lookup"><span data-stu-id="1f955-161">Polling a table using a WHILE loop until a new row has been found is an example of an application pattern that uses this assumption.</span></span> <span data-ttu-id="1f955-162">ループの各反復処理で、クエリにデータベースの最新の更新が適用されます。</span><span class="sxs-lookup"><span data-stu-id="1f955-162">With each iteration of the loop, the query will see the latest updates in the database.</span></span>  
  
     <span data-ttu-id="1f955-163">**ガイドライン:** アプリケーションでメモリ最適化テーブルをポーリングして、テーブルに書き込まれた最新の行を取得する必要がある場合は、トランザクションのスコープ外にポーリングループを移動します。</span><span class="sxs-lookup"><span data-stu-id="1f955-163">**Guideline:** If an application needs to poll a memory-optimized table to obtain the most recent rows written to the table, move the polling loop outside the scope of the transaction.</span></span>  
  
     <span data-ttu-id="1f955-164">以下は、この前提を使用するアプリケーション パターンの一例です。</span><span class="sxs-lookup"><span data-stu-id="1f955-164">The following is an example application pattern that uses this assumption.</span></span> <span data-ttu-id="1f955-165">WHILE ループを使用して、新しい行が見つかるまでテーブルをポーリングしています。</span><span class="sxs-lookup"><span data-stu-id="1f955-165">Polling a table using a WHILE loop until a new row is found.</span></span> <span data-ttu-id="1f955-166">ループの各反復処理で、クエリがデータベースの最新の更新にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1f955-166">In each loop iteration, the query will access the latest updates in the database.</span></span>  
  
 <span data-ttu-id="1f955-167">次の例のスクリプトでは、行を取得するまでテーブル t1 をポーリングしています。</span><span class="sxs-lookup"><span data-stu-id="1f955-167">The following example script polls a table t1 until it has a row.</span></span> <span data-ttu-id="1f955-168">その後で、テーブルから行を 1 つ削除してさらに処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="1f955-168">It then removes a single row from the table for further processing.</span></span>  
  
 <span data-ttu-id="1f955-169">ポーリングのロジックはテーブル t1 にアクセスするうえで SNAPSHOT 分離を使用しているため、トランザクションの範囲外に置く必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1f955-169">Notice that the polling logic needs to be outside the scope of the transaction, as it is using snapshot isolation to access table t1.</span></span> <span data-ttu-id="1f955-170">トランザクションの範囲内でポーリング ロジックを使用すると、トランザクションの実行時間が長くなり、好ましくありません。</span><span class="sxs-lookup"><span data-stu-id="1f955-170">Using polling logic inside the scope of a transaction would create a long-running transaction, which is a bad practice.</span></span>  
  
```sql  
-- poll table  
WHILE NOT EXISTS (SELECT 1 FROM dbo.t1)  
BEGIN   
  -- if empty, wait and poll again  
  WAITFOR DELAY '00:00:01'  
END  
  
BEGIN TRANSACTION  
  DECLARE @id int  
  SELECT TOP 1 @id=id FROM dbo.t1 WITH (SNAPSHOT)  
  DELETE FROM dbo.t1 WITH (SNAPSHOT) WHERE id=@id  
  
  -- insert processing based on @id  
COMMIT  
```  
  
## <a name="locking-table-hints"></a><span data-ttu-id="1f955-171">ロックに関するテーブル ヒント</span><span class="sxs-lookup"><span data-stu-id="1f955-171">Locking Table Hints</span></span>  
 <span data-ttu-id="1f955-172">ディスクベーステーブルでは、XLOCK などのロックヒント[&#40;(transact-sql&#41;](/sql/t-sql/queries/hints-transact-sql-table)) を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、指定された分離レベルで必要とされるよりも多くのロックを取得できます。</span><span class="sxs-lookup"><span data-stu-id="1f955-172">Locking hints ([Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)) such as HOLDLOCK and XLOCK can be used with disk-based tables to have [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] take more locks than are required for the specified isolation level.</span></span>  
  
 <span data-ttu-id="1f955-173">メモリ最適化テーブルではロックは使用しません。</span><span class="sxs-lookup"><span data-stu-id="1f955-173">Memory-optimized tables do not use locks.</span></span> <span data-ttu-id="1f955-174">REPEATABLE READ や SERIALIZABLE など、高度な分離レベルを使用して必要な保証を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="1f955-174">Higher isolation levels such as REPEATABLE READ and SERIALIZABLE can be used to declare the desired guarantees.</span></span>  
  
 <span data-ttu-id="1f955-175">ロック ヒントはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1f955-175">Locking hints are not supported.</span></span> <span data-ttu-id="1f955-176">代わりに、トランザクション分離レベルを使用して必要な保証を宣言します。</span><span class="sxs-lookup"><span data-stu-id="1f955-176">Instead, declare the required guarantees through the transaction isolation levels.</span></span> <span data-ttu-id="1f955-177">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ではメモリ最適化テーブルにロックを使用しないため、NOLOCK がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1f955-177">(NOLOCK is supported because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not take locks on memory-optimized tables.</span></span> <span data-ttu-id="1f955-178">ディスク ベース テーブルとは異なり、NOLOCK は、メモリ最適化テーブルに対する READ UNCOMMITTED 動作を示すわけではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1f955-178">Note that, in contrast to disk-based tables, NOLOCK does not imply READ UNCOMMITTED behavior for memory-optimized tables.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f955-179">参照</span><span class="sxs-lookup"><span data-stu-id="1f955-179">See Also</span></span>  
 <span data-ttu-id="1f955-180">[メモリ最適化テーブルのトランザクションについて](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="1f955-180">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="1f955-181">[メモリ最適化テーブルでのトランザクションの再試行ロジックのガイドライン](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="1f955-181">[Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="1f955-182">トランザクション分離レベル</span><span class="sxs-lookup"><span data-stu-id="1f955-182">Transaction Isolation Levels</span></span>](../../2014/database-engine/transaction-isolation-levels.md)  
  
  
