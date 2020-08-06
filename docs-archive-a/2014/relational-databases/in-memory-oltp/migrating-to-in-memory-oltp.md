---
title: インメモリ OLTP への移行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 405cdac5-a0d4-47a4-9180-82876b773b82
author: rothja
ms.author: jroth
ms.openlocfilehash: ed764ce52d41d76667213b846cec51b26f634a27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742093"
---
# <a name="migrating-to-in-memory-oltp"></a><span data-ttu-id="3abe6-102">インメモリ OLTP への移行</span><span class="sxs-lookup"><span data-stu-id="3abe6-102">Migrating to In-Memory OLTP</span></span>
  <span data-ttu-id="3abe6-103">このセクションでは、データベース オブジェクトを移行してインメモリ OLTP を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3abe6-103">This section discusses how to migrate database objects to use In-Memory OLTP.</span></span>  
  
-   [<span data-ttu-id="3abe6-104">テーブルまたはストアド プロシージャをインメモリ OLTP に移植する必要があるかどうかの確認</span><span class="sxs-lookup"><span data-stu-id="3abe6-104">Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP</span></span>](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)  
  
-   [<span data-ttu-id="3abe6-105">メモリ最適化アドバイザー</span><span class="sxs-lookup"><span data-stu-id="3abe6-105">Memory Optimization Advisor</span></span>](memory-optimization-advisor.md)  
  
-   [<span data-ttu-id="3abe6-106">ネイティブ コンパイル アドバイザー</span><span class="sxs-lookup"><span data-stu-id="3abe6-106">Native Compilation Advisor</span></span>](native-compilation-advisor.md)  
  
-   [<span data-ttu-id="3abe6-107">インメモリ OLTP でサポートされていない Transact-SQL の構造</span><span class="sxs-lookup"><span data-stu-id="3abe6-107">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
-   [<span data-ttu-id="3abe6-108">メモリ最適化テーブルへの LOB 列の実装</span><span class="sxs-lookup"><span data-stu-id="3abe6-108">Implementing LOB Columns in a Memory-Optimized Table</span></span>](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)  
  
-   [<span data-ttu-id="3abe6-109">メモリ最適化テーブルへの SQL_VARIANT の実装</span><span class="sxs-lookup"><span data-stu-id="3abe6-109">Implementing SQL_VARIANT in a Memory-Optimized Table</span></span>](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
-   [<span data-ttu-id="3abe6-110">ネイティブ コンパイル ストアド プロシージャの移行に関する問題</span><span class="sxs-lookup"><span data-stu-id="3abe6-110">Migration Issues for Natively Compiled Stored Procedures</span></span>](migration-issues-for-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="3abe6-111">計算列の移行</span><span class="sxs-lookup"><span data-stu-id="3abe6-111">Migrating Computed Columns</span></span>](migrating-computed-columns.md)  
  
-   [<span data-ttu-id="3abe6-112">トリガーの移行</span><span class="sxs-lookup"><span data-stu-id="3abe6-112">Migrating Triggers</span></span>](migrating-triggers.md)  
  
-   [<span data-ttu-id="3abe6-113">複数データベースにまたがるクエリ</span><span class="sxs-lookup"><span data-stu-id="3abe6-113">Cross-Database Queries</span></span>](cross-database-queries.md)  
  
-   [<span data-ttu-id="3abe6-114">CHECK 制約と外部キー制約の移行</span><span class="sxs-lookup"><span data-stu-id="3abe6-114">Migrating Check and Foreign Key Constraints</span></span>](../../database-engine/migrating-check-and-foreign-key-constraints.md)  
  
-   [<span data-ttu-id="3abe6-115">メモリ最適化テーブルへの IDENTITY の実装</span><span class="sxs-lookup"><span data-stu-id="3abe6-115">Implementing IDENTITY in a Memory-Optimized Table</span></span>](implementing-identity-in-a-memory-optimized-table.md)  
  
 <span data-ttu-id="3abe6-116">移行方法については、「[In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx)」(インメモリ OLTP - 一般的なワークロード パターンと移行に関する考慮事項) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3abe6-116">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3abe6-117">参照</span><span class="sxs-lookup"><span data-stu-id="3abe6-117">See Also</span></span>  
 <span data-ttu-id="3abe6-118">[インメモリ OLTP &#40;インメモリ最適化&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="3abe6-118">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 [<span data-ttu-id="3abe6-119">メモリ最適化テーブルのメモリ必要量の推定</span><span class="sxs-lookup"><span data-stu-id="3abe6-119">Estimate Memory Requirements for Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
