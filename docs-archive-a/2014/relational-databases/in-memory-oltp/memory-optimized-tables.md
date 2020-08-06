---
title: メモリ最適化テーブル | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14dddf81-b502-49dc-a6b6-d18b1ae32d2b
author: rothja
ms.author: jroth
ms.openlocfilehash: 73430505e55230daf31c492d882eadeb6d35d29f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740998"
---
# <a name="memory-optimized-tables"></a><span data-ttu-id="be31b-102">メモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="be31b-102">Memory-Optimized Tables</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="be31b-103">のインメモリ OLTP は、メモリ最適化された効率的なデータ アクセス、ビジネス ロジックのネイティブ コンパイル、ロック フリーおよびラッチ フリーのアルゴリズムによって OLTP アプリケーションのパフォーマンスを高めます。</span><span class="sxs-lookup"><span data-stu-id="be31b-103">In-Memory OLTP helps improve performance of OLTP applications through efficient, memory-optimized data access, native compilation of business logic, and lock- and latch free algorithms.</span></span> <span data-ttu-id="be31b-104">インメモリ OLTP 機能には、メモリ最適化テーブルおよびテーブル型と、これらのテーブルに効率的にアクセスするための [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャのネイティブ コンパイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="be31b-104">The In-Memory OLTP feature includes memory-optimized tables and table types, as well as native compilation of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures for efficient access to these tables.</span></span>  
  
 <span data-ttu-id="be31b-105">メモリ最適化テーブルの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be31b-105">For more information about memory-optimized tables, see:</span></span>  
  
-   [<span data-ttu-id="be31b-106">メモリ最適化テーブルの概要</span><span class="sxs-lookup"><span data-stu-id="be31b-106">Introduction to Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
     <span data-ttu-id="be31b-107">メモリ最適化テーブルについて詳述し、データの耐久性、メモリ最適化テーブルのデータへのアクセス、パフォーマンス、スケーラビリテに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="be31b-107">Details what memory-optimized tables are and provides information about data durability, accessing data in memory-optimized tables, and performance and scalability.</span></span>  
  
-   [<span data-ttu-id="be31b-108">テーブルとストアド プロシージャのネイティブ コンパイル</span><span class="sxs-lookup"><span data-stu-id="be31b-108">Native Compilation of Tables and Stored Procedures</span></span>](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
     <span data-ttu-id="be31b-109">どのようにメモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャが DLL にコンパイルされるかについて詳述し、関連するセキュリティ上の考慮事項を示します。</span><span class="sxs-lookup"><span data-stu-id="be31b-109">Details how memory-optimized tables and natively compiled stored procedures are compiled into DLLs, and provides related security considerations.</span></span>  
  
-   [<span data-ttu-id="be31b-110">メモリ最適化テーブルの変更</span><span class="sxs-lookup"><span data-stu-id="be31b-110">Altering Memory-Optimized Tables</span></span>](altering-memory-optimized-tables.md)  
  
     <span data-ttu-id="be31b-111">メモリ最適化テーブルの更新 (テーブルの列、索引、および bucket_count の変更など) に関するガイドラインです。</span><span class="sxs-lookup"><span data-stu-id="be31b-111">Guidelines for updating memory-optimized tables (including changing table columns, indexes, and bucket_count).</span></span>  
  
-   [<span data-ttu-id="be31b-112">メモリ最適化テーブルを対象にするトランザクションについて</span><span class="sxs-lookup"><span data-stu-id="be31b-112">Understanding Transactions on Memory-Optimized Tables</span></span>](../../database-engine/understanding-transactions-on-memory-optimized-tables.md)  
  
     <span data-ttu-id="be31b-113">このセクションには、メモリ最適化テーブルでのトランザクションの実行に関連するいくつかのトピック (トランザクション分離レベル、クロスコンテナーなど) があります。</span><span class="sxs-lookup"><span data-stu-id="be31b-113">This section provides several topics related to performing transactions on memory-optimized tables including transaction isolation levels, and cross-container transactions.</span></span>  
  
-   [<span data-ttu-id="be31b-114">メモリ最適化テーブルのパーティション分割に関するアプリケーションのパターン</span><span class="sxs-lookup"><span data-stu-id="be31b-114">Application Pattern for Partitioning Memory-Optimized Tables</span></span>](application-pattern-for-partitioning-memory-optimized-tables.md)  
  
     <span data-ttu-id="be31b-115">メモリ最適化テーブルの使用時にパーティション テーブルをエミュレートする方法を示す詳細なコード サンプルです。</span><span class="sxs-lookup"><span data-stu-id="be31b-115">Detailed code sample that shows how to emulate partitioned tables when using memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="be31b-116">メモリ最適化テーブルの統計</span><span class="sxs-lookup"><span data-stu-id="be31b-116">Statistics for Memory-Optimized Tables</span></span>](statistics-for-memory-optimized-tables.md)  
  
     <span data-ttu-id="be31b-117">メモリ最適化テーブルで統計をまとめる方法とメモリ最適化テーブルで統計を保守および手動更新する方法について詳述します。</span><span class="sxs-lookup"><span data-stu-id="be31b-117">Details how statistics are compiled for memory-optimized tables and how to maintain and manually update statistics for memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="be31b-118">照合順序とコード ページ</span><span class="sxs-lookup"><span data-stu-id="be31b-118">Collations and Code Pages</span></span>](../../database-engine/collations-and-code-pages.md)  
  
     <span data-ttu-id="be31b-119">メモリ最適化テーブルでサポートされる照合およびコード ページに関する制限について詳述します。</span><span class="sxs-lookup"><span data-stu-id="be31b-119">Details the restrictions on supported collations and code pages for memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="be31b-120">メモリ最適化テーブルのテーブルと行のサイズ</span><span class="sxs-lookup"><span data-stu-id="be31b-120">Table and Row Size in Memory-Optimized Tables</span></span>](table-and-row-size-in-memory-optimized-tables.md)  
  
     <span data-ttu-id="be31b-121">メモリ最適化テーブルの行に関する 8060 バイトの制限について詳述し、テーブルおよび行のサイズの計算例を提供します。</span><span class="sxs-lookup"><span data-stu-id="be31b-121">Details the 8060 byte limit on memory-optimized table rows, and provides an example for calculating table and row sizes.</span></span>  
  
-   [<span data-ttu-id="be31b-122">メモリ最適化テーブルのクエリ処理のガイド</span><span class="sxs-lookup"><span data-stu-id="be31b-122">A Guide to Query Processing for Memory-Optimized Tables</span></span>](a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
     <span data-ttu-id="be31b-123">メモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャの両方に対するクエリ処理の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="be31b-123">Provides an overview of query processing for both memory-optimized tables, and natively compiled stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be31b-124">参照</span><span class="sxs-lookup"><span data-stu-id="be31b-124">See Also</span></span>  
 [<span data-ttu-id="be31b-125">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="be31b-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp-in-memory-optimization.md)  
  
  
