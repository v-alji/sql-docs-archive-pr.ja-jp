---
title: メモリ最適化テーブルのトランザクションについて |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 06075248-705e-4563-9371-b64cd609793c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0671bba8b7a0bda27ea27cf059cb9e3b1bb87b2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716570"
---
# <a name="understanding-transactions-on-memory-optimized-tables"></a><span data-ttu-id="c83c8-102">メモリ最適化テーブルを対象にするトランザクションについて</span><span class="sxs-lookup"><span data-stu-id="c83c8-102">Understanding Transactions on Memory-Optimized Tables</span></span>
  <span data-ttu-id="c83c8-103">トランザクションでは、複数のバージョンから成るオプティミスティック コンカレンシーを使用して、メモリ最適化テーブルにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="c83c8-103">Transactions access memory-optimized tables using a form of optimistic, multi-version concurrency control.</span></span> <span data-ttu-id="c83c8-104">これは、データに異なるバージョンがあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c83c8-104">This means that there are different versions of the data.</span></span> <span data-ttu-id="c83c8-105">各トランザクションでは、他の同時実行トランザクションから独立して、トランザクション上の一貫性のある固有のバージョンのデータベースを処理します。</span><span class="sxs-lookup"><span data-stu-id="c83c8-105">Each transaction operates on its own transactionally consistent version of the database, independent from other concurrently running transactions.</span></span> <span data-ttu-id="c83c8-106">また、トランザクションは、他の同時実行トランザクションとの競合がないというオプティミスティックな仮定の下で行われます。</span><span class="sxs-lookup"><span data-stu-id="c83c8-106">In addition, transactions operate under the optimistic assumption that there will be no conflicts with other, concurrent, transactions.</span></span> <span data-ttu-id="c83c8-107">これにより、ロックを使用する必要はなくなりますが、システムで競合を検出して競合状態のトランザクションの一方を終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c83c8-107">This avoids the need to use locks, but does require the system to detect conflicts and terminate one of the conflicting transactions.</span></span> <span data-ttu-id="c83c8-108">競合は書き込み - 書き込みトランザクションおよび読み取り - 書き込みトランザクションのみで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c83c8-108">Conflicts can occur only for write-write transactions and for read-write transactions.</span></span> <span data-ttu-id="c83c8-109">書き込み - 書き込みが競合する場合、1 つの書き込みトランザクションが終了します。</span><span class="sxs-lookup"><span data-stu-id="c83c8-109">If there is a write-write conflict, one write transaction is terminated.</span></span>  
  
 <span data-ttu-id="c83c8-110">メモリ最適化テーブルのコンカレンシー制御と、READ_COMMITTED_SNAPSHOT および SNAPSHOT のトランザクション分離レベルを対象とするディスク ベース テーブルのコンカレンシー制御には類似点があります。</span><span class="sxs-lookup"><span data-stu-id="c83c8-110">There are similarities between the concurrency control for memory-optimized tables and the concurrency control for disk-based tables for the READ_COMMITTED_SNAPSHOT and SNAPSHOT transaction isolation levels.</span></span> <span data-ttu-id="c83c8-111">(ディスクベーステーブルの詳細については、「[データベースエンジンでの行のバージョン管理に基づく分離レベル](https://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="c83c8-111">(For more information about disk-based tables, see [Row Versioning-based Isolation Levels in the Database Engine](https://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx).)</span></span>  
  
## <a name="topics-in-this-section"></a><span data-ttu-id="c83c8-112">このセクションのトピック</span><span class="sxs-lookup"><span data-stu-id="c83c8-112">Topics in This Section</span></span>  
 <span data-ttu-id="c83c8-113">ここでは、次のトピックを含め、メモリ最適化テーブルのトランザクションを取り扱います。</span><span class="sxs-lookup"><span data-stu-id="c83c8-113">This section on transactions in memory-optimized tables includes the following topics:</span></span>  
  
-   [<span data-ttu-id="c83c8-114">メモリ最適化テーブルのトランザクション分離レベルに関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="c83c8-114">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
-   [<span data-ttu-id="c83c8-115">メモリ最適化テーブルでのトランザクションの再試行ロジックのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c83c8-115">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>](guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="c83c8-116">メモリ最適化テーブルでのトランザクション</span><span class="sxs-lookup"><span data-stu-id="c83c8-116">Transactions in Memory-Optimized Tables</span></span>](transactions-in-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="c83c8-117">トランザクション分離レベル</span><span class="sxs-lookup"><span data-stu-id="c83c8-117">Transaction Isolation Levels</span></span>](transaction-isolation-levels.md)  
  
-   [<span data-ttu-id="c83c8-118">複数コンテナーにまたがるトランザクション</span><span class="sxs-lookup"><span data-stu-id="c83c8-118">Cross-Container Transactions</span></span>](cross-container-transactions.md)  
  
 <span data-ttu-id="c83c8-119">詳しくは、「[トランザクションの持続性の制御](../relational-databases/logs/control-transaction-durability.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c83c8-119">For more information, see [Control Transaction Durability](../relational-databases/logs/control-transaction-durability.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83c8-120">参照</span><span class="sxs-lookup"><span data-stu-id="c83c8-120">See Also</span></span>  
 [<span data-ttu-id="c83c8-121">メモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="c83c8-121">Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
