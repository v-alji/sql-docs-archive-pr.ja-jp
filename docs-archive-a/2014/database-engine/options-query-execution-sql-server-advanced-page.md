---
title: '[オプション] ([クエリ実行]: SQL Server: [詳細設定] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionAdvanced
ms.assetid: 3ec788c7-22c3-4216-9ad0-81a168d17074
author: rothja
ms.author: jroth
ms.openlocfilehash: 3efc3dc8b42fc08969cc1afb85d4e629f6759e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644608"
---
# <a name="options-query-executionsql-serveradvanced-page"></a><span data-ttu-id="f7211-102">[オプション] ([クエリ実行]: [SQL Server]: [詳細設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="f7211-102">Options (Query Execution:SQL Server:Advanced Page)</span></span>
  <span data-ttu-id="f7211-103">SET コマンドを使用する場合は、いくつかのオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7211-103">Several options are available using the SET command.</span></span> <span data-ttu-id="f7211-104">このページを使用すると、SQL Server クエリ エディターで [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クエリを実行するための **set** オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f7211-104">Use this page to specify a **set** option for running [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries in the SQL Server Query Editor.</span></span> <span data-ttu-id="f7211-105">他のコード エディターには影響しません。</span><span class="sxs-lookup"><span data-stu-id="f7211-105">They have no effect on other code editors.</span></span> <span data-ttu-id="f7211-106">これらのオプションに加えられた変更は、新しい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クエリだけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f7211-106">Changes to these options are only applied to new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="f7211-107">現在のクエリのオプションを変更するには、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クエリ ウィンドウの **[クエリ]** メニューまたはショートカット メニューの **[クエリ オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7211-107">To change the options for the current queries, click **Query Options** on the **Query** menu or the shortcut menu of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window.</span></span> <span data-ttu-id="f7211-108">**[実行]** の **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7211-108">Under **Execution**, click **Advanced**.</span></span> <span data-ttu-id="f7211-109">各オプションの詳細については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7211-109">For more information on each of these, see [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f7211-110">Options</span><span class="sxs-lookup"><span data-stu-id="f7211-110">Options</span></span>  
 <span data-ttu-id="f7211-111">**SET NOCOUNT**</span><span class="sxs-lookup"><span data-stu-id="f7211-111">**SET NOCOUNT**</span></span>  
 <span data-ttu-id="f7211-112">結果セットのメッセージとして、行数を返しません。</span><span class="sxs-lookup"><span data-stu-id="f7211-112">Does not return the count of the number of rows, as a message with the result set.</span></span> <span data-ttu-id="f7211-113">既定では、このチェック ボックスはオフです。</span><span class="sxs-lookup"><span data-stu-id="f7211-113">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="f7211-114">**SET NOEXEC**</span><span class="sxs-lookup"><span data-stu-id="f7211-114">**SET NOEXEC**</span></span>  
 <span data-ttu-id="f7211-115">クエリを実行しません。</span><span class="sxs-lookup"><span data-stu-id="f7211-115">Does not run the query.</span></span> <span data-ttu-id="f7211-116">既定では、このチェック ボックスはオフです。</span><span class="sxs-lookup"><span data-stu-id="f7211-116">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="f7211-117">**[SET PARSEONLY]**</span><span class="sxs-lookup"><span data-stu-id="f7211-117">**SET PARSEONLY**</span></span>  
 <span data-ttu-id="f7211-118">各クエリの構文をチェックするだけで、クエリを実行しません。</span><span class="sxs-lookup"><span data-stu-id="f7211-118">Checks the syntax of each query but does not run the queries.</span></span> <span data-ttu-id="f7211-119">既定では、このチェック ボックスはオフです。</span><span class="sxs-lookup"><span data-stu-id="f7211-119">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="f7211-120">**SET CONCAT_NULL_YIELDS_NULL**</span><span class="sxs-lookup"><span data-stu-id="f7211-120">**SET CONCAT_NULL_YIELDS_NULL**</span></span>  
 <span data-ttu-id="f7211-121">このチェック ボックスがオンの場合、既存の値と NULL を連結するクエリは、結果として常に NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="f7211-121">When this check box is selected, queries that concatenate an existing value with a NULL, always return a NULL as the result.</span></span> <span data-ttu-id="f7211-122">このチェック ボックスがオフの場合、既存の値と NULL を連結するクエリは、既存の値を返します。</span><span class="sxs-lookup"><span data-stu-id="f7211-122">When this check box is cleared, an existing value concatenated with a NULL, returns the existing value.</span></span> <span data-ttu-id="f7211-123">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="f7211-123">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="f7211-124">**SET ARITHABORT**</span><span class="sxs-lookup"><span data-stu-id="f7211-124">**SET ARITHABORT**</span></span>  
 <span data-ttu-id="f7211-125">このチェック ボックスがオンの場合、式の評価中に INSERT、DELETE、または UPDATE ステートメントで算術エラー (オーバーフロー、0 による除算、またはドメイン エラー) が発生すると、クエリまたはバッチは終了します。</span><span class="sxs-lookup"><span data-stu-id="f7211-125">When this check box is selected, when an INSERT, DELETE, or UPDATE statement encounters an arithmetic error (overflow, divide-by-zero, or a domain error) during expression evaluation the query or batch is terminated.</span></span> <span data-ttu-id="f7211-126">このチェック ボックスがオフの場合、可能であればその値に対して NULL が与えられ、クエリが続行されます。さらに、結果にメッセージが含められます。</span><span class="sxs-lookup"><span data-stu-id="f7211-126">When this check box is cleared, a NULL is provided for that value if possible, the query continues, and a message is included with the result.</span></span> <span data-ttu-id="f7211-127">詳細については、「[SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f7211-127">For more information, see [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).</span></span> <span data-ttu-id="f7211-128">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="f7211-128">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="f7211-129">**[SET SHOWPLAN_TEXT]**</span><span class="sxs-lookup"><span data-stu-id="f7211-129">**SET SHOWPLAN_TEXT**</span></span>  
 <span data-ttu-id="f7211-130">このチェック ボックスがオンの場合、各クエリに対してクエリ プランがテキスト形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="f7211-130">When this check box is selected, the query plan is returned in text format with each query.</span></span> <span data-ttu-id="f7211-131">既定では、このチェック ボックスはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="f7211-131">This check box cleared by default.</span></span>  
  
 <span data-ttu-id="f7211-132">**SET STATISTICS TIME**</span><span class="sxs-lookup"><span data-stu-id="f7211-132">**SET STATISTICS TIME**</span></span>  
 <span data-ttu-id="f7211-133">このチェック ボックスがオンの場合、各クエリに対して時間統計情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="f7211-133">When this check box is selected, the time statistics are returned with each query.</span></span> <span data-ttu-id="f7211-134">既定では、このチェック ボックスはオフです。</span><span class="sxs-lookup"><span data-stu-id="f7211-134">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="f7211-135">**[SET STATISTICS IO]**</span><span class="sxs-lookup"><span data-stu-id="f7211-135">**SET STATISTICS IO**</span></span>  
 <span data-ttu-id="f7211-136">このチェック ボックスがオンの場合、各クエリに対して入力および出力に関する統計情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="f7211-136">When this check box is selected, statistics regarding input and output are returned with each query.</span></span> <span data-ttu-id="f7211-137">既定では、このチェック ボックスはオフです。</span><span class="sxs-lookup"><span data-stu-id="f7211-137">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="f7211-138">**SET TRANSACTION ISOLATION LEVEL**</span><span class="sxs-lookup"><span data-stu-id="f7211-138">**SET TRANSACTION ISOLATION LEVEL**</span></span>  
 <span data-ttu-id="f7211-139">既定では READ COMMITTED トランザクション分離レベルが設定されます。</span><span class="sxs-lookup"><span data-stu-id="f7211-139">The READ COMMITTED transaction isolation level is set by default.</span></span> <span data-ttu-id="f7211-140">詳細については、「[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7211-140">For more information, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span> <span data-ttu-id="f7211-141">SNAPSHOT トランザクション分離レベルは使用できません。</span><span class="sxs-lookup"><span data-stu-id="f7211-141">SNAPSHOT transaction isolation level is not available.</span></span> <span data-ttu-id="f7211-142">SNAPSHOT 分離を使用するには、次の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="f7211-142">To use SNAPSHOT isolation, add the following [!INCLUDE[tsql](../includes/tsql-md.md)] statement:</span></span>  
  
```  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
GO  
```  
  
 <span data-ttu-id="f7211-143">**[SET DEADLOCK_PRIORITY]**</span><span class="sxs-lookup"><span data-stu-id="f7211-143">**SET DEADLOCK PRIORITY**</span></span>  
 <span data-ttu-id="f7211-144">既定値の [Normal] の場合、デッドロックが発生したときに各クエリに同じ優先度が与えられます。</span><span class="sxs-lookup"><span data-stu-id="f7211-144">The default value of Normal allows each query to have the same priority when a deadlock occurs.</span></span> <span data-ttu-id="f7211-145">このクエリが、デッドロックの競合で常に優先されずに終了するクエリとして選択されるようにするには、優先度に [Low] を選択してください。</span><span class="sxs-lookup"><span data-stu-id="f7211-145">Select a priority of Low if you want this query to lose any deadlock conflict and be selected as the query to be terminated.</span></span>  
  
 <span data-ttu-id="f7211-146">**[SET LOCK TIMEOUT]**</span><span class="sxs-lookup"><span data-stu-id="f7211-146">**SET LOCK TIMEOUT**</span></span>  
 <span data-ttu-id="f7211-147">既定値の -1 は、トランザクションが完了するまでロックが保持されることを示します。</span><span class="sxs-lookup"><span data-stu-id="f7211-147">The default value of -1 indicates that locks are held until transactions are completed.</span></span> <span data-ttu-id="f7211-148">値が 0 の場合は、待ち時間はありません。ロックがかかるとすぐにメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="f7211-148">A value of 0 means not to wait at all and return a message as soon as a lock is encountered.</span></span> <span data-ttu-id="f7211-149">トランザクションを終了するまでのロックを 0 ミリ秒よりも長く保持する必要がある場合は、0 より大きい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="f7211-149">Provide a value of greater than 0 milliseconds to terminate a transaction if the locks for transaction must be held for greater than that time.</span></span>  
  
 <span data-ttu-id="f7211-150">**[SET QUERY_GOVERNOR_COST_LIMIT]**</span><span class="sxs-lookup"><span data-stu-id="f7211-150">**SET QUERY_GOVERNOR_COST_LIMIT**</span></span>  
 <span data-ttu-id="f7211-151">**[QUERY_GOVERNOR_COST_LIMIT]** オプションは、クエリを実行できる時間の上限を指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="f7211-151">Use the **QUERY_GOVERNOR_COST_LIMIT** option to specify an upper limit for the time in which a query can run.</span></span> <span data-ttu-id="f7211-152">クエリ コストとは、特定のハードウェア構成でクエリを完了するために必要とされる予測所要時間を秒単位で表したものです。</span><span class="sxs-lookup"><span data-stu-id="f7211-152">Query cost refers to the estimated elapsed time, in seconds, required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="f7211-153">既定値の 0 は、クエリの実行に関して時間的制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f7211-153">The default setting of 0 indicates no limit to the length of time a query will run.</span></span>  
  
 <span data-ttu-id="f7211-154">**[プロバイダー メッセージ ヘッダーの禁止]**</span><span class="sxs-lookup"><span data-stu-id="f7211-154">**Suppress provider message headers**</span></span>  
 <span data-ttu-id="f7211-155">このチェック ボックスがオンの場合、プロバイダー (SQLClient プロバイダーなど) からの状態メッセージは表示されません。</span><span class="sxs-lookup"><span data-stu-id="f7211-155">When this check box is selected, status messages from the provider (such as the SQLClient provider) are not displayed.</span></span> <span data-ttu-id="f7211-156">既定では、このチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="f7211-156">This check box is selected by default.</span></span> <span data-ttu-id="f7211-157">プロバイダー レベルで失敗するクエリのトラブルシューティングを行うときにプロバイダー メッセージを表示するには、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="f7211-157">Clear this check box to see the provider messages when troubleshooting queries that may be failing at the provider level.</span></span>  
  
 <span data-ttu-id="f7211-158">**[クエリ実行後に切断]**</span><span class="sxs-lookup"><span data-stu-id="f7211-158">**Disconnect after the query executes**</span></span>  
 <span data-ttu-id="f7211-159">このチェック ボックスがオンの場合、クエリが完了した後に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] への接続が終了します。</span><span class="sxs-lookup"><span data-stu-id="f7211-159">When this check box is selected, the connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is terminated after the query completes.</span></span> <span data-ttu-id="f7211-160">既定では、このチェック ボックスはオフです。</span><span class="sxs-lookup"><span data-stu-id="f7211-160">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="f7211-161">**既定値にリセット**</span><span class="sxs-lookup"><span data-stu-id="f7211-161">**Reset to Default**</span></span>  
 <span data-ttu-id="f7211-162">このページ上のすべての値を元の既定値にリセットします。</span><span class="sxs-lookup"><span data-stu-id="f7211-162">Resets all values on this page to the original default values.</span></span>  
  
  
