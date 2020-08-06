---
title: メモリ最適化テーブルでのトランザクションの再試行ロジックのガイドライン |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2a35c37-4449-49ee-8bba-928028f1de66
author: stevestein
ms.author: sstein
ms.openlocfilehash: c9ffaccefb8d4e0a3044c4858a06029fd4350354
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716609"
---
# <a name="guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables"></a><span data-ttu-id="34b71-102">メモリ最適化テーブルでのトランザクションの再試行ロジックのガイドライン</span><span class="sxs-lookup"><span data-stu-id="34b71-102">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>
  <span data-ttu-id="34b71-103">メモリ最適化テーブルにアクセスするトランザクションに発生するエラー条件にはさまざまなものがあります。</span><span class="sxs-lookup"><span data-stu-id="34b71-103">There are error conditions that occur with transactions that access memory-optimized tables.</span></span>  
  
-   41302. <span data-ttu-id="34b71-104">現在のトランザクションが、トランザクションが開始してから更新されたレコードを更新しようとしました。</span><span class="sxs-lookup"><span data-stu-id="34b71-104">The current transaction attempted to update a record that has been updated since the transaction started.</span></span>  
  
-   41305. <span data-ttu-id="34b71-105">現在のトランザクションは、REPEATABLE READ の検証の失敗が原因でコミットされませんでした。</span><span class="sxs-lookup"><span data-stu-id="34b71-105">The current transaction failed to commit due to a repeatable read validation failure.</span></span>  
  
-   41325. <span data-ttu-id="34b71-106">現在のトランザクションは、SERIALIZABLE の検証の失敗が原因でコミットされませんでした。</span><span class="sxs-lookup"><span data-stu-id="34b71-106">The current transaction failed to commit due to a serializable validation failure.</span></span>  
  
-   41301. <span data-ttu-id="34b71-107">現在のトランザクションが依存している前のトランザクションが中止されたため、現在のトランザクションはコミットできません。</span><span class="sxs-lookup"><span data-stu-id="34b71-107">A previous transaction that the current transaction took a dependency on has aborted, and the current transaction can no longer commit.</span></span>  
  
 <span data-ttu-id="34b71-108">このようなエラーの原因としてよくあるのが、同時に実行されたトランザクションの間の競合です。</span><span class="sxs-lookup"><span data-stu-id="34b71-108">A common cause of these errors is interference between concurrently executing transaction.</span></span> <span data-ttu-id="34b71-109">一般的な対処方法は、トランザクションを再試行するというものです。</span><span class="sxs-lookup"><span data-stu-id="34b71-109">The common corrective action is to retry the transaction.</span></span>  
  
 <span data-ttu-id="34b71-110">これらのエラー状態の詳細については、「[メモリ最適化テーブルのトランザクション](../relational-databases/in-memory-oltp/memory-optimized-tables.md)での競合の検出、検証、コミットの依存関係のチェック」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34b71-110">For more information about these error conditions, see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="34b71-111">デッドロック (エラー コード 1205) は、メモリ最適化テーブルでは発生しません。</span><span class="sxs-lookup"><span data-stu-id="34b71-111">Deadlocks (error code 1205) cannot occur for memory-optimized tables.</span></span> <span data-ttu-id="34b71-112">メモリ最適化テーブルではロックを使用しません。</span><span class="sxs-lookup"><span data-stu-id="34b71-112">Locks are not used for memory-optimized tables.</span></span> <span data-ttu-id="34b71-113">ただし、アプリケーションに既にデッドロックに対する再試行ロジックが含まれている場合には、既存のロジックを拡張して新しいエラー コードを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="34b71-113">However, if the application already contains retry logic for deadlocks, the existing logic could be extended to include the new error codes.</span></span>  
  
## <a name="considerations-for-retrying"></a><span data-ttu-id="34b71-114">再試行に関する注意点</span><span class="sxs-lookup"><span data-stu-id="34b71-114">Considerations for Retrying</span></span>  
 <span data-ttu-id="34b71-115">アプリケーションでは通常、トランザクション間の競合が発生するため、その解決のために再試行ロジックを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34b71-115">Applications will typically encounter conflicts between transactions and need to implement retry logic to resolve those conflicts.</span></span> <span data-ttu-id="34b71-116">発生する競合の数は、要因の数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="34b71-116">The number of conflicts encountered depends on a number of factors:</span></span>  
  
-   <span data-ttu-id="34b71-117">個々の行の競合。</span><span class="sxs-lookup"><span data-stu-id="34b71-117">Contention for individual rows.</span></span> <span data-ttu-id="34b71-118">競合の可能性は、同じ行の更新を試みるトランザクションの数が増えるにつれて増加します。</span><span class="sxs-lookup"><span data-stu-id="34b71-118">The potential for conflicts increases as the number of transactions attempting to update the same row increases.</span></span>  
  
-   <span data-ttu-id="34b71-119">REPEATABLE READ トランザクションによって読み取られる行の数。</span><span class="sxs-lookup"><span data-stu-id="34b71-119">Number of rows read by REPEATABLE READ transactions.</span></span> <span data-ttu-id="34b71-120">読み取る行が増えるほど、その行のなかに同時実行トランザクションによって更新されるものがある可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="34b71-120">The more rows read, the greater the chance that some of these rows are updated by concurrent transactions.</span></span> <span data-ttu-id="34b71-121">このため、REPEATABLE READ 検証が失敗する原因になります。</span><span class="sxs-lookup"><span data-stu-id="34b71-121">This causes repeatable read validation failures.</span></span>  
  
-   <span data-ttu-id="34b71-122">SERIALIZABLE トランザクションで使用されるスキャン範囲の大きさ。</span><span class="sxs-lookup"><span data-stu-id="34b71-122">Size of the scan ranges used by SERIALIZABLE transactions.</span></span> <span data-ttu-id="34b71-123">スキャンの範囲が大きくなるほど、同時実行トランザクションによってファントム行が発生する可能性が高くなり、SERIALIZABLE 検証の失敗につながります。</span><span class="sxs-lookup"><span data-stu-id="34b71-123">The larger the scan ranges, the higher the chance that concurrent transactions will introduce phantom rows, causing serializable validation failures.</span></span>  
  
     <span data-ttu-id="34b71-124">アプリケーションでこのような競合が発生しないようにするのは難しいため、再試行ロジックが必要になります。</span><span class="sxs-lookup"><span data-stu-id="34b71-124">It is difficult for an application to avoid these conflicts, requiring retry logic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="34b71-125">メモリ最適化テーブルにアクセスする読み取り/書き込みトランザクションでは、再試行ロジックが必要です。</span><span class="sxs-lookup"><span data-stu-id="34b71-125">Read-write transactions that access memory-optimized tables require retry logic.</span></span>  
  
### <a name="considerations-for-read-only-transactions-and-natively-compiled-stored-procedures"></a><span data-ttu-id="34b71-126">読み取り専用トランザクションおよびネイティブ コンパイル ストアド プロシージャに関する注意点</span><span class="sxs-lookup"><span data-stu-id="34b71-126">Considerations for Read-Only Transactions and Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="34b71-127">ネイティブ コンパイル ストアド プロシージャを 1 回実行する読み取り専用トランザクションでは、REPEATABLE READ トランザクションおよび SERIALIZABLE トランザクションの検証は不要です。</span><span class="sxs-lookup"><span data-stu-id="34b71-127">Read-only transactions that span a single execution of a natively compiled stored procedure do not require validation for REPEATABLE READ and SERIALIZABLE transactions.</span></span> <span data-ttu-id="34b71-128">トランザクションが読み取り専用であれば、書き込みの競合は発生しません。</span><span class="sxs-lookup"><span data-stu-id="34b71-128">Write conflicts cannot occur due to a transaction being read-only.</span></span>  
  
 <span data-ttu-id="34b71-129">ただし、依存関係のエラーは発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="34b71-129">However, dependency failures can still occur.</span></span> <span data-ttu-id="34b71-130">依存関係のエラーは、競合に起因するエラーよりも発生の可能性は低いです。</span><span class="sxs-lookup"><span data-stu-id="34b71-130">Dependency failures are rarer than errors resulting from conflicts.</span></span> <span data-ttu-id="34b71-131">このため、ネイティブ コンパイル ストアド プロシージャを 1 回実行する読み取り専用トランザクションでは、多くの場合、特定の再試行ロジックは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="34b71-131">Therefore, in many cases, specific retry logic is not required for read-only transactions that span single executions of natively compiled stored procedures.</span></span>  
  
### <a name="considerations-for-read-only-transactions-and-cross-container-transactions"></a><span data-ttu-id="34b71-132">読み取り専用トランザクションと複数コンテナーにまたがるトランザクションに関する注意点</span><span class="sxs-lookup"><span data-stu-id="34b71-132">Considerations for Read-Only Transactions and Cross-Container Transactions</span></span>  
 <span data-ttu-id="34b71-133">読み取り専用で複数コンテナーにまたがるトランザクションは、ネイティブ コンパイル ストアド プロシージャのコンテキスト外で開始されるトランザクションであり、メモリ最適化テーブルがいずれも SNAPSHOT 分離下でアクセスされている場合には、検証を実行しません。</span><span class="sxs-lookup"><span data-stu-id="34b71-133">Read-only cross-container transactions, which are transactions that are started outside the context of a natively compiled stored procedure, do not perform validation if the memory-optimized tables are all accessed under SNAPSHOT isolation.</span></span> <span data-ttu-id="34b71-134">ただし、メモリ最適化テーブルが REPEATABLE READ または SERIALIZABLE 分離下でアクセスされている場合には、コミット時に検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="34b71-134">However, when memory-optimized tables are accessed under REPEATABLE READ or SERIALIZABLE isolation, validation is performed at commit time.</span></span> <span data-ttu-id="34b71-135">この場合、再試行ロジックが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="34b71-135">In this case, retry logic may be required.</span></span>  
  
 <span data-ttu-id="34b71-136">詳細については、「[トランザクション分離レベル](../../2014/database-engine/transaction-isolation-levels.md)のコンテナー間トランザクション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34b71-136">For more information, see the section on Cross-Container Transactions in [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).</span></span>  
  
## <a name="implementing-retry-logic"></a><span data-ttu-id="34b71-137">再試行ロジックの実装</span><span class="sxs-lookup"><span data-stu-id="34b71-137">Implementing Retry Logic</span></span>  
 <span data-ttu-id="34b71-138">メモリ最適化テーブルにアクセスするすべてのトランザクションと同様に、書き込みの競合 (エラー コード 41302) や依存関係の失敗 (エラー コード 41301) など、潜在的なエラーを処理するための再試行ロジックを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34b71-138">As with all transactions that access memory-optimized tables, you need to consider retry logic to handle potential failures, such as write conflicts (error code 41302) or dependency failures (error code 41301).</span></span> <span data-ttu-id="34b71-139">ほとんどのアプリケーションでは失敗率が低くなりますが、トランザクションの再試行によって問題に対処することが必要です。</span><span class="sxs-lookup"><span data-stu-id="34b71-139">In most applications the failure rate will be low, but it is still necessary to handle failures by retrying the transaction.</span></span> <span data-ttu-id="34b71-140">再試行ロジックを実装する 2 つの方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="34b71-140">Two suggested ways of implementing retry logic are:</span></span>  
  
-   <span data-ttu-id="34b71-141">クライアント側の再試行。</span><span class="sxs-lookup"><span data-stu-id="34b71-141">Client-side retries.</span></span> <span data-ttu-id="34b71-142">クライアント側の再試行は、一般的な事例で再試行ロジックを実装する方法としてお勧めします。</span><span class="sxs-lookup"><span data-stu-id="34b71-142">Client-side retries is the preferred way to implement retry logic in the general case.</span></span> <span data-ttu-id="34b71-143">クライアント アプリケーションは、トランザクションによってスローされたエラーをキャッチし、トランザクションを再試行します。</span><span class="sxs-lookup"><span data-stu-id="34b71-143">The client application catches the error thrown by the transaction, and retries the transaction.</span></span> <span data-ttu-id="34b71-144">既存のクライアント アプリケーションにデッドロックを処理する再試行ロジックがある場合は、新しいエラー コードを処理するようにアプリケーションを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="34b71-144">If an existing client application has retry logic to handle deadlocks, you can extend the application to handle the new error codes.</span></span>  
  
-   <span data-ttu-id="34b71-145">ラッパー ストアド プロシージャの使用。</span><span class="sxs-lookup"><span data-stu-id="34b71-145">Using a wrapper stored procedure.</span></span> <span data-ttu-id="34b71-146">クライアントは、ネイティブ コンパイル ストアド プロシージャを呼び出すかトランザクションを実行する、解釈された [!INCLUDE[tsql](../includes/tsql-md.md)] ストアド プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="34b71-146">The client calls an interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] stored procedure that calls the natively compiled stored procedure or executes the transaction.</span></span> <span data-ttu-id="34b71-147">その後、ラッパー プロシージャは、try/catch ロジックを使用し、エラーをキャッチして必要に応じてプロシージャ呼び出しを再試行します。</span><span class="sxs-lookup"><span data-stu-id="34b71-147">The wrapper procedure then uses try/catch logic to catch the error and retry the procedure call if needed.</span></span> <span data-ttu-id="34b71-148">障害発生前に結果がクライアントに返され、クライアントがその結果を破棄する方法がわからない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="34b71-148">It is possible that results are returned to the client before the failure, and the client would not know to discard them.</span></span> <span data-ttu-id="34b71-149">したがって、念のため、クライアントに結果セットを返さないネイティブ コンパイル ストアド プロシージャのみでこのメソッドを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="34b71-149">Therefore, to be safe, it is best to use this method only with natively compiled stored procedures that do not return any result sets to the client.</span></span>  
  
 <span data-ttu-id="34b71-150">再試行ロジックは、[!INCLUDE[tsql](../includes/tsql-md.md)] と中間層のアプリケーション コードのいずれかに実装できます。</span><span class="sxs-lookup"><span data-stu-id="34b71-150">The retry logic can be implemented either in [!INCLUDE[tsql](../includes/tsql-md.md)] or in the application code in the mid-tier.</span></span>  
  
 <span data-ttu-id="34b71-151">再試行ロジックを検討する理由には次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="34b71-151">Two possible reasons to consider the retry logic are:</span></span>  
  
-   <span data-ttu-id="34b71-152">クライアント アプリケーションには他のエラー コード (1205 など) についての再試行ロジックがあり、拡張することができるため。</span><span class="sxs-lookup"><span data-stu-id="34b71-152">The client application has retry logic for other error codes, such as 1205, which you can extend.</span></span>  
  
-   <span data-ttu-id="34b71-153">競合が発生するのはまれであり、準備実行によってエンド ツー エンドの待機時間を減らすことが重要であるため。</span><span class="sxs-lookup"><span data-stu-id="34b71-153">Conflicts are rare, and it is important to reduce end-to-end latency by using prepared execution.</span></span> <span data-ttu-id="34b71-154">ネイティブコンパイルストアドプロシージャを直接実行する方法の詳細については、「[ネイティブコンパイルストアドプロシージャ](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34b71-154">For more information about executing natively compiled stored procedures directly, see [Natively Compiled Stored Procedures](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="34b71-155">次のサンプルでは、ネイティブ コンパイル ストアド プロシージャまたは複数コンテナーにまたがるトランザクションへの呼び出しが含まれている [!INCLUDE[tsql](../includes/tsql-md.md)] の解釈されたストアド プロシージャの再試行ロジックを示します。</span><span class="sxs-lookup"><span data-stu-id="34b71-155">The following sample shows retry logic in an interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] stored procedure that contains a call either to a natively compiled stored procedure or to a cross-container transaction.</span></span>  
  
```sql  
CREATE PROCEDURE usp_my_procedure @param1 type1, @param2 type2, ...  
AS  
BEGIN  
  -- number of retries - tune based on the workload  
  DECLARE @retry INT = 10  
  
  WHILE (@retry > 0)  
  BEGIN  
    BEGIN TRY  
  
      -- exec usp_my_native_proc @param1, @param2, ...  
  
      --       or  
  
      -- BEGIN TRANSACTION  
      --   ...  
      -- COMMIT TRANSACTION  
  
      SET @retry = 0  
    END TRY  
    BEGIN CATCH  
      SET @retry -= 1  
  
      -- the error number for deadlocks (1205) does not need to be included for   
      -- transactions that do not access disk-based tables  
      IF (@retry > 0 AND error_number() in (41302, 41305, 41325, 41301, 1205))  
      BEGIN  
        -- these error conditions are transaction dooming - rollback the transaction  
        -- this is not needed if the transaction spans a single native proc execution  
        --   as the native proc will simply rollback when an error is thrown   
        IF XACT_STATE() = -1  
          ROLLBACK TRANSACTION  
  
        -- use a delay if there is a high rate of write conflicts (41302)  
        --   length of delay should depend on the typical duration of conflicting transactions  
        -- WAITFOR DELAY '00:00:00.001'  
      END  
      ELSE  
      BEGIN  
        -- insert custom error handling for other error conditions here  
  
        -- throw if this is not a qualifying error condition  
        ;THROW  
      END  
    END CATCH  
  END  
END  
```  
  
## <a name="see-also"></a><span data-ttu-id="34b71-156">参照</span><span class="sxs-lookup"><span data-stu-id="34b71-156">See Also</span></span>  
 <span data-ttu-id="34b71-157">[メモリ最適化テーブルのトランザクションについて](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="34b71-157">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="34b71-158">[メモリ最適化テーブルのトランザクション](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="34b71-158">[Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="34b71-159">メモリ最適化テーブルのトランザクション分離レベルに関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="34b71-159">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md)  
  
  
