---
title: クエリのストアを使用した、パフォーマンスの監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e06344a4-22a5-4c67-b6c6-a7060deb5de6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e5d74b9c4def9c0314569a8d0bd87939cdcb11b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645002"
---
# <a name="monitoring-performance-by-using-the-query-store"></a><span data-ttu-id="b7a6a-102">クエリのストアを使用した、パフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="b7a6a-102">Monitoring Performance By Using the Query Store</span></span>
  <span data-ttu-id="b7a6a-103">クエリのストアの機能により、クエリ プランの選択やパフォーマンスに関する洞察が DBA に提供されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-103">The query store feature provides DBAs with insight on query plan choice and performance.</span></span> <span data-ttu-id="b7a6a-104">これにより、クエリ プランの変更によって生じるパフォーマンスの違いがすばやくわかるようになり、パフォーマンス上のトラブルシューティングを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-104">It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans.</span></span> <span data-ttu-id="b7a6a-105">この機能により、クエリ、プラン、ランタイム統計情報の履歴が自動的にキャプチャされ、レビュー用に保持されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-105">The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span> <span data-ttu-id="b7a6a-106">データは時間枠で区分されるため、データベースの使用パターンを表示して、サーバー上でクエリ プランが変わった時点を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-106">It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server.</span></span> <span data-ttu-id="b7a6a-107">クエリのストアは [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) オプションを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-107">The query store can be configured by using the [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) option.</span></span>

||
|-|
|<span data-ttu-id="b7a6a-108">**に適用さ**れます: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([取得](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag))。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-108">**Applies to**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([Get it](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span></span>|

> [!IMPORTANT]
>  <span data-ttu-id="b7a6a-109">現在、これはプレビュー機能です。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-109">This is currently a preview feature.</span></span> <span data-ttu-id="b7a6a-110">使用するクエリ ストアを確認して、クエリのストアの実装に同意する必要がありますが、プレビューの条項に従ってその適切なライセンス契約 (など、エンタープライズ契約、Microsoft Azure 契約、または Microsoft Online サブスクリプション契約) に [補足使用条件の Microsoft Azure プレビュー](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)です。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-110">To use the Query Store you must acknowledge and agree that implementation of Query Store is subject to the preview terms in your license agreement (e.g. the Enterprise Agreement, Microsoft Azure Agreement, or Microsoft Online Subscription Agreement), as well as any applicable [Supplemental Terms of Use for Microsoft Azure Preview](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).</span></span>

##  <a name="enabling-the-query-store"></a><a name="Enabling"></a> <span data-ttu-id="b7a6a-111">クエリのストアを有効にする</span><span class="sxs-lookup"><span data-stu-id="b7a6a-111">Enabling the Query Store</span></span>
 <span data-ttu-id="b7a6a-112">既定では、クエリのストアは新しいデータベースに対してアクティブではありません。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-112">Query Store is not active for new databases by default.</span></span>

#### <a name="by-using-the-query-store-page-in-management-studio"></a><span data-ttu-id="b7a6a-113">Management Studio でクエリのストアのページを使用する方法</span><span class="sxs-lookup"><span data-stu-id="b7a6a-113">By Using the Query Store Page in Management Studio</span></span>

1.  <span data-ttu-id="b7a6a-114">オブジェクト エクスプローラーで、データベースを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-114">In Object Explorer, right-click a database, and then click **Properties**.</span></span> <span data-ttu-id="b7a6a-115">( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2016 バージョンの [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]が必要)。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-115">(Requires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2016 version of [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].)</span></span>

2.  <span data-ttu-id="b7a6a-116">**[データベースのプロパティ]** ダイアログ ボックスで、 **[クエリのストア]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-116">In the **Database Properties** dialog box, select the **Query Store** page.</span></span>

3.  <span data-ttu-id="b7a6a-117">**[有効にする]** ボックスで、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-117">In the **Enable** box, select **True**.</span></span>

#### <a name="by-using-transact-sql-statements"></a><span data-ttu-id="b7a6a-118">Transact-SQL ステートメントを使用する方法</span><span class="sxs-lookup"><span data-stu-id="b7a6a-118">By Using Transact-SQL Statements</span></span>

1.  <span data-ttu-id="b7a6a-119">`ALTER DATABASE` ステートメントを使用してクエリのストアを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-119">Use the `ALTER DATABASE` statement to enable the query store.</span></span> <span data-ttu-id="b7a6a-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-120">For example:</span></span>

    ```
    ALTER DATABASE AdventureWorks2012 SET QUERY_STORE = ON;
    ```

     <span data-ttu-id="b7a6a-121">クエリストアに関連するその他の構文オプションについては、「 [ALTER DATABASE SET options &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-121">For more syntax options related to the query store, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>

> [!NOTE]
>  <span data-ttu-id="b7a6a-122">マスター データベースに対しては、クエリのストアを有効にできません。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-122">You cannot enable the query store for the master database.</span></span>



##  <a name="information-in-the-query-store"></a><a name="About"></a> <span data-ttu-id="b7a6a-123">クエリのストア内の情報</span><span class="sxs-lookup"><span data-stu-id="b7a6a-123">Information in the Query Store</span></span>
 <span data-ttu-id="b7a6a-124">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のどの特定のクエリの実行プランも、通常、統計情報やスキーマの変更、インデックスの作成または削除などのさまざまな理由により、時間の経過とともに進化します。プロシージャ キャッシュ (ここにキャッシュされたクエリ プランが格納される) には、最新の実行プランのみ格納されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-124">Execution plans for any specific query in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] typically evolve over time due to a number of different reasons such as statistics changes, schema changes, creation/deletion of indexes, etc. The procedure cache (where cached query plans are stored) only stores the latest execution plan.</span></span> <span data-ttu-id="b7a6a-125">メモリ負荷が原因で、プランがプラン キャッシュから削除されることもあります。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-125">Plans also get evicted from the plan cache due to memory pressure.</span></span> <span data-ttu-id="b7a6a-126">その結果、実行プランの変更によるクエリ パフォーマンスの低下が深刻なレベルになり、解決に時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-126">As a result, query performance regressions caused by execution plan changes can be non-trivial and time consuming to resolve.</span></span>

 <span data-ttu-id="b7a6a-127">クエリのストアには、1 つのクエリにつき複数の実行プランが保持されるため、クエリの特定の実行プランを使用するようクエリ プロセッサに指示するポリシーを強制できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-127">Since the query store retains multiple execution plans per query, it can enforce policies to direct the query processor to use a specific execution plan for a query.</span></span> <span data-ttu-id="b7a6a-128">これをプラン強制と呼びます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-128">This is referred to as plan forcing.</span></span> <span data-ttu-id="b7a6a-129">クエリのストアのプラン強制は、 [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) クエリ ヒントに似たメカニズムを使用して提供されますが、ユーザー アプリケーションを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-129">Plan forcing in Query Store is provided by using a mechanism similar to the [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) query hint, but it does not require any change in user applications.</span></span> <span data-ttu-id="b7a6a-130">プラン強制を使用することで、プラン変更によるクエリ パフォーマンスの低下をきわめて短時間に解決できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-130">Plan forcing can resolve a query performance regression caused by a plan change in a very short period of time.</span></span>

 <span data-ttu-id="b7a6a-131">このクエリのストアの機能を使用する一般的なシナリオは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-131">Common scenarios for using the Query Store feature are:</span></span>

-   <span data-ttu-id="b7a6a-132">前のクエリ プランを強制的に適用することにより、プラン パフォーマンスの低下をすばやく発見し修正します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-132">Quickly find and fix a plan performance regression by forcing the previous query plan.</span></span> <span data-ttu-id="b7a6a-133">実行プランの変更によって最近パフォーマンスが低下したクエリを修正します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-133">Fix queries that have recently regressed in performance due to execution plan changes.</span></span>

-   <span data-ttu-id="b7a6a-134">特定の時間枠内にクエリが実行された回数を確認し、パフォーマンス リソースの問題に関するトラブルシューティングにおいて DBA を支援します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-134">Determine the number of times a query was executed in a given time window, assisting a DBA in troubleshooting performance resource problems.</span></span>

-   <span data-ttu-id="b7a6a-135">上位 *n* クエリ (過去 *x* 時間内) を、実行時間やメモリ消費量などを基に識別します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-135">Identify top *n* queries (by execution time, memory consumption, etc.) in the past *x* hours.</span></span>

-   <span data-ttu-id="b7a6a-136">指定したクエリのクエリ プランの履歴を監査します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-136">Audit the history of query plans for a given query.</span></span>

-   <span data-ttu-id="b7a6a-137">特定のデータベースのリソース (CPU、I/O、メモリ) の使用パターンを分析します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-137">Analyze the resource (CPU, I/O, and Memory) usage patterns for a particular database.</span></span>

 <span data-ttu-id="b7a6a-138">クエリのストアには、次の&2; つのストアが含まれています。 **プラン ストア** は実行プラン情報を保持し、 **ランタイム統計情報ストア** は実行統計情報を保持するためのものです。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-138">The query store contains two stores; a **plan store** for persisting the execution plan information, and a **runtime stats store** for persisting the execution statistics information.</span></span> <span data-ttu-id="b7a6a-139">クエリのためにプラン ストア内に格納できる一意のプラン数は、`max_plans_per_query` 構成オプションによって制限されています。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-139">The number of unique plans that can be stored for a query in the plan store is limited by the `max_plans_per_query` configuration option.</span></span> <span data-ttu-id="b7a6a-140">パフォーマンスを向上させるために、この情報は つのストアに非同期的に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-140">To enhance performance, the information is written to the two stores asynchronously.</span></span> <span data-ttu-id="b7a6a-141">領域使用量を最小にするため、ランタイム統計情報ストアのランタイム実行統計情報は、一定の時間枠で集計されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-141">To minimize space usage, the runtime execution statistics in the runtime stats store are aggregated over a fixed time window.</span></span> <span data-ttu-id="b7a6a-142">これらのストア内の情報は、クエリのストアのカタログ ビューに対してクエリを実行することによって表示できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-142">The information in these stores is visible by querying the query store catalog views.</span></span>

 <span data-ttu-id="b7a6a-143">次のクエリは、クエリのストア内のクエリとプランに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-143">The following query returns information about queries and plans in the query store.</span></span>

```
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
FROM sys.query_store_plan AS Pl
JOIN sys.query_store_query AS Qry
    ON Pl.query_id = Qry.query_id
JOIN sys.query_store_query_text AS Txt
    ON Qry.query_text_id = Txt.query_text_id ;
```



## <a name="using-the-regressed-queries-feature"></a><span data-ttu-id="b7a6a-144">機能低下したクエリ機能の使用</span><span class="sxs-lookup"><span data-stu-id="b7a6a-144">Using the Regressed Queries Feature</span></span>
 <span data-ttu-id="b7a6a-145">クエリストアを有効にした後、[オブジェクトエクスプローラー] ウィンドウのデータベース部分を更新して**クエリストア**セクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-145">After enabling the query store, refresh the database portion of the Object Explorer pane to add the **Query Store** section.</span></span>

 <span data-ttu-id="b7a6a-146">![QueryStore](../../database-engine/media/querystore.PNG "QueryStore")</span><span class="sxs-lookup"><span data-stu-id="b7a6a-146">![QueryStore](../../database-engine/media/querystore.PNG "QueryStore")</span></span>

 <span data-ttu-id="b7a6a-147">**[機能低下したクエリ]** を選択し、 **で** [機能低下したクエリ] [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-147">Selecting **Regressed Queries**, opens the **Regressed Queries** pane in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="b7a6a-148">[機能低下したクエリ] ペインにクエリと、クエリのストア内のプランが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-148">The Regressed Queries pane shows you the queries, and plans in the query store.</span></span> <span data-ttu-id="b7a6a-149">上部にあるドロップダウン ボックスを使用すると、さまざまな条件に合わせてクエリを選択できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-149">Drop down boxes at the top allow you to select queries based on various criteria.</span></span> <span data-ttu-id="b7a6a-150">プランを選択して、グラフィカルなクエリ プランを表示します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-150">Select a plan to see the graphical query plan.</span></span> <span data-ttu-id="b7a6a-151">ソース クエリの表示、クエリ プランの強制と強制解除、表示の更新に使用できるボタンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-151">Buttons are available to view the source query, force, and unforce a query plan, and refresh the display.</span></span>

 <span data-ttu-id="b7a6a-152">![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")</span><span class="sxs-lookup"><span data-stu-id="b7a6a-152">![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")</span></span>

 <span data-ttu-id="b7a6a-153">プランを強制するには、クエリとプランを選択し、[プランの強制] をクリックし**ます。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-153">To force a plan, select a query and plan, and then click **Force Plan.**</span></span> <span data-ttu-id="b7a6a-154">強制できるプランは、クエリ プランの機能によって保存され、クエリ プランのキャッシュに保持されているプランのみです。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-154">You can only force plans that were saved by the query plan feature and are still retained in the query plan cache.</span></span>



##  <a name="configuration-options"></a><a name="Options"></a> <span data-ttu-id="b7a6a-155">構成オプション</span><span class="sxs-lookup"><span data-stu-id="b7a6a-155">Configuration Options</span></span>
 <span data-ttu-id="b7a6a-156">OPERATION_MODE は、READ_WRITE または READ_ONLY できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-156">OPERATION_MODE Can be READ_WRITE or READ_ONLY.</span></span>

 <span data-ttu-id="b7a6a-157">CLEANUP_POLICY STALE_QUERY_THRESHOLD_DAYS 引数を構成して、クエリストアにデータを保持する日数を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-157">CLEANUP_POLICY Configure the STALE_QUERY_THRESHOLD_DAYS argument to specify the number of days to retain data in the query store.</span></span>

 <span data-ttu-id="b7a6a-158">DATA_FLUSH_INTERVAL_SECONDS: クエリ ストアに書き込まれるデータがディスクに永続化される頻度を示します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-158">DATA_FLUSH_INTERVAL_SECONDS Determines the frequency at which data written to the query store is persisted to disk.</span></span> <span data-ttu-id="b7a6a-159">パフォーマンスを最適化するため、クエリ ストアで収集したデータは非同期的にディスクに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-159">To optimize for performance, data collected by the query store is asynchronously written to the disk.</span></span> <span data-ttu-id="b7a6a-160">この非同期転送が発生する頻度は、DATA_FLUSH_INTERVAL_SECONDS 引数を介して構成されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-160">The frequency at which this asynchronous transfer occurs is configured via DATA_FLUSH_INTERVAL_SECONDS.</span></span>

 <span data-ttu-id="b7a6a-161">MAX_SIZE_MB クエリストアの最大サイズを構成します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-161">MAX_SIZE_MB Configures the maximum size of the query store.</span></span> <span data-ttu-id="b7a6a-162">クエリのストア内のデータが MAX_SIZE_MB の上限に達すると、クエリのストアは自動的に状態を読み取り/書き込みから読み取り専用に変更し、新しいデータの収集を停止します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-162">If the data in the query store hits the MAX_SIZE_MB limit, the query store automatically changes the state from read-write to read-only and stops collecting new data.</span></span>

 <span data-ttu-id="b7a6a-163">INTERVAL_LENGTH_MINUTES: クエリのストアにランタイムの実行の統計データを集計する時間間隔を示します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-163">INTERVAL_LENGTH_MINUTES Determines the time interval at which runtime execution statistics data is aggregated into the query store.</span></span> <span data-ttu-id="b7a6a-164">領域使用量を最適化するため、ランタイム統計情報ストアのランタイム実行統計情報は、一定の時間枠で集計されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-164">To optimize for space usage, the runtime execution statistics in the Runtime Stats Store are aggregated over a fixed time window.</span></span> <span data-ttu-id="b7a6a-165">この固定された時間枠は、INTERVAL_LENGTH_MINUTES 引数を介して構成されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-165">This fixed time window is configured via INTERVAL_LENGTH_MINUTES.</span></span>

 <span data-ttu-id="b7a6a-166">`sys.database_query_store_options` ビューにクエリを実行し、クエリのストアの現在のオプションを確認します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-166">Query the `sys.database_query_store_options` view to determine the current options of the query store.</span></span>

 <span data-ttu-id="b7a6a-167">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用してオプションを設定する方法の詳細については、「 [オプション管理](#OptionMgmt)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-167">For more information about setting options by using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, see [Option Management](#OptionMgmt).</span></span>

 

##  <a name="related-views-functions-and-procedures"></a><a name="Related"></a> <span data-ttu-id="b7a6a-168">関連するビュー、関数、プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b7a6a-168">Related Views, Functions, and Procedures</span></span>
 <span data-ttu-id="b7a6a-169">クエリのストアは、 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] か、次のビューとプロシージャを使用して表示および管理できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-169">The Query Store can be viewed and managed through [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] or by using the following views and procedures.</span></span>

-   [<span data-ttu-id="b7a6a-170">sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-170">sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql)

### <a name="query-store-catalog-views"></a><span data-ttu-id="b7a6a-171">クエリのストアのカタログ ビュー</span><span class="sxs-lookup"><span data-stu-id="b7a6a-171">Query Store Catalog Views</span></span>
 <span data-ttu-id="b7a6a-172">7 種類のカタログ ビューがクエリのストアの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-172">Seven catalog views present information about the Query Store.</span></span>

-   [<span data-ttu-id="b7a6a-173">sys.database_query_store_options &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-173">sys.database_query_store_options &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql)

-   [<span data-ttu-id="b7a6a-174">sys.query_context_settings &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-174">sys.query_context_settings &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-context-settings-transact-sql)

-   [<span data-ttu-id="b7a6a-175">sys.query_store_plan &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-175">sys.query_store_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-plan-transact-sql)

-   [<span data-ttu-id="b7a6a-176">sys.query_store_query &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-176">sys.query_store_query &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-query-transact-sql)

-   [<span data-ttu-id="b7a6a-177">sys.query_store_query_text &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-177">sys.query_store_query_text &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql)

-   [<span data-ttu-id="b7a6a-178">sys.query_store_runtime_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-178">sys.query_store_runtime_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql)

-   [<span data-ttu-id="b7a6a-179">sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-179">sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql)

### <a name="query-store-stored-procedures"></a><span data-ttu-id="b7a6a-180">クエリのストアのストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b7a6a-180">Query Store Stored Procedures</span></span>
 <span data-ttu-id="b7a6a-181">6 つのストアド プロシージャがクエリのストアを構成します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-181">Six stored procedures configure the Query Store.</span></span>

-   [<span data-ttu-id="b7a6a-182">sp_query_store_flush_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-182">sp_query_store_flush_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql)

-   [<span data-ttu-id="b7a6a-183">sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-183">sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql)

-   [<span data-ttu-id="b7a6a-184">sp_query_store_force_plan &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-184">sp_query_store_force_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql)

-   [<span data-ttu-id="b7a6a-185">sp_query_store_unforce_plan &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-185">sp_query_store_unforce_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql)

-   [<span data-ttu-id="b7a6a-186">sp_query_store_remove_plan &#40;Transct-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-186">sp_query_store_remove_plan &#40;Transct-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql)

-   [<span data-ttu-id="b7a6a-187">sp_query_store_remove_query &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7a6a-187">sp_query_store_remove_query &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql)



##  <a name="key-usage-scenarios"></a><a name="Scenarios"></a> <span data-ttu-id="b7a6a-188">基本的な使用シナリオ</span><span class="sxs-lookup"><span data-stu-id="b7a6a-188">Key Usage Scenarios</span></span>

###  <a name="option-management"></a><a name="OptionMgmt"></a> <span data-ttu-id="b7a6a-189">オプション管理</span><span class="sxs-lookup"><span data-stu-id="b7a6a-189">Option Management</span></span>
 <span data-ttu-id="b7a6a-190">このセクションでは、クエリのストアの機能自体を管理する方法に関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-190">This section provides some guidelines on managing Query Store feature itself.</span></span>

 <span data-ttu-id="b7a6a-191">**クエリのストアが現在アクティブか**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-191">**Is Query Store currently active?**</span></span>

 <span data-ttu-id="b7a6a-192">クエリのストアはユーザー データベース内にデータを格納するため、サイズに上限が設定されています (`MAX_STORAGE_SIZE_MB` で構成)。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-192">Query Store stores its data inside the user database and that is why it has size limit (configured  with `MAX_STORAGE_SIZE_MB`).</span></span> <span data-ttu-id="b7a6a-193">クエリのストア内のデータがその上限に達すると、クエリのストアは自動的に状態を読み取り/書き込みから読み取り専用に変更し、新しいデータの収集を停止します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-193">If data in Query Store hits that limit Query Store will automatically change state from read-write to read-only and stop collecting new data.</span></span>

 <span data-ttu-id="b7a6a-194">次のスクリプトを実行して、クエリのストアが現在アクティブであるか、また、ランタイム統計情報を現在収集しているかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-194">Execute the following script to determine if Query Store is currently active, and whether it is currently collects runtime stats or not.</span></span>

```
DECLARE @x nvarchar(100) = CAST(newid() AS nvarchar(100));
DECLARE @query nvarchar(max) = 
N'IF EXISTS
(
    SELECT * 
    FROM sys.query_store_query_text 
    WHERE query_sql_text LIKE ''%' + @x + N'%''
)
SELECT ''Query Store is active'' ;
ELSE SELECT ''Query Store is NOT active''' ;
EXEC sp_executesql @query;
```

 <span data-ttu-id="b7a6a-195">**クエリのストアのオプションを取得する**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-195">**Get Query Store options**</span></span>

 <span data-ttu-id="b7a6a-196">クエリのストアの状態に関する詳細情報については、ユーザー データベースで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-196">To find out detailed information about Query Store status, execute following in a user database.</span></span>

```
SELECT * FROM sys.database_query_store_options;
```

 <span data-ttu-id="b7a6a-197">**クエリのストアの時間間隔を設定する**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-197">**Setting Query Store interval**</span></span>

 <span data-ttu-id="b7a6a-198">クエリのランタイム統計情報を集計する時間間隔 (既定では 60 分) をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-198">You can override interval for aggregating query runtime statistics (default is 60 minutes).</span></span>

```

      USE master;
GO

ALTER DATABASE <database_name> 
SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 15);
```

 <span data-ttu-id="b7a6a-199">任意の値は許可されていません。1、5、10、15、30、60 のいずれかの値を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-199">Note that arbitrary values are not allowed - you should use one of the following: 1, 5, 10, 15, 30 and 60.</span></span>

 <span data-ttu-id="b7a6a-200">時間間隔に使用する新しい値は、`sys.database_query_store_options` ビューで公開されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-200">New value for interval is exposed through `sys.database_query_store_options` view.</span></span>

 <span data-ttu-id="b7a6a-201">クエリのストアの記憶域がいっぱいの場合は、次のステートメントを使用して記憶域を拡張します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-201">If the Query Store storage is full use the following statement to extend the storage.</span></span>

```
ALTER DATABASE <database_name> 
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <new_size>);
```

 <span data-ttu-id="b7a6a-202">**クエリのストアのオプションをすべて設定する**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-202">**Set all Query Store options**</span></span>

 <span data-ttu-id="b7a6a-203">単一の ALTER DATABASE ステートメントで、クエリのストアの複数のオプションを一度にまとめて設定できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-203">You can set multiple Query Store options at once with a single ALTER DATABASE statement.</span></span>

```
ALTER DATABASE <database name> 
SET QUERY_STORE (
    OPERATION_MODE = READ_WRITE,
    CLEANUP_POLICY = 
    (STALE_QUERY_THRESHOLD_DAYS = 30),
    DATA_FLUSH_INTERVAL_SECONDS = 3000,
    MAX_STORAGE_SIZE_MB = 500,
    INTERVAL_LENGTH_MINUTES = 15
);
```

 <span data-ttu-id="b7a6a-204">**領域のクリーンアップ**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-204">**Cleaning up the space**</span></span>

 <span data-ttu-id="b7a6a-205">クエリのストアの内部テーブルは、データベースの作成時に PRIMARY ファイル グループに作成され、その構成を後で変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-205">Query Store internal tables are created in the PRIMARY filegroup during database creation and that configuration cannot be changed later.</span></span> <span data-ttu-id="b7a6a-206">領域が不足している場合は、次のステートメントを使用して、古いクエリのストアのデータを消去できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-206">If you are running out of space you might want to clear older Query Store data by using the following statement.</span></span>

```
ALTER DATABASE <db_name> SET QUERY_STORE CLEAR;
```

 <span data-ttu-id="b7a6a-207">または、アドホック クエリ データはクエリの最適化やプラン分析との関連性が低く、ただ場所を占有するだけなので、アドホック クエリ データのみを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-207">Alternatively, you might want to clear up only ad-hoc query data, since it is less relevant for query optimizations and plan analysis but takes up just as much space.</span></span>

 <span data-ttu-id="b7a6a-208">**アドホック クエリの削除** : この操作は、24 時間以上前に 1 回実行しただけのクエリを削除します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-208">**Delete ad-hoc queries** This deletes the queries that were only executed only once and that are more than 24 hours old.</span></span>

```
DECLARE @id int
DECLARE adhoc_queries_cursor CURSOR 
FOR 
SELECT q.query_id
FROM sys.query_store_query_text AS qt
JOIN sys.query_store_query AS q 
    ON q.query_text_id = qt.query_text_id
JOIN sys.query_store_plan AS p 
    ON p.query_id = q.query_id
JOIN sys.query_store_runtime_stats AS rs 
    ON rs.plan_id = p.plan_id
GROUP BY q.query_id
HAVING SUM(rs.count_executions) < 2 
AND MAX(rs.last_execution_time) < DATEADD (hour, -24, GETUTCDATE())
ORDER BY q.query_id ;

OPEN adhoc_queries_cursor ;
FETCH NEXT FROM adhoc_queries_cursor INTO @id;
WHILE @@fetch_status = 0
    BEGIN 
        PRINT @id
        EXEC sp_query_store_remove_query @id
        FETCH NEXT FROM adhoc_queries_cursor INTO @id
    END 
CLOSE adhoc_queries_cursor ;
DEALLOCATE adhoc_queries_cursor;
```

 <span data-ttu-id="b7a6a-209">不要になったデータを消去する別のロジックを利用した独自のプロシージャを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-209">You can define your own procedure with different logic for clearing up the data that is no longer important for you.</span></span>

 <span data-ttu-id="b7a6a-210">上記の例では、`sp_query_store_remove_query` 拡張ストアド プロシージャを使用して不要なデータを削除しています。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-210">The example above uses the `sp_query_store_remove_query` extended stored procedure for removing unnecessary data.</span></span> <span data-ttu-id="b7a6a-211">さらに、別の 2 つのプロシージャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-211">You can also use two other procedures.</span></span>

-   <span data-ttu-id="b7a6a-212">`sp_query_store_reset_exec_stats`-指定されたプランの実行時統計をクリアします。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-212">`sp_query_store_reset_exec_stats` - clear runtime statistics for a given plan.</span></span>

-   <span data-ttu-id="b7a6a-213">`sp_query_store_remove_plan`-1 つのプランを削除します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-213">`sp_query_store_remove_plan` - removes a single plan.</span></span>



###  <a name="performance-auditing-and-troubleshooting"></a><a name="Peformance"></a> <span data-ttu-id="b7a6a-214">パフォーマンスの監査とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b7a6a-214">Performance Auditing and Troubleshooting</span></span>
 <span data-ttu-id="b7a6a-215">クエリのストアには、コンパイルの履歴とクエリの実行全体に関するランタイム メトリックスが保持されているため、ワークロードに関連した多くの疑問の答えを簡単に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-215">Because Query Store keeps history of compilation and runtime metrics throughout query executions there are many different questions you can easily answer with regards to your workload.</span></span>

 <span data-ttu-id="b7a6a-216">**データベースで実行された最後の*n 個*のクエリ。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-216">**Last *n* queries executed on the database.**</span></span>

```
SELECT TOP 10 qt.query_sql_text, q.query_id, 
    qt.query_text_id, p.plan_id, rs.last_execution_time
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
ORDER BY rs.last_execution_time DESC;
```

 <span data-ttu-id="b7a6a-217">**各クエリの実行回数。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-217">**Number of executions for each query.**</span></span>

```
SELECT q.query_id, qt.query_text_id, qt.query_sql_text, 
    SUM(rs.count_executions) AS total_execution_count
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
GROUP BY q.query_id, qt.query_text_id, qt.query_sql_text
ORDER BY total_execution_count DESC;
```

 <span data-ttu-id="b7a6a-218">**過去1時間以内に平均実行時間が最も長いクエリの数。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-218">**The number of queries with the longest average execution time within last hour.**</span></span>

```
SELECT TOP 10 rs.avg_duration, qt.query_sql_text, q.query_id,
    qt.query_text_id, p.plan_id, GETUTCDATE() AS CurrentUTCTime, 
    rs.last_execution_time 
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
WHERE rs.last_execution_time > DATEADD(hour, -1, GETUTCDATE())
ORDER BY rs.avg_duration DESC;
```

 <span data-ttu-id="b7a6a-219">**過去24時間に発生した平均物理 IO 読み取り数が、対応する平均行数と実行回数であるクエリの数。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-219">**The number of queries that had the biggest average physical IO reads in last 24 hours, with corresponding average row count and execution count.**</span></span>

```
SELECT TOP 10 rs.avg_physical_io_reads, qt.query_sql_text, 
    q.query_id, qt.query_text_id, p.plan_id, rs.runtime_stats_id, 
    rsi.start_time, rsi.end_time, rs.avg_rowcount, rs.count_executions
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi 
    ON rsi.runtime_stats_interval_id = rs.runtime_stats_interval_id
WHERE rsi.start_time >= DATEADD(hour, -24, GETUTCDATE()) 
ORDER BY rs.avg_physical_io_reads DESC;
```

 <span data-ttu-id="b7a6a-220">**複数のプランを持つクエリ。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-220">**Queries with multiple plans.**</span></span> <span data-ttu-id="b7a6a-221">これらは、プラン選択の変更による機能低下の原因になりうるため、特に興味深いクエリです。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-221">These queries are especially interesting because they are candidates for regressions due to plan choice change.</span></span> <span data-ttu-id="b7a6a-222">次のクエリは、これらのクエリとすべてのプランを識別します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-222">The following query identifies these queries along with all plans:</span></span>

```
WITH Query_MultPlans
AS
(
    SELECT COUNT(*) AS cnt, q.query_id 
    FROM sys.query_store_query_text AS qt
    JOIN sys.query_store_query AS q
        ON qt.query_text_id = q.query_text_id
    JOIN sys.query_store_plan AS p
        ON p.query_id = q.query_id
    GROUP BY q.query_id
    HAVING COUNT(distinct plan_id) > 1
)

SELECT q.query_id, object_name(object_id) AS ContainingObject, query_sql_text,
plan_id, p.query_plan AS plan_xml,
p.last_compile_start_time, p.last_execution_time
FROM Query_MultPlans AS qm
JOIN sys.query_store_query AS q
    ON qm.query_id = q.query_id
JOIN sys.query_store_plan AS p
    ON q.query_id = p.query_id
JOIN sys.query_store_query_text qt 
    ON qt.query_text_id = q.query_text_id
ORDER BY query_id, plan_id;
```

 <span data-ttu-id="b7a6a-223">**最近パフォーマンスが低下したされた (異なる時点を比較する) クエリ。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-223">**Queries that recently regressed in performance (comparing different point in time).**</span></span> <span data-ttu-id="b7a6a-224">次のクエリの例では、プラン選択の変更により、過去 48 時間で実行時間が 2 倍になったすべてのクエリを返します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-224">The following query example returns all queries for which execution time doubled in last 48 hours due to a plan choice change.</span></span> <span data-ttu-id="b7a6a-225">次のクエリは、すべてのランタイム統計情報の時間間隔を並べて比較します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-225">Query compares all runtime stat intervals side by side.</span></span>

```
SELECT 
    qt.query_sql_text, 
    q.query_id, 
    qt.query_text_id, 
    rs1.runtime_stats_id AS runtime_stats_id_1,
    rsi1.start_time AS interval_1, 
    p1.plan_id AS plan_1, 
    rs1.avg_duration AS avg_duration_1, 
    rs2.avg_duration AS avg_duration_2,
    p2.plan_id AS plan_2, 
    rsi2.start_time AS interval_2, 
    rs2.runtime_stats_id AS runtime_stats_id_2
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p1 
    ON q.query_id = p1.query_id 
JOIN sys.query_store_runtime_stats AS rs1 
    ON p1.plan_id = rs1.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi1 
    ON rsi1.runtime_stats_interval_id = rs1.runtime_stats_interval_id 
JOIN sys.query_store_plan AS p2 
    ON q.query_id = p2.query_id 
JOIN sys.query_store_runtime_stats AS rs2 
    ON p2.plan_id = rs2.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi2 
    ON rsi2.runtime_stats_interval_id = rs2.runtime_stats_interval_id
WHERE rsi1.start_time > DATEADD(hour, -48, GETUTCDATE()) 
    AND rsi2.start_time > rsi1.start_time 
    AND p1.plan_id <> p2.plan_id
    AND rs2.avg_duration > 2*rs1.avg_duration
ORDER BY q.query_id, rsi1.start_time, rsi2.start_time;
```

 <span data-ttu-id="b7a6a-226">プラン選択の変更に関連するものだけでなく、パフォーマンス低下に関するすべての情報を表示する場合、前のクエリから条件 `AND p1.plan_id <> p2.plan_id` を削除します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-226">If you want to see performance all regressions (not only those related to plan choice change) than just remove condition `AND p1.plan_id <> p2.plan_id` from the previous query.</span></span>

 <span data-ttu-id="b7a6a-227">**最近パフォーマンスに低下したしたクエリ (最近の実行と履歴の実行を比較)。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-227">**Queries that recently regressed in performance (comparing recent vs. history execution).**</span></span> <span data-ttu-id="b7a6a-228">次のクエリは、実行期間に基づいてクエリの実行を比較します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-228">The next query compares query execution based periods of execution.</span></span> <span data-ttu-id="b7a6a-229">この例では、クエリは、最近の期間 (1 時間) と履歴の期間 (過去 1 日間) とで実行を比較し、additional_duration_workload の原因となったものを識別します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-229">In this particular example the query compares execution in recent period (1 hour) vs. history period (last day) and identifies those that introduced additional_duration_workload.</span></span> <span data-ttu-id="b7a6a-230">このメトリックは、最近の平均実行と履歴の平均実行に最近実行の数を掛けた値の間の差として計算されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-230">This metrics is calculated as a difference between recent average execution and history average execution multiplied by the number of recent executions.</span></span> <span data-ttu-id="b7a6a-231">これは、履歴と比較して、最近の実行でどれほどの期間が追加されたかを表します。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-231">It actually represents how much of additional duration recent executions introduced compared to history:</span></span>

```
--- "Recent" workload - last 1 hour
DECLARE @recent_start_time datetimeoffset;
DECLARE @recent_end_time datetimeoffset;
SET @recent_start_time = DATEADD(hour, -1, SYSUTCDATETIME());
SET @recent_end_time = SYSUTCDATETIME();

--- "History" workload
DECLARE @history_start_time datetimeoffset;
DECLARE @history_end_time datetimeoffset;
SET @history_start_time = DATEADD(hour, -24, SYSUTCDATETIME());
SET @history_end_time = SYSUTCDATETIME();

WITH
hist AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
     FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @history_start_time AND rs.last_execution_time < @history_end_time)
        OR (rs.first_execution_time <= @history_start_time AND rs.last_execution_time > @history_start_time)
        OR (rs.first_execution_time <= @history_end_time AND rs.last_execution_time > @history_end_time)
    GROUP BY p.query_id
),
recent AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
    FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @recent_start_time AND rs.last_execution_time < @recent_end_time)
        OR (rs.first_execution_time <= @recent_start_time AND rs.last_execution_time > @recent_start_time)
        OR (rs.first_execution_time <= @recent_end_time AND rs.last_execution_time > @recent_end_time)
    GROUP BY p.query_id
)
SELECT 
    results.query_id query_id,
    results.query_text query_text,
    results.additional_duration_workload additional_duration_workload,
    results.total_duration_recent total_duration_recent,
    results.total_duration_hist total_duration_hist,
    ISNULL(results.count_executions_recent, 0) count_executions_recent,
    ISNULL(results.count_executions_hist, 0) count_executions_hist 
FROM
(
    SELECT
        hist.query_id query_id,
        qt.query_sql_text query_text,
        ROUND(CONVERT(float, recent.total_duration/recent.count_executions-hist.total_duration/hist.count_executions)*(recent.count_executions), 2) AS additional_duration_workload,
        ROUND(recent.total_duration, 2) total_duration_recent, 
        ROUND(hist.total_duration, 2) total_duration_hist,
        recent.count_executions count_executions_recent,
        hist.count_executions count_executions_hist   
    FROM hist 
        JOIN recent 
            ON hist.query_id = recent.query_id 
        JOIN sys.query_store_query AS q 
            ON q.query_id = hist.query_id
        JOIN sys.query_store_query_text AS qt 
            ON q.query_text_id = qt.query_text_id    
) AS results
WHERE additional_duration_workload > 0
ORDER BY additional_duration_workload DESC
OPTION (MERGE JOIN);
```



###  <a name="maintaining-query-performance-stability"></a><a name="Stability"></a><span data-ttu-id="b7a6a-232">クエリパフォーマンスの安定性の維持</span><span class="sxs-lookup"><span data-stu-id="b7a6a-232">Maintaining Query Performance Stability</span></span>
 <span data-ttu-id="b7a6a-233">複数回実行されるクエリの場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が異なるプランを使用した結果、リソースの使用の仕方や期間が異なっていることに気付く場合があります。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-233">For queries that are executed multiple times you may notice that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] used different plans which resulted in different resource utilization and duration.</span></span> <span data-ttu-id="b7a6a-234">クエリのストアを使用すると、クエリ パフォーマンスが低下している時点を検出し、対象期間の最適なプランを特定できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-234">With Query Store you can easily detect when the query performance regressed and determine the optimal plan within a period of interest.</span></span> <span data-ttu-id="b7a6a-235">こうすることで、将来のクエリの実行で最適なプランを強制的に適用できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-235">Then you can force that optimal plan for future query execution.</span></span>

 <span data-ttu-id="b7a6a-236">パラメーターを持つクエリ (自動的にパラメーター化されたもの、または手動でパラメーター化されたもののいずれか) に関して、クエリ パフォーマンスが一定ではないものを特定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-236">You can also identify inconsistent query performance for a query with parameters (either auto- parameterized or manually parameterized).</span></span> <span data-ttu-id="b7a6a-237">さまざまなプランの中で、ほとんどすべてのパラメーター値に対して高速で最適なプランを特定し、そのプランを強制的に適用できます。これにより、より一層多様なユーザー シナリオに対して、予測可能なパフォーマンスを維持できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-237">Among different plans you can identify plan which is fast and optimal enough for all or most of the parameter values and force that plan; keeping predictable performance for the wider set of user scenarios.</span></span>

 <span data-ttu-id="b7a6a-238">**クエリに対してプランを強制する (強制ポリシーの適用)。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-238">**Force or a plan for a query (apply forcing policy).**</span></span> <span data-ttu-id="b7a6a-239">特定のクエリに対して つのプランを強制すると、クエリが実行されるたびに、強制されているプランが使われて実行されます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-239">When a plan is forced for a certain query, every time a query comes to execution it will be executed with the plan that is forced.</span></span>

```
EXEC sp_query_store_force_plan @query_id = 48, @plan_id = 49;
```

 <span data-ttu-id="b7a6a-240">`sp_query_store_force_plan` を使用する場合は、クエリのストアによってそのクエリのプランとして記録されたプランのみを強制できます。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-240">When using `sp_query_store_force_plan` you can only force plans that were recorded by Query Store as a plan for that query.</span></span> <span data-ttu-id="b7a6a-241">つまり、クエリで使用できるプランは、クエリのストアがアクティブであったときに Q1 を実行するために既に使用されているプランのみです。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-241">In other words, the only plans available for a query are those that were already used to execute Q1 while Query Store was active.</span></span>

 <span data-ttu-id="b7a6a-242">**クエリに対するプランの強制を削除します。**</span><span class="sxs-lookup"><span data-stu-id="b7a6a-242">**Remove plan forcing for a query.**</span></span> <span data-ttu-id="b7a6a-243">クエリオプティマイザーを使用して最適なクエリプランを計算するには、を使用して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クエリに対して選択されたプランを `sp_query_store_unforce_plan` 強制的に適用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="b7a6a-243">To rely again on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] query optimizer to calculate the optimal query plan, use `sp_query_store_unforce_plan` to unforce the plan that was selected for the query.</span></span>

```
EXEC sp_query_store_unforce_plan @query_id = 48, @plan_id = 49;
```



## <a name="see-also"></a><span data-ttu-id="b7a6a-244">参照</span><span class="sxs-lookup"><span data-stu-id="b7a6a-244">See Also</span></span>
 <span data-ttu-id="b7a6a-245">パフォーマンス[パフォーマンスの監視とチューニング](../performance/performance-monitoring-and-tuning-tools.md)[のための監視](../performance/monitor-and-tune-for-performance.md)とチューニングツール[利用状況モニターを開く &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md) [利用状況モニター](../performance-monitor/activity-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="b7a6a-245">[Monitor and Tune for Performance](../performance/monitor-and-tune-for-performance.md) [Performance Monitoring and Tuning Tools](../performance/performance-monitoring-and-tuning-tools.md) [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md) [Activity Monitor](../performance-monitor/activity-monitor.md)</span></span>


