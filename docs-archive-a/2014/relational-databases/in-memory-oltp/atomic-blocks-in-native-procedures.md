---
title: ATOMIC ブロック | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 40e0e749-260c-4cfc-a848-444d30c09d85
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ca8f5b4d767ef0fe836cd260f8d12dd5b40c75d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632463"
---
# <a name="atomic-blocks"></a><span data-ttu-id="1310f-102">ATOMIC ブロック</span><span class="sxs-lookup"><span data-stu-id="1310f-102">Atomic Blocks</span></span>
  <span data-ttu-id="1310f-103">`BEGIN ATOMIC` は、ANSI SQL 標準の一部です。</span><span class="sxs-lookup"><span data-stu-id="1310f-103">`BEGIN ATOMIC` is part of the ANSI SQL standard.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1310f-104">では、ネイティブ コンパイル ストアド プロシージャの最上位でのみ ATOMIC ブロックがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1310f-104">supports atomic blocks only at the top-level of natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="1310f-105">各ネイティブ コンパイル ストアド プロシージャには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが正確に 1 ブロックずつ含まれています。</span><span class="sxs-lookup"><span data-stu-id="1310f-105">Every natively compiled stored procedure contains exactly one block of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="1310f-106">これが ATOMIC ブロックです。</span><span class="sxs-lookup"><span data-stu-id="1310f-106">This is an ATOMIC block.</span></span>  
  
-   <span data-ttu-id="1310f-107">ネイティブでない、解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャおよびアドホック バッチでは、ATOMIC ブロックはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="1310f-107">Non-native, interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and ad hoc batches do not support atomic blocks.</span></span>  
  
 <span data-ttu-id="1310f-108">ATOMIC ブロックはトランザクション内部で (自動的に) 実行されます。</span><span class="sxs-lookup"><span data-stu-id="1310f-108">Atomic blocks are executed (atomically) within the transaction.</span></span> <span data-ttu-id="1310f-109">ブロック内のすべてのステートメントが成功するか、またはブロック全体がブロックの先頭で作成したセーブポイントまでロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="1310f-109">Either all statements in the block succeed or the entire block will be rolled back to the savepoint that was created at the start of the block.</span></span> <span data-ttu-id="1310f-110">また、ATOMIC ブロックのセッション設定は固定されています。</span><span class="sxs-lookup"><span data-stu-id="1310f-110">In addition, the session settings are fixed for the atomic block.</span></span> <span data-ttu-id="1310f-111">同じ ATOMIC ブロックを異なる設定のセッションで実行しても、現在のセッション設定とは関係なく動作は同じになります。</span><span class="sxs-lookup"><span data-stu-id="1310f-111">Executing the same atomic block in sessions with different settings will result in the same behavior, independent of the settings of the current session.</span></span>  
  
## <a name="transactions-and-error-handling"></a><span data-ttu-id="1310f-112">トランザクションとエラー処理</span><span class="sxs-lookup"><span data-stu-id="1310f-112">Transactions and Error Handling</span></span>  
 <span data-ttu-id="1310f-113">バッチによって `BEGIN TRANSACTION` ステートメントが実行されてトランザクションがアクティブな状態になっているため、トランザクションがセッションに存在する場合、ATOMIC ブロックの処理を開始するとトランザクションにセーブポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1310f-113">If a transaction already exists on a session (because a batch executed a `BEGIN TRANSACTION` statement and the transaction remains active), then starting an atomic block will create a savepoint in the transaction.</span></span> <span data-ttu-id="1310f-114">ブロックが例外なしで終了すると、ブロックに対して作成されたセーブポイントがコミットされますが、セッション レベルでコミットされるまでトランザクションはコミットされません。</span><span class="sxs-lookup"><span data-stu-id="1310f-114">If the block exits without an exception, the savepoint that was created for the block commits, but the transaction will not commit until the transaction at the session level commits.</span></span> <span data-ttu-id="1310f-115">ブロックで例外がスローされるとブロックの結果はロールバックされますが、例外によってトランザクションの失敗が決定的にならない限り、セッション レベルのトランザクションは続行されます。</span><span class="sxs-lookup"><span data-stu-id="1310f-115">If the block throws an exception, the effects of the block are rolled back but the transaction at the session level will proceed, unless the exception is transaction-dooming.</span></span> <span data-ttu-id="1310f-116">たとえば、書き込みの競合によってトランザクションの失敗は決定的になりますが、型キャスト エラーの場合はそうではありません。</span><span class="sxs-lookup"><span data-stu-id="1310f-116">For example a write conflict is transaction-dooming, but not a type casting error.</span></span>  
  
 <span data-ttu-id="1310f-117">セッションにアクティブなトランザクションがない場合、`BEGIN ATOMIC` は新しいトランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="1310f-117">If there is no active transaction on a session, `BEGIN ATOMIC` will start a new transaction.</span></span> <span data-ttu-id="1310f-118">ブロックのスコープ外でスローされる例外が存在しない場合、トランザクションはブロックの末尾でコミットされます。</span><span class="sxs-lookup"><span data-stu-id="1310f-118">If no exception is thrown outside the scope of the block, the transaction will be committed at the end of the block.</span></span> <span data-ttu-id="1310f-119">ブロックで例外がスローされた場合 (つまり、ブロック内で例外をキャッチして処理できなかった場合)、トランザクションはロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="1310f-119">If the block throws an exception (that is, the exception is not caught and handled within the block), the transaction will be rolled back.</span></span> <span data-ttu-id="1310f-120">1 つの ATOMIC ブロック (1 つのネイティブ コンパイル ストアド プロシージャ) 全体に及ぶトランザクションの場合、明示的に `BEGIN TRANSACTION` ステートメントと、`COMMIT` または `ROLLBACK` ステートメントを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1310f-120">For transactions that span a single atomic block (a single natively compiled stored procedure), you do not need to write explicit `BEGIN TRANSACTION` and `COMMIT` or `ROLLBACK` statements.</span></span>  
  
 <span data-ttu-id="1310f-121">ネイティブ コンパイル ストアド プロシージャは、エラー処理のために `TRY`、`CATCH`、および `THROW` の各構造をサポートします。</span><span class="sxs-lookup"><span data-stu-id="1310f-121">Natively compiled stored procedures support the `TRY`, `CATCH`, and `THROW` constructs for error handling.</span></span> <span data-ttu-id="1310f-122">`RAISERROR` がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1310f-122">`RAISERROR` is not supported.</span></span>  
  
 <span data-ttu-id="1310f-123">次の例は、ATOMIC ブロックおよびネイティブ コンパイル ストアド プロシージャでのエラー処理動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="1310f-123">The following example illustrates the error handling behavior with atomic blocks and natively compiled stored procedures:</span></span>  
  
```sql  
-- sample table  
CREATE TABLE dbo.t1 (  
  c1 int not null primary key nonclustered  
)  
WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- sample proc that inserts 2 rows  
CREATE PROCEDURE dbo.usp_t1 @v1 bigint not null, @v2 bigint not null  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC  
WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english', DELAYED_DURABILITY = ON)  
  
  INSERT dbo.t1 VALUES (@v1)  
  INSERT dbo.t1 VALUES (@v2)  
  
END  
GO  
  
-- insert two rows  
EXEC dbo.usp_t1 1, 2  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify the rows 1 and 2 were committed  
SELECT c1 FROM dbo.t1  
GO  
  
-- execute proc with arithmetic overflow  
EXEC dbo.usp_t1 3, 4444444444444  
GO  
-- expected error message:  
-- Msg 8115, Level 16, State 0, Procedure usp_t1  
-- Arithmetic overflow error converting bigint to data type int.  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 was not committed; usp_t1 has been rolled back  
SELECT c1 FROM dbo.t1  
GO  
  
-- start a new transaction  
BEGIN TRANSACTION  
  -- insert rows 3 and 4  
  EXEC dbo.usp_t1 3, 4  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify the rows 3 and 4 were inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
  -- catch the arithmetic overflow error  
  BEGIN TRY  
    EXEC dbo.usp_t1 5, 4444444444444  
  END TRY  
  BEGIN CATCH  
    PRINT N'Error occurred: ' + error_message()  
  END CATCH  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify rows 3 and 4 are still in the table, and row 5 has not been inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
COMMIT  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 and 4 has been committed  
SELECT c1 FROM dbo.t1  
ORDER BY c1  
GO  
```  
  
 <span data-ttu-id="1310f-124">メモリ最適化テーブルに固有の次のエラー メッセージは、トランザクションの失敗が決定的であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="1310f-124">The following error messages specific to memory-optimized tables are transaction dooming.</span></span> <span data-ttu-id="1310f-125">ATOMIC ブロックのスコープ内で、10772、41301、41302、41305、41325、41332、または 41333 のエラーが発生した場合、トランザクションは中止されます。</span><span class="sxs-lookup"><span data-stu-id="1310f-125">If they occur in the scope of an atomic block, they will cause the transaction to abort: 10772, 41301, 41302, 41305, 41325, 41332, and 41333.</span></span>  
  
## <a name="session-settings"></a><span data-ttu-id="1310f-126">セッションの設定</span><span class="sxs-lookup"><span data-stu-id="1310f-126">Session Settings</span></span>  
 <span data-ttu-id="1310f-127">ATOMIC ブロックのセッション設定は、ストアド プロシージャのコンパイル時に固定されます。</span><span class="sxs-lookup"><span data-stu-id="1310f-127">The session settings in atomic blocks are fixed when the stored procedure is compiled.</span></span> <span data-ttu-id="1310f-128">一部の設定は `BEGIN ATOMIC` で指定できますが、その他の設定は常に同じ値に固定されます。</span><span class="sxs-lookup"><span data-stu-id="1310f-128">Some settings can be specified with `BEGIN ATOMIC` while other settings are always fixed to the same value.</span></span>  
  
 <span data-ttu-id="1310f-129">`BEGIN ATOMIC` では以下のオプションは必須です。</span><span class="sxs-lookup"><span data-stu-id="1310f-129">The following options are required with `BEGIN ATOMIC`:</span></span>  
  
|<span data-ttu-id="1310f-130">必須の設定</span><span class="sxs-lookup"><span data-stu-id="1310f-130">Required Setting</span></span>|<span data-ttu-id="1310f-131">説明</span><span class="sxs-lookup"><span data-stu-id="1310f-131">Description</span></span>|  
|----------------------|-----------------|  
|`TRANSACTION ISOLATION LEVEL`|<span data-ttu-id="1310f-132">サポートされている値は、`SNAPSHOT`、`REPEATABLEREAD`、および `SERIALIZABLE` です。</span><span class="sxs-lookup"><span data-stu-id="1310f-132">Supported values are `SNAPSHOT`, `REPEATABLEREAD`, and `SERIALIZABLE`.</span></span>|  
|`LANGUAGE`|<span data-ttu-id="1310f-133">日付と時刻の形式とシステム メッセージが決まります。</span><span class="sxs-lookup"><span data-stu-id="1310f-133">Determines date and time formats and system messages.</span></span> <span data-ttu-id="1310f-134">[sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) のすべての言語とエイリアスがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1310f-134">All languages and aliases in [sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) are supported.</span></span>|  
  
 <span data-ttu-id="1310f-135">次の設定は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1310f-135">The following settings are optional:</span></span>  
  
|<span data-ttu-id="1310f-136">省略可能な設定</span><span class="sxs-lookup"><span data-stu-id="1310f-136">Optional Setting</span></span>|<span data-ttu-id="1310f-137">説明</span><span class="sxs-lookup"><span data-stu-id="1310f-137">Description</span></span>|  
|----------------------|-----------------|  
|`DATEFORMAT`|<span data-ttu-id="1310f-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべての日付形式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1310f-138">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date formats are supported.</span></span> <span data-ttu-id="1310f-139">指定した場合、`DATEFORMAT` は `LANGUAGE` に関連付けられた既定の日付形式をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="1310f-139">When specified, `DATEFORMAT` overrides the default date format associated with `LANGUAGE`.</span></span>|  
|`DATEFIRST`|<span data-ttu-id="1310f-140">指定した場合、`DATEFIRST` は `LANGUAGE` に関連付けられた既定値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="1310f-140">When specified, `DATEFIRST` overrides the default associated with `LANGUAGE`.</span></span>|  
|`DELAYED_DURABILITY`|<span data-ttu-id="1310f-141">サポートされる値は、`OFF` と `ON`。</span><span class="sxs-lookup"><span data-stu-id="1310f-141">Supported values are `OFF` and `ON`.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1310f-142">によるトランザクションのコミットには、完全持続性、既定値、または遅延持続性が適用されます。詳細については、「[Control Transaction Durability](../logs/control-transaction-durability.md)」 (トランザクションの持続性の制御) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1310f-142">transaction commits can be either fully durable, the default, or delayed durable.For more information, see [Control Transaction Durability](../logs/control-transaction-durability.md).</span></span>|  
  
 <span data-ttu-id="1310f-143">次の SET オプションには、すべてのネイティブ コンパイル ストアド プロシージャのすべての ATOMIC ブロックについて同じシステム既定値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="1310f-143">The following SET options have the same system default value for all atomic blocks in all natively compiled stored procedures:</span></span>  
  
|<span data-ttu-id="1310f-144">SET オプション</span><span class="sxs-lookup"><span data-stu-id="1310f-144">Set Option</span></span>|<span data-ttu-id="1310f-145">ATOMIC ブロックのシステム既定値</span><span class="sxs-lookup"><span data-stu-id="1310f-145">System Default for Atomic Blocks</span></span>|  
|----------------|--------------------------------------|  
|<span data-ttu-id="1310f-146">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="1310f-146">ANSI_NULLS</span></span>|<span data-ttu-id="1310f-147">ON</span><span class="sxs-lookup"><span data-stu-id="1310f-147">ON</span></span>|  
|<span data-ttu-id="1310f-148">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="1310f-148">ANSI_PADDING</span></span>|<span data-ttu-id="1310f-149">ON</span><span class="sxs-lookup"><span data-stu-id="1310f-149">ON</span></span>|  
|<span data-ttu-id="1310f-150">ANSI_WARNING</span><span class="sxs-lookup"><span data-stu-id="1310f-150">ANSI_WARNING</span></span>|<span data-ttu-id="1310f-151">ON</span><span class="sxs-lookup"><span data-stu-id="1310f-151">ON</span></span>|  
|<span data-ttu-id="1310f-152">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="1310f-152">ARITHABORT</span></span>|<span data-ttu-id="1310f-153">ON</span><span class="sxs-lookup"><span data-stu-id="1310f-153">ON</span></span>|  
|<span data-ttu-id="1310f-154">ARITHIGNORE</span><span class="sxs-lookup"><span data-stu-id="1310f-154">ARITHIGNORE</span></span>|<span data-ttu-id="1310f-155">OFF</span><span class="sxs-lookup"><span data-stu-id="1310f-155">OFF</span></span>|  
|<span data-ttu-id="1310f-156">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="1310f-156">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="1310f-157">ON</span><span class="sxs-lookup"><span data-stu-id="1310f-157">ON</span></span>|  
|<span data-ttu-id="1310f-158">IDENTITY_INSERT</span><span class="sxs-lookup"><span data-stu-id="1310f-158">IDENTITY_INSERT</span></span>|<span data-ttu-id="1310f-159">OFF</span><span class="sxs-lookup"><span data-stu-id="1310f-159">OFF</span></span>|  
|<span data-ttu-id="1310f-160">NOCOUNT</span><span class="sxs-lookup"><span data-stu-id="1310f-160">NOCOUNT</span></span>|<span data-ttu-id="1310f-161">ON</span><span class="sxs-lookup"><span data-stu-id="1310f-161">ON</span></span>|  
|<span data-ttu-id="1310f-162">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="1310f-162">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="1310f-163">OFF</span><span class="sxs-lookup"><span data-stu-id="1310f-163">OFF</span></span>|  
|<span data-ttu-id="1310f-164">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="1310f-164">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="1310f-165">ON</span><span class="sxs-lookup"><span data-stu-id="1310f-165">ON</span></span>|  
|<span data-ttu-id="1310f-166">ROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="1310f-166">ROWCOUNT</span></span>|<span data-ttu-id="1310f-167">0</span><span class="sxs-lookup"><span data-stu-id="1310f-167">0</span></span>|  
|<span data-ttu-id="1310f-168">TEXTSIZE</span><span class="sxs-lookup"><span data-stu-id="1310f-168">TEXTSIZE</span></span>|<span data-ttu-id="1310f-169">0</span><span class="sxs-lookup"><span data-stu-id="1310f-169">0</span></span>|  
|<span data-ttu-id="1310f-170">XACT_ABORT</span><span class="sxs-lookup"><span data-stu-id="1310f-170">XACT_ABORT</span></span>|<span data-ttu-id="1310f-171">OFF</span><span class="sxs-lookup"><span data-stu-id="1310f-171">OFF</span></span><br /><br /> <span data-ttu-id="1310f-172">処理できない例外により ATOMIC ブロックはロールバックされますが、そのエラーが致命的でない限りトランザクションは中止されません。</span><span class="sxs-lookup"><span data-stu-id="1310f-172">Uncaught exceptions cause the atomic block to roll back, but not cause the transaction to abort unless the error is transaction dooming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1310f-173">参照</span><span class="sxs-lookup"><span data-stu-id="1310f-173">See Also</span></span>  
 [<span data-ttu-id="1310f-174">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1310f-174">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
