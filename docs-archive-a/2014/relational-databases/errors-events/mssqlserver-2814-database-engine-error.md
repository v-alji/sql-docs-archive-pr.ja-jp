---
title: MSSQLSERVER_2814 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2814 (Database Engine error)
ms.assetid: 22800748-9be9-4511-9428-6b8b40e5bef9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26b1fae5b683ed72cb93c3f81981bd41e2f4ad4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641002"
---
# <a name="mssqlserver_2814"></a><span data-ttu-id="70d69-102">MSSQLSERVER_2814</span><span class="sxs-lookup"><span data-stu-id="70d69-102">MSSQLSERVER_2814</span></span>
    
## <a name="details"></a><span data-ttu-id="70d69-103">詳細</span><span class="sxs-lookup"><span data-stu-id="70d69-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70d69-104">製品名</span><span class="sxs-lookup"><span data-stu-id="70d69-104">Product Name</span></span>|<span data-ttu-id="70d69-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="70d69-105">SQL Server</span></span>|  
|<span data-ttu-id="70d69-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="70d69-106">Event ID</span></span>|<span data-ttu-id="70d69-107">2814</span><span class="sxs-lookup"><span data-stu-id="70d69-107">2814</span></span>|  
|<span data-ttu-id="70d69-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="70d69-108">Event Source</span></span>|<span data-ttu-id="70d69-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="70d69-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="70d69-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="70d69-110">Component</span></span>|<span data-ttu-id="70d69-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="70d69-111">SQLEngine</span></span>|  
|<span data-ttu-id="70d69-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="70d69-112">Symbolic Name</span></span>|<span data-ttu-id="70d69-113">PR_POSSIBLE_INFINITE_RECOMPILE</span><span class="sxs-lookup"><span data-stu-id="70d69-113">PR_POSSIBLE_INFINITE_RECOMPILE</span></span>|  
|<span data-ttu-id="70d69-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="70d69-114">Message Text</span></span>|<span data-ttu-id="70d69-115">SQLHANDLE %hs、PlanHandle %hs、開始オフセット %d、終了オフセット %d の再コンパイルが無限に行われる可能性があることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="70d69-115">A possible infinite recompile was detected for SQLHANDLE %hs, PlanHandle %hs, starting offset %d, ending offset %d.</span></span> <span data-ttu-id="70d69-116">前回の再コンパイルの理由は、%d でした。</span><span class="sxs-lookup"><span data-stu-id="70d69-116">The last recompile reason was %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="70d69-117">説明</span><span class="sxs-lookup"><span data-stu-id="70d69-117">Explanation</span></span>  
 <span data-ttu-id="70d69-118">1 つ以上のステートメントにより、クエリ バッチが少なくとも 50 回再コンパイルされました。</span><span class="sxs-lookup"><span data-stu-id="70d69-118">One or more statements caused the query batch to recompile at least 50 times.</span></span> <span data-ttu-id="70d69-119">指定したステートメントを修正し、これ以上再コンパイルされるのを回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70d69-119">The specified statement should be corrected to avoid further recompilations.</span></span>  
  
 <span data-ttu-id="70d69-120">次の表に、再コンパイルの理由を示します。</span><span class="sxs-lookup"><span data-stu-id="70d69-120">The following table lists the reasons for recompilation.</span></span>  
  
|<span data-ttu-id="70d69-121">理由コード</span><span class="sxs-lookup"><span data-stu-id="70d69-121">Reason code</span></span>|<span data-ttu-id="70d69-122">説明</span><span class="sxs-lookup"><span data-stu-id="70d69-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="70d69-123">1</span><span class="sxs-lookup"><span data-stu-id="70d69-123">1</span></span>|<span data-ttu-id="70d69-124">スキーマの変更</span><span class="sxs-lookup"><span data-stu-id="70d69-124">Schema changed</span></span>|  
|<span data-ttu-id="70d69-125">2</span><span class="sxs-lookup"><span data-stu-id="70d69-125">2</span></span>|<span data-ttu-id="70d69-126">統計の変更</span><span class="sxs-lookup"><span data-stu-id="70d69-126">Statistics changed</span></span>|  
|<span data-ttu-id="70d69-127">3</span><span class="sxs-lookup"><span data-stu-id="70d69-127">3</span></span>|<span data-ttu-id="70d69-128">コンパイルの遅延</span><span class="sxs-lookup"><span data-stu-id="70d69-128">Deferred compile</span></span>|  
|<span data-ttu-id="70d69-129">4</span><span class="sxs-lookup"><span data-stu-id="70d69-129">4</span></span>|<span data-ttu-id="70d69-130">Set オプションの変更</span><span class="sxs-lookup"><span data-stu-id="70d69-130">Set option changed</span></span>|  
|<span data-ttu-id="70d69-131">5</span><span class="sxs-lookup"><span data-stu-id="70d69-131">5</span></span>|<span data-ttu-id="70d69-132">Temp テーブルの変更</span><span class="sxs-lookup"><span data-stu-id="70d69-132">Temp table changed</span></span>|  
|<span data-ttu-id="70d69-133">6</span><span class="sxs-lookup"><span data-stu-id="70d69-133">6</span></span>|<span data-ttu-id="70d69-134">リモート行セットの変更</span><span class="sxs-lookup"><span data-stu-id="70d69-134">Remote rowset changed</span></span>|  
|<span data-ttu-id="70d69-135">7</span><span class="sxs-lookup"><span data-stu-id="70d69-135">7</span></span>|<span data-ttu-id="70d69-136">参照権限の変更</span><span class="sxs-lookup"><span data-stu-id="70d69-136">For Browse permissions changed</span></span>|  
|<span data-ttu-id="70d69-137">8</span><span class="sxs-lookup"><span data-stu-id="70d69-137">8</span></span>|<span data-ttu-id="70d69-138">クエリ通知環境の変更</span><span class="sxs-lookup"><span data-stu-id="70d69-138">Query notification environment changed</span></span>|  
|<span data-ttu-id="70d69-139">9</span><span class="sxs-lookup"><span data-stu-id="70d69-139">9</span></span>|<span data-ttu-id="70d69-140">パーティション ビューの変更</span><span class="sxs-lookup"><span data-stu-id="70d69-140">Partition view changed</span></span>|  
|<span data-ttu-id="70d69-141">10</span><span class="sxs-lookup"><span data-stu-id="70d69-141">10</span></span>|<span data-ttu-id="70d69-142">カーソル オプションの変更</span><span class="sxs-lookup"><span data-stu-id="70d69-142">Cursor options changed</span></span>|  
|<span data-ttu-id="70d69-143">11</span><span class="sxs-lookup"><span data-stu-id="70d69-143">11</span></span>|<span data-ttu-id="70d69-144">オプション (再コンパイル) の要求</span><span class="sxs-lookup"><span data-stu-id="70d69-144">Option (recompile) requested</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="70d69-145">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="70d69-145">User Action</span></span>  
  
1.  <span data-ttu-id="70d69-146">次のクエリを実行して、再コンパイルの原因になっているステートメントを確認します。</span><span class="sxs-lookup"><span data-stu-id="70d69-146">View the statement causing the recompilation by running the following query.</span></span> <span data-ttu-id="70d69-147">*sql_handle*、*starting_offset*、*ending_offset*、*plan_handle* の各プレースホルダーを、エラー メッセージで指定された値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="70d69-147">Replace the *sql_handle*, *starting_offset*, *ending_offset*, and *plan_handle* placeholders with the values specified in the error message.</span></span> <span data-ttu-id="70d69-148">**database_name** 列と **object_name** 列は、アドホックおよび準備された [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは NULL になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="70d69-148">Note that the **database_name** and **object_name** columns will be NULL for ad hoc and prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="70d69-149">SELECT DB_NAME(st.dbid) AS database_name</span><span class="sxs-lookup"><span data-stu-id="70d69-149">SELECT DB_NAME(st.dbid) AS database_name</span></span>  
  
     <span data-ttu-id="70d69-150">, OBJECT_NAME(st.objectid) AS object_name</span><span class="sxs-lookup"><span data-stu-id="70d69-150">, OBJECT_NAME(st.objectid) AS object_name</span></span>  
  
     <span data-ttu-id="70d69-151">, st.text</span><span class="sxs-lookup"><span data-stu-id="70d69-151">, st.text</span></span>  
  
     <span data-ttu-id="70d69-152">FROM sys.dm_exec_query_stats AS qs</span><span class="sxs-lookup"><span data-stu-id="70d69-152">FROM sys.dm_exec_query_stats AS qs</span></span>  
  
     <span data-ttu-id="70d69-153">CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st</span><span class="sxs-lookup"><span data-stu-id="70d69-153">CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st</span></span>  
  
     <span data-ttu-id="70d69-154">WHERE qs.statement_start_offset = *starting_offset*</span><span class="sxs-lookup"><span data-stu-id="70d69-154">WHERE qs.statement_start_offset = *starting_offset*</span></span>  
  
     <span data-ttu-id="70d69-155">AND qs.statement_end_offset = *ending_offset*</span><span class="sxs-lookup"><span data-stu-id="70d69-155">AND qs.statement_end_offset = *ending_offset*</span></span>  
  
     <span data-ttu-id="70d69-156">AND qs.plan_handle = *plan_handle*;</span><span class="sxs-lookup"><span data-stu-id="70d69-156">AND qs.plan_handle = *plan_handle*;</span></span>  
  
2.  <span data-ttu-id="70d69-157">理由コードの説明に基づいて、再コンパイルを回避するようにステートメント、バッチ、またはプロシージャを修正します。</span><span class="sxs-lookup"><span data-stu-id="70d69-157">Based on the reason code description, modify the statement, batch, or procedure to avoid recompilations.</span></span> <span data-ttu-id="70d69-158">たとえば、ストアド プロシージャに 1 つ以上の SET ステートメントが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="70d69-158">For example, a stored procedure may contain one or more SET statements.</span></span> <span data-ttu-id="70d69-159">これらのステートメントはプロシージャから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70d69-159">These statements should be removed from the procedure.</span></span> <span data-ttu-id="70d69-160">再コンパイルの理由と解決策のその他の例については、「[SQL Server 2005 のバッチのコンパイル、再コンパイル、およびプランのキャッシュに関する問題](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70d69-160">For additional examples of recompilation causes and resolutions, see [Batch Compilation, Recompilation, and Plan Caching Issues in SQL Server 2005](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10)).</span></span>  
  
3.  <span data-ttu-id="70d69-161">問題が継続して発生する場合は、マイクロソフト カスタマー サポート サービスに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="70d69-161">If the problem persists, contact Microsoft Customer Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d69-162">参照</span><span class="sxs-lookup"><span data-stu-id="70d69-162">See Also</span></span>  
 [<span data-ttu-id="70d69-163">SQL:StmtRecompile イベント クラス</span><span class="sxs-lookup"><span data-stu-id="70d69-163">SQL:StmtRecompile Event Class</span></span>](../event-classes/sql-stmtrecompile-event-class.md)  
  
  
