---
title: 'SQL Server: SQL Statistics オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:SQL Statistics
- SQL Statistics object
ms.assetid: da7dbb4b-f632-45a0-b1ab-c35cc2695c86
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8aba118f93a9a4f38179e8e7c5156eecc24012ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713074"
---
# <a name="sql-server-sql-statistics-object"></a><span data-ttu-id="02f89-102">SQL Server: SQL Statistics オブジェクト</span><span class="sxs-lookup"><span data-stu-id="02f89-102">SQL Server, SQL Statistics Object</span></span>
  <span data-ttu-id="02f89-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **SQLServer:SQL Statistics** オブジェクトには、コンパイルの動作や、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに送信された要求の種類を監視するためのカウンターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="02f89-103">The **SQLServer:SQL Statistics** object in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor compilation and the type of requests sent to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="02f89-104">クエリのコンパイルと再コンパイルの回数、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが受信するバッチの数を監視すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がユーザー クエリを処理する速度や、クエリ オプティマイザーによるクエリ処理の効果がわかります。</span><span class="sxs-lookup"><span data-stu-id="02f89-104">Monitoring the number of query compilations and recompilations and the number of batches received by an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gives you an indication of how quickly [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is processing user queries and how effectively the query optimizer is processing the queries.</span></span>  
  
 <span data-ttu-id="02f89-105">コンパイルは、クエリのターンアラウンド時間の大半を占めます。</span><span class="sxs-lookup"><span data-stu-id="02f89-105">Compilation is a significant part of a query's turnaround time.</span></span> <span data-ttu-id="02f89-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] では、コンパイルのコストを節約するために、コンパイル済みのクエリ プランがクエリ キャッシュに保存されます。</span><span class="sxs-lookup"><span data-stu-id="02f89-106">In order to save the compilation cost, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] saves the compiled query plan in a query cache.</span></span> <span data-ttu-id="02f89-107">キャッシュを使用して、コンパイル済みのクエリを再使用のために保存すると、後から実行するときに再コンパイルの必要がなくなるので、コンパイルを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="02f89-107">The objective of the cache is to reduce compilation by storing compiled queries for later reuse, therefore ending the requirement to recompile queries when later executed.</span></span> <span data-ttu-id="02f89-108">ただし、一意のクエリはすべて、少なくとも 1 回コンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02f89-108">However, each unique query must be compiled at least one time.</span></span> <span data-ttu-id="02f89-109">クエリの再コンパイルは、次の要因によって生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="02f89-109">Query recompilations can be caused by the following factors:</span></span>  
  
-   <span data-ttu-id="02f89-110">テーブルへの列またはインデックスの追加など、ベース スキーマの変更を含むスキーマの変更、またはテーブルに大量の行を挿入したり、テーブルから大量の行を削除することなどの統計スキーマの変更。</span><span class="sxs-lookup"><span data-stu-id="02f89-110">Schema changes, including base schema changes such as adding columns or indexes to a table, or statistics schema changes such as inserting or deleting a significant number of rows from a table.</span></span>  
  
-   <span data-ttu-id="02f89-111">環境 (SET ステートメント) の変更。</span><span class="sxs-lookup"><span data-stu-id="02f89-111">Environment (SET statement) changes.</span></span> <span data-ttu-id="02f89-112">ANSI_PADDING や ANSI_NULLS などのセッション設定の変更によって、クエリが再コンパイルされることがあります。</span><span class="sxs-lookup"><span data-stu-id="02f89-112">Changes in session settings such as ANSI_PADDING or ANSI_NULLS can cause a query to be recompiled.</span></span>  
  
 <span data-ttu-id="02f89-113">簡易パラメーター化と強制パラメーター化の詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02f89-113">For more information about simple and forced parameterization, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="02f89-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Statistics** カウンターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="02f89-114">These are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Statistics** counters.</span></span>  
  
|<span data-ttu-id="02f89-115">SQL Server SQL Statistics カウンター</span><span class="sxs-lookup"><span data-stu-id="02f89-115">SQL Server SQL Statistics counters</span></span>|<span data-ttu-id="02f89-116">説明</span><span class="sxs-lookup"><span data-stu-id="02f89-116">Description</span></span>|  
|----------------------------------------|-----------------|  
|<span data-ttu-id="02f89-117">**Auto-Param Attempts/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-117">**Auto-Param Attempts/sec**</span></span>|<span data-ttu-id="02f89-118">1 秒あたりの自動パラメーター化が実行された数。</span><span class="sxs-lookup"><span data-stu-id="02f89-118">Number of auto-parameterization attempts per second.</span></span> <span data-ttu-id="02f89-119">総数は、失敗した試行、安全な試行、および安全ではない試行の合計でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="02f89-119">Total should be the sum of the failed, safe, and unsafe auto-parameterizations.</span></span> <span data-ttu-id="02f89-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにより、いくつかのリテラルをパラメーターに置き換えることによって [!INCLUDE[tsql](../../../includes/tsql-md.md)] 要求のパラメーター化が試行されると、自動パラメーター化が発生します。複数の類似した要求で、結果としてキャッシュされた実行プランの再使用を可能にするためです。</span><span class="sxs-lookup"><span data-stu-id="02f89-120">Auto-parameterization occurs when an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to parameterize a [!INCLUDE[tsql](../../../includes/tsql-md.md)] request by replacing some literals with parameters so that reuse of the resulting cached execution plan across multiple similar-looking requests is possible.</span></span> <span data-ttu-id="02f89-121">自動パラメーター化は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新しいバージョンでは簡易パラメーター化とも呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="02f89-121">Note that auto-parameterizations are also known as simple parameterizations in newer versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="02f89-122">このカウンターには、強制パラメーター化は含まれません。</span><span class="sxs-lookup"><span data-stu-id="02f89-122">This counter does not include forced parameterizations.</span></span>|  
|<span data-ttu-id="02f89-123">**Batch Requests/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-123">**Batch Requests/sec**</span></span>|<span data-ttu-id="02f89-124">1 秒あたりに受信した [!INCLUDE[tsql](../../../includes/tsql-md.md)] コマンドのバッチの数。</span><span class="sxs-lookup"><span data-stu-id="02f89-124">Number of [!INCLUDE[tsql](../../../includes/tsql-md.md)] command batches received per second.</span></span> <span data-ttu-id="02f89-125">この統計値はすべての制約の影響を受けます。制約とは、I/O、ユーザー数、キャッシュ サイズ、要求の複雑さなどです。</span><span class="sxs-lookup"><span data-stu-id="02f89-125">This statistic is affected by all constraints (such as I/O, number of users, cache size, complexity of requests, and so on).</span></span> <span data-ttu-id="02f89-126">バッチ要求の数が多いことは、スループットが優れていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="02f89-126">High batch requests mean good throughput.</span></span>|  
|<span data-ttu-id="02f89-127">**Failed Auto-Params/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-127">**Failed Auto-Params/sec**</span></span>|<span data-ttu-id="02f89-128">1 秒あたりの失敗した自動パラメーター化を実行した回数。</span><span class="sxs-lookup"><span data-stu-id="02f89-128">Number of failed auto-parameterization attempts per second.</span></span> <span data-ttu-id="02f89-129">これは小さな値でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="02f89-129">This should be small.</span></span> <span data-ttu-id="02f89-130">自動パラメーター化は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の最新バージョンでは簡易パラメーター化とも呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="02f89-130">Note that auto-parameterizations are also known as simple parameterizations in later versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="02f89-131">**Forced Parameterizations/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-131">**Forced Parameterizations/sec**</span></span>|<span data-ttu-id="02f89-132">強制パラメーター化に成功した 1 秒あたりの回数。</span><span class="sxs-lookup"><span data-stu-id="02f89-132">Number of successful forced parameterizations per second.</span></span>|  
|<span data-ttu-id="02f89-133">**Guided Plan Executions/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-133">**Guided Plan Executions/sec**</span></span>|<span data-ttu-id="02f89-134">プラン ガイドを使用してクエリ プランが生成された、1 秒あたりのプラン実行回数。</span><span class="sxs-lookup"><span data-stu-id="02f89-134">Number of plan executions per second in which the query plan has been generated by using a plan guide.</span></span>|  
|<span data-ttu-id="02f89-135">**Misguided Plan Executions/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-135">**Misguided Plan Executions/sec**</span></span>|<span data-ttu-id="02f89-136">プランの生成中にプラン ガイドが適用できなかった、1 秒あたりのプラン実行回数。</span><span class="sxs-lookup"><span data-stu-id="02f89-136">Number of plan executions per second in which a plan guide could not be honored during plan generation.</span></span> <span data-ttu-id="02f89-137">このプラン ガイドは無視され、通常のコンパイルを使用して実行済みプランが生成されています。</span><span class="sxs-lookup"><span data-stu-id="02f89-137">The plan guide was disregarded and normal compilation was used to generate the executed plan.</span></span>|  
|<span data-ttu-id="02f89-138">**Safe Auto-Params/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-138">**Safe Auto-Params/sec**</span></span>|<span data-ttu-id="02f89-139">1 秒あたりの安全な自動パラメーター化を実行した回数。</span><span class="sxs-lookup"><span data-stu-id="02f89-139">Number of safe auto-parameterization attempts per second.</span></span> <span data-ttu-id="02f89-140">安全とは、キャッシュされた実行プランを、さまざまな類似する [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメント間で共有できるという判断のことを言います。</span><span class="sxs-lookup"><span data-stu-id="02f89-140">Safe refers to a determination that a cached execution plan can be shared between different similar-looking [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="02f89-141">多くの自動パラメーター化が試行され、そのうちのいくつかは安全という結果になり、その他は安全ではないという結果になります。</span><span class="sxs-lookup"><span data-stu-id="02f89-141">makes many auto-parameterization attempts some of which turn out to be safe and others fail.</span></span> <span data-ttu-id="02f89-142">自動パラメーター化は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の最新バージョンでは簡易パラメーター化とも呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="02f89-142">Note that auto-parameterizations are also known as simple parameterizations in later versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="02f89-143">これには、強制的なパラメーター化は含まれません。</span><span class="sxs-lookup"><span data-stu-id="02f89-143">This does not include forced parameterizations.</span></span>|  
|<span data-ttu-id="02f89-144">**SQL Attention rate**</span><span class="sxs-lookup"><span data-stu-id="02f89-144">**SQL Attention rate**</span></span>|<span data-ttu-id="02f89-145">1 秒あたりのアテンションの数。</span><span class="sxs-lookup"><span data-stu-id="02f89-145">Number of attentions per second.</span></span> <span data-ttu-id="02f89-146">アテンションは、現在実行している要求を終了するために、クライアントから要求されます。</span><span class="sxs-lookup"><span data-stu-id="02f89-146">An attention is a request by the client to end the currently running request.</span></span>|  
|<span data-ttu-id="02f89-147">**SQL Compilations/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-147">**SQL Compilations/sec**</span></span>|<span data-ttu-id="02f89-148">1 秒あたりの SQL コンパイルの回数。</span><span class="sxs-lookup"><span data-stu-id="02f89-148">Number of SQL compilations per second.</span></span> <span data-ttu-id="02f89-149">コンパイル コード パスが入力された回数を示します。</span><span class="sxs-lookup"><span data-stu-id="02f89-149">Indicates the number of times the compile code path is entered.</span></span> <span data-ttu-id="02f89-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のステートメントレベルの再コンパイルによって発生したコンパイル回数を含みます。</span><span class="sxs-lookup"><span data-stu-id="02f89-150">Includes compiles caused by statement-level recompilations in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="02f89-151">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザー利用状況が安定化すると、この値は定常状態に到達します。</span><span class="sxs-lookup"><span data-stu-id="02f89-151">After [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user activity is stable, this value reaches a steady state.</span></span>|  
|<span data-ttu-id="02f89-152">**SQL Re-Compilations/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-152">**SQL Re-Compilations/sec**</span></span>|<span data-ttu-id="02f89-153">1 秒あたりのステートメントの再コンパイル回数。</span><span class="sxs-lookup"><span data-stu-id="02f89-153">Number of statement recompiles per second.</span></span> <span data-ttu-id="02f89-154">ステートメントの再コンパイルがトリガーされた回数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="02f89-154">Counts the number of times statement recompiles are triggered.</span></span> <span data-ttu-id="02f89-155">一般に、再コンパイルは少なくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02f89-155">Generally, you want the recompiles to be low.</span></span>|  
|<span data-ttu-id="02f89-156">**Unsafe Auto-Params/sec**</span><span class="sxs-lookup"><span data-stu-id="02f89-156">**Unsafe Auto-Params/sec**</span></span>|<span data-ttu-id="02f89-157">1 秒あたりの安全でない自動パラメーター化の回数。</span><span class="sxs-lookup"><span data-stu-id="02f89-157">Number of unsafe auto-parameterization attempts per second.</span></span> <span data-ttu-id="02f89-158">たとえば、クエリには、キャッシュされたプランを共有できないいくつかの特性があります。</span><span class="sxs-lookup"><span data-stu-id="02f89-158">For example, the query has some characteristics that prevent the cached plan from being shared.</span></span> <span data-ttu-id="02f89-159">これらは、安全ではないと見なされています。</span><span class="sxs-lookup"><span data-stu-id="02f89-159">These are designated as unsafe.</span></span> <span data-ttu-id="02f89-160">これは、強制パラメーター化の数としてはカウントされません。</span><span class="sxs-lookup"><span data-stu-id="02f89-160">This does not count the number of forced parameterizations.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02f89-161">参照</span><span class="sxs-lookup"><span data-stu-id="02f89-161">See Also</span></span>  
 <span data-ttu-id="02f89-162">[SQL Server の Plan Cache オブジェクト](sql-server-plan-cache-object.md) </span><span class="sxs-lookup"><span data-stu-id="02f89-162">[SQL Server, Plan Cache Object](sql-server-plan-cache-object.md) </span></span>  
 [<span data-ttu-id="02f89-163">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="02f89-163">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  