---
title: Transact-SQL によるインメモリ OLTP のサポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: rothja
ms.author: jroth
ms.openlocfilehash: bf3708a258e3bb97231e45b10bea2c59351a06a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740977"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a><span data-ttu-id="a35f6-102">Transact-SQL によるインメモリ OLTP のサポート</span><span class="sxs-lookup"><span data-stu-id="a35f6-102">Transact-SQL Support for In-Memory OLTP</span></span>
  <span data-ttu-id="a35f6-103">Transact-SQL クエリまたは DML ステートメント (SELECT、INSERT、UPDATE、または DELETE)、アドホック ステートメント、および SQL モジュール (ストアド プロシージャ、テーブル-値関数、スカラー関数、トリガー、ビューなど) を使用して、メモリ最適化テーブルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a35f6-103">You can access memory-optimized tables using any Transact-SQL query or DML statement (SELECT, INSERT, UPDATE, or DELETE), ad hoc statement, and SQL module such as stored procedures, table-value functions, scalar functions, triggers, and views.</span></span> <span data-ttu-id="a35f6-104">詳細については、「解釈された[Transact-sql を使用したメモリ最適化テーブルへのアクセス](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a35f6-104">For more information see [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).</span></span>  
  
 <span data-ttu-id="a35f6-105">メモリ最適化テーブルのみを参照するストアド プロシージャは、マシン コードにネイティブ コンパイルできます。これにより、一般に、インタープリタ式の (ディスク ベースの) ストアド プロシージャよりも大幅に高いパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="a35f6-105">Stored procedures that only reference memory-optimized tables can be natively compiled into machine code and typically provide significant performance gains over interpreted (disk-based) stored procedures.</span></span> <span data-ttu-id="a35f6-106">メモリ最適化テーブル アクセスを最適化するには、ネイティブ コンパイル ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="a35f6-106">For optimized access to memory-optimized tables use natively compiled stored procedures.</span></span> <span data-ttu-id="a35f6-107">詳細については、次を参照してください。 [ネイティブ コンパイル ストアド プロシージャ](natively-compiled-stored-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="a35f6-107">For more information, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="a35f6-108">データベース オブジェクト (DDL ステートメント) を作成および変更する場合に、次のステートメントが修正されました。</span><span class="sxs-lookup"><span data-stu-id="a35f6-108">When creating and modifying database objects (DDL statements), the following statements have been modified:</span></span>  
  
-   <span data-ttu-id="a35f6-109">[Transact-sql&#41;&#40;の ALTER database の File および Filegroup オプション](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)(「」を参照 `MEMORY_OPTIMIZED_DATA` )</span><span class="sxs-lookup"><span data-stu-id="a35f6-109">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (see `MEMORY_OPTIMIZED_DATA`)</span></span>  
  
-   <span data-ttu-id="a35f6-110">[Transact-sql&#41;SQL Server のデータベース &#40;の作成](/sql/t-sql/statements/create-database-sql-server-transact-sql)(「」を参照 `MEMORY_OPTIMIZED_DATA` )</span><span class="sxs-lookup"><span data-stu-id="a35f6-110">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) (see `MEMORY_OPTIMIZED_DATA`)</span></span>  
  
-   <span data-ttu-id="a35f6-111">[Transact-sql&#41;&#40;プロシージャを作成する](/sql/t-sql/statements/create-procedure-transact-sql)(「」、「」、「」、「」、「」、「」を参照 `NATIVE_COMPILATION` `SCHEMABINDING` `EXECUTE AS` `BEGIN ATOMIC` )</span><span class="sxs-lookup"><span data-stu-id="a35f6-111">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) (see `NATIVE_COMPILATION`, `SCHEMABINDING`, `EXECUTE AS`, and `BEGIN ATOMIC`)</span></span>  
  
-   <span data-ttu-id="a35f6-112">[Transact-sql&#41;を CREATE TABLE &#40;](/sql/t-sql/statements/create-table-transact-sql) (「」、「」、「」、「」、「」、「」、および「」を参照 `MEMORY_OPTIMIZED` `DURABILITY` `BUCKET_COUNT` `INDEX` `HASH` )</span><span class="sxs-lookup"><span data-stu-id="a35f6-112">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) (see `MEMORY_OPTIMIZED`, `DURABILITY`, `BUCKET_COUNT`, `INDEX`, and `HASH`)</span></span>  
  
-   <span data-ttu-id="a35f6-113">[Transact-sql&#41;&#40;型を作成する](/sql/t-sql/statements/create-type-transact-sql)(「」、「」、「」、「」、「」、「」を参照 `MEMORY_OPTIMIZED` `BUCKET_COUNT` `INDEX` `HASH` )</span><span class="sxs-lookup"><span data-stu-id="a35f6-113">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) (see `MEMORY_OPTIMIZED`, `BUCKET_COUNT`, `INDEX`, and `HASH`)</span></span>  
  
-   <span data-ttu-id="a35f6-114">[ @local_variable Transact-sql&#41;の &#40;宣言](/sql/t-sql/language-elements/declare-local-variable-transact-sql)(「」を参照 `NULL`  |  `NOT NULL` )</span><span class="sxs-lookup"><span data-stu-id="a35f6-114">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (see `NULL` | `NOT NULL`)</span></span>  
  
 <span data-ttu-id="a35f6-115">メモリ最適化テーブルは、`PRIMARY KEY` および `NOT NULL` の制約をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a35f6-115">Memory-optimized tables support `PRIMARY KEY` and `NOT NULL` constraints.</span></span> <span data-ttu-id="a35f6-116">サポートされていない制約の実装の詳細については、「 [Check 制約と Foreign Key 制約の移行](../../database-engine/migrating-check-and-foreign-key-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a35f6-116">For information on implementing unsupported constraints, see [Migrating Check and Foreign Key Constraints](../../database-engine/migrating-check-and-foreign-key-constraints.md).</span></span>  
  
 <span data-ttu-id="a35f6-117">サポートされていない機能の詳細については、「[インメモリ OLTP でサポートされていない Transact-SQL の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a35f6-117">For information on unsupported features, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a35f6-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a35f6-118">In This Section</span></span>  
  
-   [<span data-ttu-id="a35f6-119">サポートされるデータ型</span><span class="sxs-lookup"><span data-stu-id="a35f6-119">Supported Data Types</span></span>](supported-data-types-for-in-memory-oltp.md)  
  
-   [<span data-ttu-id="a35f6-120">解釈された Transact-SQL を使用したメモリ最適化テーブルへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a35f6-120">Accessing Memory-Optimized Tables Using Interpreted Transact-SQL</span></span>](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [<span data-ttu-id="a35f6-121">インメモリ OLTP 向けのシステム ビュー、ストアド プロシージャ、DMV、待機の種類</span><span class="sxs-lookup"><span data-stu-id="a35f6-121">System Views, Stored Procedures, DMVs and Wait Types for In-Memory OLTP</span></span>](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a><span data-ttu-id="a35f6-122">参照</span><span class="sxs-lookup"><span data-stu-id="a35f6-122">See Also</span></span>  
 <span data-ttu-id="a35f6-123">[インメモリ OLTP &#40;インメモリ最適化&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="a35f6-123">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 <span data-ttu-id="a35f6-124">[ネイティブ コンパイル ストアド プロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a35f6-124">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 <span data-ttu-id="a35f6-125">[サポートされている SQL Server 機能](unsupported-sql-server-features-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="a35f6-125">[Supported SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md) </span></span>  
 [<span data-ttu-id="a35f6-126">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a35f6-126">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
