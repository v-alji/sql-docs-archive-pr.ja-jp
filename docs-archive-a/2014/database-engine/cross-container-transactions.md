---
title: 複数コンテナーにまたがるトランザクション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5d84b51a-ec17-4c5c-b80e-9e994fc8ae80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28437f0903459616a574e713c0f138e8bb459870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641213"
---
# <a name="cross-container-transactions"></a><span data-ttu-id="fe152-102">複数コンテナーにまたがるトランザクション</span><span class="sxs-lookup"><span data-stu-id="fe152-102">Cross-Container Transactions</span></span>
  <span data-ttu-id="fe152-103">複数コンテナーにまたがるトランザクションは、ネイティブ コンパイル ストアド プロシージャの呼び出しまたはメモリ最適化テーブルでの操作を含む、暗黙的または明示的なユーザー トランザクションです。</span><span class="sxs-lookup"><span data-stu-id="fe152-103">Cross-container transactions are either implicit or explicit user transactions that include calls to natively-compiled stored procedures or operations on memory-optimized tables.</span></span>  
  
 <span data-ttu-id="fe152-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、ストアド プロシージャの呼び出しでトランザクションが開始されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fe152-104">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], calls to stored procedures do not initiate a transaction.</span></span> <span data-ttu-id="fe152-105">ネイティブ コンパイル プロシージャの (ユーザー トランザクションのコンテキストではなく) 自動コミット モードでの実行は、複数コンテナーにまたがるトランザクションとは見なされません。</span><span class="sxs-lookup"><span data-stu-id="fe152-105">Executions of natively compiled procedures in autocommit mode (not in the context of a user transaction) are not considered cross-container transactions.</span></span>  
  
 <span data-ttu-id="fe152-106">メモリ最適化テーブルを参照する解釈されたクエリは、明示的または暗黙的なトランザクションから実行された場合も、自動コミット モードで実行された場合も、複数コンテナーにまたがるトランザクションの一部と見なされます。</span><span class="sxs-lookup"><span data-stu-id="fe152-106">Any interpreted query that references memory-optimized tables is considered a part of a cross-container transaction, whether executed from an explicit or implicit transaction or in auto-commit mode.</span></span>  
  
##  <a name="isolation-of-individual-operations"></a><a name="isolation"></a><span data-ttu-id="fe152-107">個々の操作の分離</span><span class="sxs-lookup"><span data-stu-id="fe152-107">Isolation of Individual Operations</span></span>  
 <span data-ttu-id="fe152-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の各トランザクションには分離レベルがあります。</span><span class="sxs-lookup"><span data-stu-id="fe152-108">Each [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] transaction has an isolation level.</span></span> <span data-ttu-id="fe152-109">既定の分離レベルは READ COMMITTED です。</span><span class="sxs-lookup"><span data-stu-id="fe152-109">The default isolation level is Read Committed.</span></span> <span data-ttu-id="fe152-110">別の分離レベルを使用するには、 [SET TRANSACTION 分離レベル &#40;transact-sql&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)を使用して分離レベルを設定できます。</span><span class="sxs-lookup"><span data-stu-id="fe152-110">To use a different isolation level, you can set the isolation level using [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
 <span data-ttu-id="fe152-111">多くの場合、ディスク ベース テーブルでの操作とは異なる分離レベルで、メモリ最適化テーブルでの操作を実行することが必要になります。</span><span class="sxs-lookup"><span data-stu-id="fe152-111">It is often necessary to perform operations on memory-optimized tables at a different isolation level than operations on disk-based tables.</span></span> <span data-ttu-id="fe152-112">トランザクションでは、ステートメントのコレクションまたは個別の読み取り操作に対して別の分離レベルを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="fe152-112">In a transaction, it is possible to set a different isolation level for a collection of statements or for an individual read operation.</span></span>  
  
### <a name="specifying-the-isolation-level-of-individual-operations"></a><span data-ttu-id="fe152-113">個別の操作の分離レベルの指定</span><span class="sxs-lookup"><span data-stu-id="fe152-113">Specifying the Isolation Level of Individual Operations</span></span>  
 <span data-ttu-id="fe152-114">トランザクションの一連のステートメントに対して別の分離レベルを設定するには、`SET TRANSACTION ISOLATION LEVEL` を使用します。</span><span class="sxs-lookup"><span data-stu-id="fe152-114">To set a different isolation level for a set of statements in a transaction, you can use `SET TRANSACTION ISOLATION LEVEL`.</span></span> <span data-ttu-id="fe152-115">トランザクションの次の例では既定で SERIALIZABLE 分離レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe152-115">The following example of a transaction uses the serializable isolation level as default.</span></span> <span data-ttu-id="fe152-116">t3、t2、および t1 に対する挿入操作や選択操作は、REPEATABLE READ 分離レベルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-116">The insert and select operations on t3, t2, and t1 are executed under repeatable read isolation.</span></span>  
  
```sql  
set transaction isolation level serializable  
go  
  
begin transaction  
 ......  
  set transaction isolation level repeatable read  
  
  insert t3 select * from t1 join t2 on t1.id=t2.id  
  
  set transaction isolation level serializable  
 ......  
commit  
```  
  
 <span data-ttu-id="fe152-117">トランザクションの既定値と異なる個別の読み取り操作の分離レベルを設定するには、テーブル ヒント (SERIALIZABLE など) を使用します。</span><span class="sxs-lookup"><span data-stu-id="fe152-117">To set an isolation level for individual read operations that is different from the transaction default, you can use a table hint (for example, serializable).</span></span> <span data-ttu-id="fe152-118">行の更新や削除を可能にするには、その行を読み取っておくことが常に必要であるため、すべての選択は読み取り操作に相当し、すべての更新やすべての削除は読み取りに相当します。</span><span class="sxs-lookup"><span data-stu-id="fe152-118">Every select corresponds to a read operation and every update and every delete corresponds to a read, because the row always needs to be read before it can be updated or deleted.</span></span> <span data-ttu-id="fe152-119">書き込みは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では常に分離されるため、挿入操作には分離レベルはありません。</span><span class="sxs-lookup"><span data-stu-id="fe152-119">Insert operations do not have an isolation level, because writes are always isolated in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fe152-120">次の例では、トランザクションの既定の分離レベルは READ COMMITTED ですが、テーブル t1 には SERIALIZABLE 分離で、テーブル t2 には SNAPSHOT 分離でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="fe152-120">In the following example, the default isolation level for the transaction is read committed, but table t1 is accessed under serializable and t2 under snapshot isolation.</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
 ......  
  
  insert t3 select * from t1 (serializable) join t2 (snapshot) on t1.id=t2.id  
  
  ......  
commit  
```  
  
### <a name="isolation-semantics-for-individual-operations"></a><span data-ttu-id="fe152-121">個別の操作の分離セマンティクス</span><span class="sxs-lookup"><span data-stu-id="fe152-121">Isolation Semantics for Individual Operations</span></span>  
 <span data-ttu-id="fe152-122">シリアル化可能なトランザクション T は完全に分離して実行されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-122">A serializable transaction T is executed in complete isolation.</span></span> <span data-ttu-id="fe152-123">他のすべてのトランザクションは、T の開始前にコミット済みであるか、T のコミット後に開始されるかのように見えます。</span><span class="sxs-lookup"><span data-stu-id="fe152-123">It is as if every other transaction has either committed before T started, or is started after T committed.</span></span> <span data-ttu-id="fe152-124">トランザクション内の別の操作に別の分離レベルがある場合は、さらに複雑になります。</span><span class="sxs-lookup"><span data-stu-id="fe152-124">It becomes more complex when different operations in a transaction have different isolation levels.</span></span>  
  
 <span data-ttu-id="fe152-125">でのトランザクション分離レベルの一般的なセマンティクスについては、「 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SET TRANSACTION 分離レベル &#40;transact-sql&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)」で説明されています。</span><span class="sxs-lookup"><span data-stu-id="fe152-125">The general semantics of the transaction isolation levels in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], along with the implications on locking, is explained in [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
 <span data-ttu-id="fe152-126">異なる操作に異なる分離レベルがある複数コンテナーにまたがるトランザクションの場合は、個別の読み取り操作の分離のセマンティクスを理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe152-126">For cross-container transactions where different operations may have different isolation levels, you need to understand the semantics of isolation of individual read operations.</span></span> <span data-ttu-id="fe152-127">書き込み操作は常に分離されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-127">Write operations are always isolated.</span></span> <span data-ttu-id="fe152-128">それぞれ異なるトランザクションでの書き込みが互いに影響し合うことはできません。</span><span class="sxs-lookup"><span data-stu-id="fe152-128">Writes in different transactions cannot impact each other.</span></span>  
  
 <span data-ttu-id="fe152-129">データの読み取り操作では、フィルター条件を満たす行の数が返されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-129">A data read operation returns a number of rows that satisfy a filter condition.</span></span>  
  
 <span data-ttu-id="fe152-130">読み取りは、トランザクション T の一部として実行されます。読み取り操作の分離レベルは、という点で理解できます。</span><span class="sxs-lookup"><span data-stu-id="fe152-130">Reads are performed as part of a transaction T. Isolation levels for read operations can be understood in terms of,</span></span>  
  
 <span data-ttu-id="fe152-131">コミットの状態</span><span class="sxs-lookup"><span data-stu-id="fe152-131">Commit Status</span></span>  
 <span data-ttu-id="fe152-132">コミットの状態では、読み取られたデータのコミットが保証されるかどうかを参照します。</span><span class="sxs-lookup"><span data-stu-id="fe152-132">Commit status refers to whether the data read is guaranteed to be committed.</span></span>  
  
 <span data-ttu-id="fe152-133">(トランザクションの) 一貫性</span><span class="sxs-lookup"><span data-stu-id="fe152-133">(Transactional) Consistency</span></span>  
 <span data-ttu-id="fe152-134">一連の読み取りに関するトランザクションの一貫性では、読み取られた行バージョンがすべて正確な同じ一連のトランザクションからの更新を含んでいることが保証されるかどうかを参照します。</span><span class="sxs-lookup"><span data-stu-id="fe152-134">Transactional consistency for a set of reads refers to whether the row versions read are all guaranteed to include updates from precisely the same set of transactions.</span></span>  
  
 <span data-ttu-id="fe152-135">安定性では、読み取られたデータについてシステムからトランザクション T への提供が保証されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-135">Stability guarantees the system gives to transaction T about the data read.</span></span>  
 <span data-ttu-id="fe152-136">安定性とは、トランザクションの読み取りが反復可能であるかどうかを意味します。</span><span class="sxs-lookup"><span data-stu-id="fe152-136">Stability refers to whether the transaction's reads are repeatable.</span></span> <span data-ttu-id="fe152-137">したがって、読み取りが反復された場合、同じ行や行バージョンが返されるかということになります。</span><span class="sxs-lookup"><span data-stu-id="fe152-137">That is, if the reads were repeated would they return the same rows and row versions?</span></span>  
  
 <span data-ttu-id="fe152-138">特定の保証では、トランザクションの論理的な終了時刻を参照します。</span><span class="sxs-lookup"><span data-stu-id="fe152-138">Certain guarantees refer to the logical end time of the transaction.</span></span> <span data-ttu-id="fe152-139">一般に、論理的な終了時刻は、トランザクションがデータベースにコミットされる時間です。</span><span class="sxs-lookup"><span data-stu-id="fe152-139">In general, the logical end time is the time the transaction is committed to the database.</span></span> <span data-ttu-id="fe152-140">メモリ最適化テーブルにトランザクションからアクセスする場合、論理的な終了時刻は、理論的には検証フェーズの開始時です </span><span class="sxs-lookup"><span data-stu-id="fe152-140">If memory-optimized tables are accessed by the transaction, the logical end time is technically the beginning of the validation phase.</span></span> <span data-ttu-id="fe152-141">(詳細については、「[メモリ最適化テーブルの](../relational-databases/in-memory-oltp/memory-optimized-tables.md)トランザクション」に記載されているトランザクションの有効期間の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe152-141">(For more information, see the transaction lifetime discussion in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="fe152-142">分離レベルに関係なく、トランザクション (T) は常に自己の更新を確認します。</span><span class="sxs-lookup"><span data-stu-id="fe152-142">Regardless of isolation level, a transaction (T) always sees its own updates:</span></span>  
  
 <span data-ttu-id="fe152-143">READ UNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="fe152-143">READ UNCOMMITTED</span></span>  
 <span data-ttu-id="fe152-144">読み取られるデータが、コミット済み、一貫した状態、または安定状態のいずれでもありません。</span><span class="sxs-lookup"><span data-stu-id="fe152-144">The data read may neither be committed, consistent, or stable.</span></span> <span data-ttu-id="fe152-145">ただし、これには T によって実行された前の書き込み操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fe152-145">However, it will include earlier write operations done by T.</span></span>  
  
 <span data-ttu-id="fe152-146">READ COMMITTED</span><span class="sxs-lookup"><span data-stu-id="fe152-146">READ COMMITTED</span></span>  
 <span data-ttu-id="fe152-147">読み取られるデータはコミットされます。</span><span class="sxs-lookup"><span data-stu-id="fe152-147">The data read will be committed.</span></span>  
  
 <span data-ttu-id="fe152-148">SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="fe152-148">SNAPSHOT</span></span>  
 <span data-ttu-id="fe152-149">SNAPSHOT 分離で T によって実行されたすべての読み取り操作には、同じ論理的読み取り時刻があります。それは、トランザクションの開始時です。</span><span class="sxs-lookup"><span data-stu-id="fe152-149">All read operations performed by T under snapshot isolation have the same logical read time, which is the beginning of the transaction.</span></span> <span data-ttu-id="fe152-150">読み取られるデータは、コミットされること、および論理的読み取りの時点で一貫性があることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-150">The data read is guaranteed to be committed and consistent as of the logical read time.</span></span> <span data-ttu-id="fe152-151">元の読み取りの時点で読み取りを繰り返しても、同じ結果を返すことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-151">Repeating a read as of the original read time is guaranteed to return the same result.</span></span>  
  
 <span data-ttu-id="fe152-152">REPEATABLE READ</span><span class="sxs-lookup"><span data-stu-id="fe152-152">REPEATABLE READ</span></span>  
 <span data-ttu-id="fe152-153">読み取られるデータは、コミットされること、およびトランザクションの論理的終了時刻まで安定状態であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-153">The data read is guaranteed to be committed and stable up to the logical end time of the transaction.</span></span>  
  
 <span data-ttu-id="fe152-154">SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="fe152-154">SERIALIZABLE</span></span>  
 <span data-ttu-id="fe152-155">すべてのシリアル化可能な読み取りとファントムの回避、およびで実行されるすべてのシリアル化可能な読み取り操作に関して、トランザクションの一貫性が保証されます。ファントムの回避とは、他のトランザクションによって書き込まれた行を返さない、T によって書き込まれた追加の行のみを返すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="fe152-155">All guarantees of REPEATABLE READ plus phantom avoidance and transactional consistency with respect to all serializable read operations performed by T. Phantom avoidance means that the scan operation can only return additional rows that were written by T, but no rows that were written by other transactions.</span></span>  
  
 <span data-ttu-id="fe152-156">次のようなトランザクションがあるとします。</span><span class="sxs-lookup"><span data-stu-id="fe152-156">Consider the following transaction,</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  -- remove all rows from t3; the related read operation is performed under read committed   
  -- isolation, as this is the default for the transaction  
  delete from t3  
  
  -- copy the contents from t1 to t3; the read on t1 is performed under the serializable   
  -- isolation level  
  insert t3 select * from t1 (serializable)  
  
  -- compare t3 and t1; note: the result set may not be empty, as rows may have been added   
  -- by other transaction before this select, due to the read committed isolation level  
  select * from t3 except t1  
  
  -- compare t1 and t3; note: the result set is empty, as no rows have been added to t1   
  -- since its contents were copied to t1, due to the serializable isolation level  
  select * from t1 except t3  
commit  
```  
  
 <span data-ttu-id="fe152-157">このトランザクションでは、READ COMMITTED 分離で t3 からすべての行を削除し、SERIALIZABLE 分離で t1 からすべての行を t3 にコピーして、t1 と t3 を比較します。</span><span class="sxs-lookup"><span data-stu-id="fe152-157">This transaction deletes all rows from t3 under read committed isolation, copies all rows from t1 to t3 under serializable isolation, and then compares t1 and t3.</span></span> <span data-ttu-id="fe152-158">テーブルが空にされたので、一部の行 [t1 の行以外] が t3 に追加されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fe152-158">Some rows [not in t1] may have been added to t3 since the table was emptied.</span></span> <span data-ttu-id="fe152-159">コピーは SERIALIZABLE であったので、t1 には行は追加されていません。</span><span class="sxs-lookup"><span data-stu-id="fe152-159">No rows were added to t1 as the copy was serializable.</span></span>  
  
 <span data-ttu-id="fe152-160">トランザクションの終了時の t1 からの読み取りは構文的に READ COMMITTED で行われますが、同じ読み取りが SERIALIZABLE のトランザクションで前に実行されているので、この読み取りは効果的にシリアル化可能です。シリアル化可能性により、トランザクションの後続のどの時点で読み取りを実行しても、同じ行を返すことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-160">Although the read from t1 at the end of the transaction is syntactically read committed, it is effectively serializable, because the same read was performed earlier in the transaction under serializable isolation: serializability guarantees that if the read is performed at any later point in the transaction, the same rows are returned.</span></span>  
  
## <a name="cross-container-transactions-and-isolation-levels"></a><span data-ttu-id="fe152-161">複数コンテナーにまたがるトランザクションと分離レベル</span><span class="sxs-lookup"><span data-stu-id="fe152-161">Cross-Container Transactions and Isolation Levels</span></span>  
 <span data-ttu-id="fe152-162">複数コンテナーにまたがるトランザクションは、ディスクベースの側 (ディスクベーステーブルに対する操作の場合) とメモリ最適化側 (メモリ最適化テーブルでの操作の場合) という2つの側面を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="fe152-162">A cross-container transaction can be seen as having two sides: a disk-based side (for operations on disk-based tables) and a memory-optimized side (for operations on memory-optimized tables).</span></span> <span data-ttu-id="fe152-163">これら 2 つの側で分離レベルが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fe152-163">These two sides may have different isolation levels.</span></span> <span data-ttu-id="fe152-164">実際に、それぞれの側での個々の読み取り操作で分離レベルが異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="fe152-164">In fact, individual read operations on each side may have different isolation levels.</span></span>  
  
 <span data-ttu-id="fe152-165">特定のトランザクション T のディスク ベース側は、次の条件のいずれかに一致する場合、特定の分離レベル X に達します。</span><span class="sxs-lookup"><span data-stu-id="fe152-165">The disk-based side of a given transaction T reaches a certain isolation level X if one of the following conditions is met:</span></span>  
  
-   <span data-ttu-id="fe152-166">X で開始します。つまり、セッションの既定値は X で、実行したか、 `SET TRANSACTION ISOLATION LEVEL` [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 既定値です。</span><span class="sxs-lookup"><span data-stu-id="fe152-166">It starts in X. That is, the session default was X, either because you executed `SET TRANSACTION ISOLATION LEVEL`, or it is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] default.</span></span>  
  
-   <span data-ttu-id="fe152-167">トランザクションの実行中に、`SET TRANSACTION ISOLATION LEVEL` を使用して、既定の分離レベルが X に変更されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-167">During the transaction, the default isolation level is changed to X using `SET TRANSACTION ISOLATION LEVEL`.</span></span>  
  
-   <span data-ttu-id="fe152-168">ディスク ベース テーブルに対する読み取り操作が、構文 `WITH (X)` を使用して、分離レベル X で実行されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-168">A read operation on a disk-based table is executed under isolation level X, using the syntax `WITH (X)`.</span></span>  
  
 <span data-ttu-id="fe152-169">T の実行中に、メモリ最適化テーブルに対する任意の読み取り操作、または任意のネイティブ コンパイル ストアド プロシージャが分離レベル Y で実行された場合、T のメモリ最適化側は分離レベル Y に達します。</span><span class="sxs-lookup"><span data-stu-id="fe152-169">The memory-optimized side of T reaches an isolation level Y if during execution of T, any read operation on a memory-optimized table or any natively compiled stored procedure is executed under isolation level Y.</span></span>  
  
 <span data-ttu-id="fe152-170">次のトランザクションを例として考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="fe152-170">Consider the following transaction as an example.</span></span> <span data-ttu-id="fe152-171">ここで、t1 と t2 はディスク ベース テーブル、t3 と t4 はメモリ最適化テーブルです。</span><span class="sxs-lookup"><span data-stu-id="fe152-171">Here, t1 and t2 are disk-based tables and t3 and t4 are memory-optimized tables.</span></span>  
  
 <span data-ttu-id="fe152-172">トランザクションのディスク ベース側は READ COMMITTED 分離レベルに達します。これは、開始時のレベルが READ COMMITTED であるためです。</span><span class="sxs-lookup"><span data-stu-id="fe152-172">The disk-based side of the transaction reaches the isolation level read committed, because it starts in that level.</span></span> <span data-ttu-id="fe152-173">また、ディスク ベース側は REPEATABLE READ にも達します。これは、最初の読み取り操作が REPEATABLE READ で実行されるためです。</span><span class="sxs-lookup"><span data-stu-id="fe152-173">The disk-based side also reaches repeatable read, because the first read operation is executed under that isolation level.</span></span> <span data-ttu-id="fe152-174">トランザクションの終了時の削除は READ COMMITTED 分離レベルで実行され、新しい分離レベルの導入はありません。</span><span class="sxs-lookup"><span data-stu-id="fe152-174">The delete at the end of the transaction is executed under read committed isolation level, and so does not introduce a new isolation level.</span></span>  
  
 <span data-ttu-id="fe152-175">トランザクションのメモリ最適化側は、次の2つのレベルのいずれかに到達できます。 condition1 が true の場合は、シリアル化可能な状態になりますが、false の場合、メモリ最適化側はスナップショット分離にのみ到達します。</span><span class="sxs-lookup"><span data-stu-id="fe152-175">The memory-optimized side of the transaction can reach one of two levels: if condition1 is true, it reaches serializable, while if it is false, the memory-optimized side reaches only snapshot isolation.</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  select * from t1 (repeatableread)  
  
  if condition1 begin  
    insert t3 select * from t4 (serializable)  
  end  
  else begin  
    insert t3 select * from t4 (snapshot)  
  end  
  
  delete from t1  
commit  
```  
  
### <a name="supported-isolation-levels-for-cross-container-transactions"></a><span data-ttu-id="fe152-176">複数コンテナーにまたがるトランザクションでサポートされる分離レベル</span><span class="sxs-lookup"><span data-stu-id="fe152-176">Supported Isolation Levels for Cross-Container Transactions</span></span>  
 <span data-ttu-id="fe152-177">複数コンテナーにまたがるトランザクションでは、メモリ最適化テーブルでの操作に使用される分離レベルに制限があります。</span><span class="sxs-lookup"><span data-stu-id="fe152-177">There are limitations on the isolation levels used with operations on memory-optimized tables in cross-container transactions.</span></span>  
  
 <span data-ttu-id="fe152-178">メモリ最適化テーブルは、SNAPSHOT、REPEATABLE READ、および SERIALIZABLE の各分離レベルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="fe152-178">Memory-optimized tables support the isolation levels SNAPSHOT, REPEATABLE READ, and SERIALIZABLE.</span></span> <span data-ttu-id="fe152-179">自動コミット トランザクションの場合、メモリ最適化テーブルは READ COMMITTED 分離レベルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="fe152-179">For autocommit transactions, memory-optimized tables support the isolation level READ COMMITTED.</span></span>  
  
 <span data-ttu-id="fe152-180">次のシナリオがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="fe152-180">The following scenarios are supported:</span></span>  
  
-   <span data-ttu-id="fe152-181">READ UNCOMMITTED、READ COMMITTED、および READ_COMMITTED_SNAPSHOT の複数コンテナーにまたがるトランザクションは、SNAPSHOT、REPEATABLE READ、および SERIALIZABLE の各分離でメモリ最適化テーブルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="fe152-181">READ UNCOMMITTED, READ COMMITTED, and READ_COMMITTED_SNAPSHOT cross-container transactions can access memory-optimized tables under SNAPSHOT, REPEATABLE READ, and SERIALIZABLE isolation.</span></span> <span data-ttu-id="fe152-182">READ COMMITTED の保証はトランザクションに対して保持されます。トランザクションで読み取られたすべての行がデータベースにコミットされています。</span><span class="sxs-lookup"><span data-stu-id="fe152-182">The READ COMMITTED guarantee holds for the transaction; all rows read by the transaction have been committed to the database.</span></span>  
  
-   <span data-ttu-id="fe152-183">REPEATABLE READ および SERIALIZABLE のトランザクションは、SNAPSHOT 分離でメモリ最適化テーブルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="fe152-183">REPEATABLE READ and SERIALIZABLE transactions can access memory-optimized tables under SNAPSHOT isolation.</span></span>  
  
## <a name="read-only-cross-container-transactions"></a><span data-ttu-id="fe152-184">読み取り専用の複数コンテナーにまたがるトランザクション</span><span class="sxs-lookup"><span data-stu-id="fe152-184">Read-only Cross-Container Transactions</span></span>  
 <span data-ttu-id="fe152-185">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のほとんどの読み取り専用トランザクションは、コミット時にロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="fe152-185">Most read-only transactions in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are rolled back at commit time.</span></span> <span data-ttu-id="fe152-186">データベースにコミットされる変更がないため、システムはトランザクションによって使用されるリソースを単純に解放します。</span><span class="sxs-lookup"><span data-stu-id="fe152-186">Because there are no changes to commit to the database, the system simply frees the resources used by the transaction.</span></span> <span data-ttu-id="fe152-187">読み取り専用のディスク ベース トランザクションの場合、トランザクションによって使用されるロックはこの時点ですべて解放されます。</span><span class="sxs-lookup"><span data-stu-id="fe152-187">For read-only disk-based transactions, all locks taken by the transaction are released at this time.</span></span> <span data-ttu-id="fe152-188">ネイティブ コンパイル プロシージャの 1 回の実行全体での読み取り専用のメモリ最適化トランザクションの場合、検証は実行されません。</span><span class="sxs-lookup"><span data-stu-id="fe152-188">For read-only memory-optimized transactions that span a single natively compiled procedure execution, no validation is performed.</span></span>  
  
 <span data-ttu-id="fe152-189">自動コミット モードの複数コンテナーにまたがる読み取り専用トランザクションは、トランザクションの終了時に単純にロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="fe152-189">Cross-container, read-only transactions in autocommit mode are simply rolled back at the end of the transaction.</span></span> <span data-ttu-id="fe152-190">検証が実行されません。</span><span class="sxs-lookup"><span data-stu-id="fe152-190">No validation is performed.</span></span>  
  
 <span data-ttu-id="fe152-191">明示的または暗黙的な複数コンテナーにまたがる読み取り専用トランザクションでは、REPEATABLE READ 分離または SERIALIZABLE 分離でメモリ最適化テーブルにアクセスする場合、コミット時に検証を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe152-191">Explicit or implicit cross-container, read-only transactions perform validation at commit time if the transaction accesses memory-optimized tables under REPEATABLE READ or SERIALIZABLE isolation.</span></span> <span data-ttu-id="fe152-192">検証の詳細については、「[メモリ最適化テーブルのトランザクション](../relational-databases/in-memory-oltp/memory-optimized-tables.md)での競合の検出、検証、コミットの依存関係のチェック」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe152-192">For details about validation see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe152-193">参照</span><span class="sxs-lookup"><span data-stu-id="fe152-193">See Also</span></span>  
 <span data-ttu-id="fe152-194">[メモリ最適化テーブルのトランザクションについて](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="fe152-194">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="fe152-195">[メモリ最適化テーブルを使用したトランザクション分離レベルのガイドライン](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="fe152-195">[Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="fe152-196">メモリ最適化テーブルでのトランザクションの再試行ロジックのガイドライン</span><span class="sxs-lookup"><span data-stu-id="fe152-196">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  
