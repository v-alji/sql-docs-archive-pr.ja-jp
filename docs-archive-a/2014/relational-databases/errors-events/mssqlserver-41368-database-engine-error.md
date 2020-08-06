---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 10e187223a3f35b4b21ede6965e3c9efea2e30c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715309"
---
# <a name="mssqlserver_41368"></a><span data-ttu-id="55299-102">MSSQLSERVER_41368</span><span class="sxs-lookup"><span data-stu-id="55299-102">MSSQLSERVER_41368</span></span>
    
## <a name="details"></a><span data-ttu-id="55299-103">詳細</span><span class="sxs-lookup"><span data-stu-id="55299-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55299-104">製品名</span><span class="sxs-lookup"><span data-stu-id="55299-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="55299-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="55299-105">Event ID</span></span>|<span data-ttu-id="55299-106">41368</span><span class="sxs-lookup"><span data-stu-id="55299-106">41368</span></span>|  
|<span data-ttu-id="55299-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="55299-107">Event Source</span></span>|<span data-ttu-id="55299-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="55299-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="55299-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="55299-109">Component</span></span>|<span data-ttu-id="55299-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="55299-110">SQLEngine</span></span>|  
|<span data-ttu-id="55299-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="55299-111">Symbolic Name</span></span>|<span data-ttu-id="55299-112">SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="55299-112">SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="55299-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="55299-113">Message Text</span></span>|<span data-ttu-id="55299-114">READ COMMITTED 分離レベルを使用してメモリ最適化テーブルにアクセスする機能は、オートコミット トランザクションでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="55299-114">Accessing memory optimized tables using the READ COMMITTED isolation level is supported only for autocommit transactions.</span></span> <span data-ttu-id="55299-115">明示的なトランザクションおよび暗黙的なトランザクションではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="55299-115">It is not supported for explicit or implicit transactions.</span></span> <span data-ttu-id="55299-116">メモリ最適化テーブルには WITH (SNAPSHOT) などのテーブル ヒントを使用して、サポートされる分離レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="55299-116">Provide a supported isolation level for the memory optimized table using a table hint, such as WITH (SNAPSHOT).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="55299-117">説明</span><span class="sxs-lookup"><span data-stu-id="55299-117">Explanation</span></span>  
 <span data-ttu-id="55299-118">READ COMMITTED 分離レベルを使用してメモリ最適化テーブルにアクセスする機能は、自動コミット トランザクションでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="55299-118">Accessing memory-optimized tables using the READ COMMITTED isolation level is supported only for autocommit transactions.</span></span> <span data-ttu-id="55299-119">詳細については、「 [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="55299-119">For more information, see [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).</span></span>  
  
 <span data-ttu-id="55299-120">BEGIN TRANSACTION を使用して開始された明示的なトランザクション、または IMPLICIT_TRANSACTIONS が ON に設定されている状況で暗黙的なトランザクションからメモリ最適化テーブルにアクセスする場合は、READ COMMITTED 分離レベルはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="55299-120">When accessing a memory-optimized table from an explicit transaction that was started with BEGIN TRANSACTION, or from an implicit transaction, if IMPLICIT_TRANSACTIONS is set to ON, the READ COMMITTED isolation level is not supported.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="55299-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="55299-121">User Action</span></span>  
 <span data-ttu-id="55299-122">明示的または暗黙的な READ COMMITTED トランザクションからメモリ最適化されたテーブルにアクセスする場合は、テーブルにアクセスするために SNAPSHOT を使用します。</span><span class="sxs-lookup"><span data-stu-id="55299-122">When accessing a memory-optimized table from an explicit or implicit READ COMMITTED transaction, use SNAPSHOT to access the table.</span></span> <span data-ttu-id="55299-123">これを実現するには、テーブルヒント WITH (SNAPSHOT) を使用します (詳細については、「[メモリ最適化テーブルを使用したトランザクション分離レベルのガイドライン](../in-memory-oltp/memory-optimized-tables.md)」を参照)。または、データベース MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT オプションを ON に設定する (詳細については、「 [ALTER database SET Options &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55299-123">This can be achieved by using the table hint WITH (SNAPSHOT) (for more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../in-memory-oltp/memory-optimized-tables.md)) or by setting the database option MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT to ON (for more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55299-124">参照</span><span class="sxs-lookup"><span data-stu-id="55299-124">See Also</span></span>  
 [<span data-ttu-id="55299-125">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="55299-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
