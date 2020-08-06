---
title: ネイティブ コンパイル ストアド プロシージャの呼び出しに関するベスト プラクティス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d07d0e290d1fbd9b324235e64734a399bf7801d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632461"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a><span data-ttu-id="74165-102">ネイティブ コンパイル ストアド プロシージャの呼び出しに関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="74165-102">Best Practices for Calling Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="74165-103">ネイティブ コンパイル ストアド プロシージャの特徴:</span><span class="sxs-lookup"><span data-stu-id="74165-103">Natively compiled stored procedures are:</span></span>  
  
-   <span data-ttu-id="74165-104">通常、アプリケーションのパフォーマンスが重要な部分に使用されます。</span><span class="sxs-lookup"><span data-stu-id="74165-104">Used typically in performance-critical parts of an application.</span></span>  
  
-   <span data-ttu-id="74165-105">頻繁に実行されます。</span><span class="sxs-lookup"><span data-stu-id="74165-105">Frequently executed.</span></span>  
  
-   <span data-ttu-id="74165-106">非常に高速であることが求められます。</span><span class="sxs-lookup"><span data-stu-id="74165-106">Expected to be very fast.</span></span>  
  
 <span data-ttu-id="74165-107">ネイティブ コンパイル ストアド プロシージャを使用することに伴うパフォーマンス上の利点は、プロシージャによって処理される行の数と論理の量に従って大きくなります。</span><span class="sxs-lookup"><span data-stu-id="74165-107">The performance benefit of using a natively compiled stored procedure increases with the number of rows and the amount of logic that is processed by the procedure.</span></span> <span data-ttu-id="74165-108">たとえば、次の 1 つ以上を使用している場合は、ネイティブ コンパイル ストアド プロシージャのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="74165-108">For example, a natively compiled stored procedure will exhibit better performance if it uses one or more of the following:</span></span>  
  
-   <span data-ttu-id="74165-109">集計。</span><span class="sxs-lookup"><span data-stu-id="74165-109">Aggregation.</span></span>  
  
-   <span data-ttu-id="74165-110">入れ子になっているループ結合。</span><span class="sxs-lookup"><span data-stu-id="74165-110">Nested-loops joins.</span></span>  
  
-   <span data-ttu-id="74165-111">複数ステートメントの SELECT、INSERT、UPDATE、および DELETE 操作。</span><span class="sxs-lookup"><span data-stu-id="74165-111">Multi-statement select, insert, update, and delete operations.</span></span>  
  
-   <span data-ttu-id="74165-112">複合式。</span><span class="sxs-lookup"><span data-stu-id="74165-112">Complex expressions.</span></span>  
  
-   <span data-ttu-id="74165-113">条件ステートメントとループなど、手続き型のロジック。</span><span class="sxs-lookup"><span data-stu-id="74165-113">Procedural logic, such as conditional statements and loops.</span></span>  
  
 <span data-ttu-id="74165-114">単一行のみを処理する必要がある場合は、ネイティブ コンパイル ストアド プロシージャを使用しても、パフォーマンス上の利点が得られるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="74165-114">If you need to process only a single row, using a natively compiled stored procedure may not provide a performance benefit.</span></span>  
  
 <span data-ttu-id="74165-115">サーバーによるパラメーター名のマップと型の変換を回避するには:</span><span class="sxs-lookup"><span data-stu-id="74165-115">To avoid the server having to map parameter names and convert types:</span></span>  
  
-   <span data-ttu-id="74165-116">プロシージャに渡されるパラメーターの型をプロシージャ定義の型に一致させます。</span><span class="sxs-lookup"><span data-stu-id="74165-116">Match the types of the parameters passed to the procedure with the types in the procedure definition.</span></span>  
  
-   <span data-ttu-id="74165-117">ネイティブ コンパイル ストアド プロシージャを呼び出すときに序数 (名前のない) パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="74165-117">Use ordinal (nameless) parameters when calling natively compiled stored procedures.</span></span> <span data-ttu-id="74165-118">最も効率的に実行するには、名前付きパラメーターを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="74165-118">For the most efficient execution, do not use named parameters.</span></span>  
  
 <span data-ttu-id="74165-119">ネイティブ コンパイル ストアド プロシージャでの (非効率的な) 名前付きパラメーターの使用は、XEvent の `hekaton_slow_parameter_passing` を `reason=named_parameters` と共に使用して検出できます。</span><span class="sxs-lookup"><span data-stu-id="74165-119">Use of (inefficient) named parameters with natively compiled stored procedures can be detected through the XEvent `hekaton_slow_parameter_passing`, with `reason=named_parameters`.</span></span>  
  
 <span data-ttu-id="74165-120">同様に、同じ XEvent `hekaton_slow_parameter_passing` を `reason=parameter_conversion` と共に使用して、一致しない型の使用を検出することができます。</span><span class="sxs-lookup"><span data-stu-id="74165-120">Similarly, you can detect use of mismatched types through the same XEvent `hekaton_slow_parameter_passing`, with `reason=parameter_conversion`.</span></span>  
  
 <span data-ttu-id="74165-121">メモリ最適化テーブルを使用するときは (多くのシナリオで) 再試行ロジックを実装する必要があり、特定の機能制限に対処する必要があるため、インタープリターによって処理されるラッパー形式の [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを作成する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="74165-121">Because you will need to implement retry logic when using memory-optimized tables (in many scenarios), and because you will need to work around certain feature limitations, you may want to create a wrapper interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure.</span></span> <span data-ttu-id="74165-122">例については、「[メモリ最適化テーブルでのトランザクションの再試行ロジックのガイドライン](memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74165-122">For an example, see [Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74165-123">参照</span><span class="sxs-lookup"><span data-stu-id="74165-123">See Also</span></span>  
 [<span data-ttu-id="74165-124">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="74165-124">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
