---
title: ネイティブ コンパイル ストアド プロシージャと実行 SET オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 264a2b3ab1e6f3f0bda97bfe89a4438aa641577d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742070"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a><span data-ttu-id="bbff2-102">ネイティブ コンパイル ストアド プロシージャと実行 SET オプション</span><span class="sxs-lookup"><span data-stu-id="bbff2-102">Natively Compiled Stored Procedures and Execution Set Options</span></span>
  <span data-ttu-id="bbff2-103">セッションのオプションは、ATOMIC ブロックでは固定されています。</span><span class="sxs-lookup"><span data-stu-id="bbff2-103">Session options are fixed in atomic blocks.</span></span> <span data-ttu-id="bbff2-104">ストアド プロシージャの実行は、セッションの SET オプションの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="bbff2-104">A stored procedure's execution is not affected by a session's SET options.</span></span> <span data-ttu-id="bbff2-105">ただし、特定の SET オプション (SET NOEXEC や SET SHOWPLAN_XML など) を指定すると、ストアド プロシージャ (ネイティブ コンパイル ストアド プロシージャを含む) が実行されなくなります。</span><span class="sxs-lookup"><span data-stu-id="bbff2-105">However, certain SET options, such as SET NOEXEC and SET SHOWPLAN_XML, cause stored procedures (including natively compiled stored procedures) to not execute.</span></span>  
  
 <span data-ttu-id="bbff2-106">任意の STATISTICS オプションを有効にしてネイティブ コンパイル ストアド プロシージャを実行すると、統計情報は、ステートメントごとではなく、プロシージャ全体に対して収集されます。</span><span class="sxs-lookup"><span data-stu-id="bbff2-106">When a natively compiled stored procedure is executed with any STATISTICS option turned on, statistics are gathered for the procedure as a whole and not per statement.</span></span> <span data-ttu-id="bbff2-107">詳細については、「[SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql)」、「[SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql)」、「[SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql)」、「[SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbff2-107">For more information, see [SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql), [SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql), and [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql).</span></span> <span data-ttu-id="bbff2-108">ネイティブ コンパイル ストアド プロシージャのステートメントごとのレベルに対する実行統計を取得するには、ストアド プロシージャの実行に含まれる各クエリが完了したときに開始される sp_statement_completed イベントの拡張イベント セッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="bbff2-108">To obtain execution statistics on a per-statement level in natively compiled stored procedures, use an Extended Event session on the sp_statement_completed event, which starts when each individual query in a stored procedures execution completes.</span></span> <span data-ttu-id="bbff2-109">拡張イベント セッションの作成の詳細については、「[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbff2-109">For more information on creating Extended Event sessions, see [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).</span></span>  
  
 <span data-ttu-id="bbff2-110">ネイティブ コンパイル ストアド プロシージャでは、`SHOWPLAN_XML` がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bbff2-110">`SHOWPLAN_XML` is supported for natively compiled stored procedures.</span></span> <span data-ttu-id="bbff2-111">`SHOWPLAN_ALL` と `SHOWPLAN_TEXT` は、ネイティブ コンパイル ストアド プロシージャではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bbff2-111">`SHOWPLAN_ALL` and `SHOWPLAN_TEXT` are not supported with natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="bbff2-112">`SET FMTONLY` は、ネイティブ コンパイル ストアド プロシージャではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bbff2-112">`SET FMTONLY` in not supported with natively compiled stored procedures.</span></span> <span data-ttu-id="bbff2-113">代わりに [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="bbff2-113">Use [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbff2-114">参照</span><span class="sxs-lookup"><span data-stu-id="bbff2-114">See Also</span></span>  
 [<span data-ttu-id="bbff2-115">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="bbff2-115">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
