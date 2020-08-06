---
title: 管理データ ウェアハウス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collector [SQL Server], management data warehouse
- data warehouse
- management data warehouse
ms.assetid: 9874a8b2-7ccd-494a-944c-ad33b30b5499
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 96eb26c3e273832aead4aa0421304df17dc5b8ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634560"
---
# <a name="management-data-warehouse"></a><span data-ttu-id="14b0d-102">管理データ ウェアハウス (management data warehouse)</span><span class="sxs-lookup"><span data-stu-id="14b0d-102">Management Data Warehouse</span></span>
  <span data-ttu-id="14b0d-103">管理データ ウェアハウスは、データ コレクションの対象であるサーバーから収集されたデータを格納するリレーショナル データベースです。</span><span class="sxs-lookup"><span data-stu-id="14b0d-103">The management data warehouse is a relational database that contains the data that is collected from a server that is a data collection target.</span></span> <span data-ttu-id="14b0d-104">このデータは、システム データ コレクション セットのレポートを生成するために使用され、カスタム レポートを作成する際にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-104">This data is used to generate the reports for the System Data collection sets, and can also be used to create custom reports.</span></span>  
  
 <span data-ttu-id="14b0d-105">データベース管理者が定義した保有ポリシーを実装するために必要なジョブやメンテナンス プランは、データ コレクターのインフラストラクチャによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-105">The data collector infrastructure defines the jobs and maintenance plans that are needed to implement the retention policies defined by the database administrator.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="14b0d-106">このリリースのデータ コレクターでは、ログ記録を最小限に抑えるため、単純復旧モデルを使用して管理データ ウェアハウスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-106">For this release of the data collector, the management data warehouse is created using the Simple recovery model, to minimize logging.</span></span> <span data-ttu-id="14b0d-107">組織に適した復旧モデルを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14b0d-107">You should implement the appropriate recovery model for your organization.</span></span>  
  
## <a name="deploying-and-using-the-data-warehouse"></a><span data-ttu-id="14b0d-108">データ ウェアハウスの配置と使用</span><span class="sxs-lookup"><span data-stu-id="14b0d-108">Deploying and Using the Data Warehouse</span></span>  
 <span data-ttu-id="14b0d-109">管理データ ウェアハウスは、データ コレクターを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスと同じインスタンスにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-109">You can install the management data warehouse on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that runs the data collector.</span></span> <span data-ttu-id="14b0d-110">ただし、監視中のサーバーでサーバー リソースやパフォーマンスが問題となっている場合は、別のコンピューターに管理データ ウェアハウスをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-110">However, if server resources or performance is an issue on the server being monitored, you can install the management data warehouse on a different computer.</span></span>  
  
 <span data-ttu-id="14b0d-111">事前に定義されたシステム コレクション セットに必要なスキーマとそのオブジェクトは、管理データ ウェアハウス作成時に作成されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-111">The required schemas and their objects for the predefined system collection sets are created when you create the management data warehouse.</span></span> <span data-ttu-id="14b0d-112">作成されるスキーマは、core と snapshots です。3 つ目のスキーマである custom_snapshots は、ジェネリック T-SQL Query コレクター型を使用するコレクション アイテムを含んだユーザー定義のコレクション セットの作成時に作成されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-112">The schemas that are created are core and snapshots.A third schema, custom_snapshots, is created when user-defined collection sets are created that include collection items that use the Generic T-SQL Query collector type.</span></span>  
  
###### <a name="core-schema"></a><span data-ttu-id="14b0d-113">core スキーマ</span><span class="sxs-lookup"><span data-stu-id="14b0d-113">Core schema</span></span>  
 <span data-ttu-id="14b0d-114">core スキーマでは、収集したデータの編成と識別に使用するテーブル、ストアド プロシージャ、およびビューが記述されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-114">The core schema describes the tables, stored procedures, and views that are used to organize and to identify collected data.</span></span> <span data-ttu-id="14b0d-115">これらのテーブルは、個々のコレクター型ごとに作成されるすべてのデータ テーブルで共有されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-115">These tables are shared among all the data tables created for individual collector types.</span></span> <span data-ttu-id="14b0d-116">このスキーマはロックされており、変更できるのは管理データ ウェアハウスのデータベースの所有者だけです。</span><span class="sxs-lookup"><span data-stu-id="14b0d-116">This schema is locked and can only be modified by the owner of the management data warehouse database.</span></span> <span data-ttu-id="14b0d-117">このスキーマに記述されるテーブルは、名前の先頭に "core" が付加されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-117">The names of the tables in this schema are prefixed by "core".</span></span>  
  
 <span data-ttu-id="14b0d-118">次の表では、core スキーマ内のデータベース テーブルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-118">The following table describes the database tables in the core schema.</span></span> <span data-ttu-id="14b0d-119">データ コレクターは、これらのデータベース テーブルで、データの出所、挿入者、データ ウェアハウスにアップロードされた時刻を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-119">These database tables enable the data collector to track where the data came from, who inserted it, and when it was uploaded to the data warehouse.</span></span>  
  
|<span data-ttu-id="14b0d-120">テーブル名</span><span class="sxs-lookup"><span data-stu-id="14b0d-120">Table name</span></span>|<span data-ttu-id="14b0d-121">説明</span><span class="sxs-lookup"><span data-stu-id="14b0d-121">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="14b0d-122">core.performance_counter_report_group_items</span><span class="sxs-lookup"><span data-stu-id="14b0d-122">core.performance_counter_report_group_items</span></span>|<span data-ttu-id="14b0d-123">管理データ ウェアハウスのレポートがパフォーマンス カウンターをグループ化および集計する方法に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-123">Stores information about how the management data warehouse reports should group and aggregate performance counters.</span></span>|  
|<span data-ttu-id="14b0d-124">core.snapshots_internal</span><span class="sxs-lookup"><span data-stu-id="14b0d-124">core.snapshots_internal</span></span>|<span data-ttu-id="14b0d-125">それぞれの新しいスナップショットを識別します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-125">Identifies each new snapshot.</span></span> <span data-ttu-id="14b0d-126">アップロード パッケージによってデータの新しいバッチのアップロードが開始されるたびに、このテーブルに新しい行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-126">A new row is inserted into this table whenever an upload package starts uploading a new batch of data.</span></span>|  
|<span data-ttu-id="14b0d-127">core.snapshot_timetable_internal</span><span class="sxs-lookup"><span data-stu-id="14b0d-127">core.snapshot_timetable_internal</span></span>|<span data-ttu-id="14b0d-128">スナップショット時間に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-128">Stores information about the snapshot times.</span></span> <span data-ttu-id="14b0d-129">多数のスナップショットがほぼ同時に発生する可能性があるため、スナップショット時間は別のテーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-129">The snapshot time is stored in a separate table because many snapshots can happen at nearly the same time.</span></span>|  
|<span data-ttu-id="14b0d-130">core.source.info_internal</span><span class="sxs-lookup"><span data-stu-id="14b0d-130">core.source.info_internal</span></span>|<span data-ttu-id="14b0d-131">このテーブルは、データ ソースに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-131">This table stores information about the data source.</span></span> <span data-ttu-id="14b0d-132">新しいコレクション セットからデータ ウェアハウスへのデータのアップロードが開始されるたびに更新されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-132">This table is updated whenever a new collection set starts uploading data to the data warehouse.</span></span>|  
|<span data-ttu-id="14b0d-133">core.supported_collector_types_internal</span><span class="sxs-lookup"><span data-stu-id="14b0d-133">core.supported_collector_types_internal</span></span>|<span data-ttu-id="14b0d-134">管理データ ウェアハウスにデータをアップロードできる、登録済みのコレクター型の ID を格納します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-134">Contains the IDs of registered collector types that can upload data to the management data warehouse.</span></span> <span data-ttu-id="14b0d-135">このテーブルが更新されるのは、新しいコレクター型のサポートのためウェアハウスのスキーマが更新された場合だけです。</span><span class="sxs-lookup"><span data-stu-id="14b0d-135">This table is only updated when the schema of the warehouse is updated to support a new collector type.</span></span> <span data-ttu-id="14b0d-136">管理データ ウェアハウスの作成時に、データ コレクターで提供されるコレクター型の ID がこのテーブルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-136">When the management data warehouse is created, this table is populated with the IDs of the collector types provided by the data collector.</span></span>|  
|<span data-ttu-id="14b0d-137">core.wait_categories</span><span class="sxs-lookup"><span data-stu-id="14b0d-137">core.wait_categories</span></span>|<span data-ttu-id="14b0d-138">wait_type 特性に従って待機の種類を分類するために使用されるカテゴリを格納します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-138">Contains the categories used to group wait types according to wait_type characteristic.</span></span>|  
|<span data-ttu-id="14b0d-139">core.wait_types</span><span class="sxs-lookup"><span data-stu-id="14b0d-139">core.wait_types</span></span>|<span data-ttu-id="14b0d-140">データ コレクターで認識される待機の種類を格納します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-140">Contains the wait types recognized by the data collector.</span></span>|  
|<span data-ttu-id="14b0d-141">core.purge_info_internal</span><span class="sxs-lookup"><span data-stu-id="14b0d-141">core.purge_info_internal</span></span>|<span data-ttu-id="14b0d-142">管理データ ウェアハウスのデータ削除を停止する要求が行われたことを示します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-142">Indicates that a request has been made to stop the removal of data from the management data warehouse.</span></span>|  
  
 <span data-ttu-id="14b0d-143">上記のテーブルは、コレクター型テーブルと共に情報を格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-143">The preceding tables are used with collector type tables to store information.</span></span> <span data-ttu-id="14b0d-144">たとえば、ジェネリック SQL トレース コレクター型は、次のテーブルを使用してトレース データを格納します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-144">For example, the Generic SQL Trace collector type uses the following tables to store trace data:</span></span>  
  
-   <span data-ttu-id="14b0d-145">core.source_info_internal</span><span class="sxs-lookup"><span data-stu-id="14b0d-145">core.source_info_internal</span></span>  
  
-   <span data-ttu-id="14b0d-146">core.snapshots_internal</span><span class="sxs-lookup"><span data-stu-id="14b0d-146">core.snapshots_internal</span></span>  
  
-   <span data-ttu-id="14b0d-147">snapshots.trace_info</span><span class="sxs-lookup"><span data-stu-id="14b0d-147">snapshots.trace_info</span></span>  
  
-   <span data-ttu-id="14b0d-148">snapshots.trace_data</span><span class="sxs-lookup"><span data-stu-id="14b0d-148">snapshots.trace_data</span></span>  
  
###### <a name="snapshots-schema"></a><span data-ttu-id="14b0d-149">snapshots スキーマ</span><span class="sxs-lookup"><span data-stu-id="14b0d-149">Snapshots schema</span></span>  
 <span data-ttu-id="14b0d-150">snapshots スキーマでは、提供されているコレクター型で収集されるデータの格納と保持に必要なオブジェクトが記述されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-150">The snapshots schema describes the objects needed to store and maintain the data collected by the collector types that are provided.</span></span> <span data-ttu-id="14b0d-151">このスキーマのテーブルは固定であり、コレクター型の有効期間中に変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="14b0d-151">The tables in this schema are fixed and do not need to be changed during the lifetime of the collector type.</span></span> <span data-ttu-id="14b0d-152">変更が必要な場合、スキーマを変更できるのは mdw_admin ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="14b0d-152">If changes are needed, the schema can only be changed by members of the mdw_admin role.</span></span> <span data-ttu-id="14b0d-153">このテーブルは、システム データ コレクション セットによって収集されたデータを格納するために作成されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-153">These tables are created to store the data collected by the System Data collection sets.</span></span>  
  
 <span data-ttu-id="14b0d-154">次の表は、管理データ ウェアハウス スキーマの、サーバー利用状況コレクション セットとクエリ統計情報コレクション セットに必要な部分を示しています。</span><span class="sxs-lookup"><span data-stu-id="14b0d-154">The following tables illustrate a portion of the management data warehouse schema that is required for the Server Activity and Query Statistics collection sets.</span></span>  
  
-   <span data-ttu-id="14b0d-155">システム レベルのリソースのテーブル</span><span class="sxs-lookup"><span data-stu-id="14b0d-155">System-level resource tables</span></span>  
  
    -   <span data-ttu-id="14b0d-156">**snapshots.os_wait_stats**</span><span class="sxs-lookup"><span data-stu-id="14b0d-156">**snapshots.os_wait_stats**</span></span>  
  
    -   <span data-ttu-id="14b0d-157">**snapshots.os_latch_stats**</span><span class="sxs-lookup"><span data-stu-id="14b0d-157">**snapshots.os_latch_stats**</span></span>  
  
    -   <span data-ttu-id="14b0d-158">**snapshots.os_schedulers**</span><span class="sxs-lookup"><span data-stu-id="14b0d-158">**snapshots.os_schedulers**</span></span>  
  
    -   `snapshots.os_memory_clerks`  
  
    -   <span data-ttu-id="14b0d-159">**snapshots.os_memory_nodes**</span><span class="sxs-lookup"><span data-stu-id="14b0d-159">**snapshots.os_memory_nodes**</span></span>  
  
    -   <span data-ttu-id="14b0d-160">snapshots.sql_process_and_system_memory</span><span class="sxs-lookup"><span data-stu-id="14b0d-160">snapshots.sql_process_and_system_memory</span></span>  
  
-   <span data-ttu-id="14b0d-161">システムの利用状況</span><span class="sxs-lookup"><span data-stu-id="14b0d-161">System activity</span></span>  
  
    -   <span data-ttu-id="14b0d-162">snapshots.active_sessions_and_requests</span><span class="sxs-lookup"><span data-stu-id="14b0d-162">snapshots.active_sessions_and_requests</span></span>  
  
-   <span data-ttu-id="14b0d-163">クエリ統計情報</span><span class="sxs-lookup"><span data-stu-id="14b0d-163">Query statistics</span></span>  
  
    -   <span data-ttu-id="14b0d-164">snapshots.query_stats</span><span class="sxs-lookup"><span data-stu-id="14b0d-164">snapshots.query_stats</span></span>  
  
-   <span data-ttu-id="14b0d-165">I/O 統計</span><span class="sxs-lookup"><span data-stu-id="14b0d-165">I/O statistics</span></span>  
  
    -   `snapshots.io_virtual_file_stats`  
  
-   <span data-ttu-id="14b0d-166">クエリ テキストとクエリ プラン</span><span class="sxs-lookup"><span data-stu-id="14b0d-166">Query text and plan</span></span>  
  
    -   <span data-ttu-id="14b0d-167">snapshots.notable_query_text</span><span class="sxs-lookup"><span data-stu-id="14b0d-167">snapshots.notable_query_text</span></span>  
  
    -   <span data-ttu-id="14b0d-168">snapshots.notable_query_plan</span><span class="sxs-lookup"><span data-stu-id="14b0d-168">snapshots.notable_query_plan</span></span>  
  
-   <span data-ttu-id="14b0d-169">正規化されたクエリ統計</span><span class="sxs-lookup"><span data-stu-id="14b0d-169">Normalized query statistics</span></span>  
  
    -   <span data-ttu-id="14b0d-170">snapshots.distinct_queries</span><span class="sxs-lookup"><span data-stu-id="14b0d-170">snapshots.distinct_queries</span></span>  
  
    -   <span data-ttu-id="14b0d-171">snapshots.distinct_query_to_handle</span><span class="sxs-lookup"><span data-stu-id="14b0d-171">snapshots.distinct_query_to_handle</span></span>  
  
 <span data-ttu-id="14b0d-172">**custom_snapshots スキーマ**</span><span class="sxs-lookup"><span data-stu-id="14b0d-172">**Custom_snapshots schema**</span></span>  
  
 <span data-ttu-id="14b0d-173">custom_snapshots スキーマでは、標準のコレクター型またはサード パーティのコレクター型を使用してユーザー定義のコレクション セットを作成するときに作成される新しいテーブルとビューが記述されます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-173">The custom_snapshots schema describes new tables and views that are created when standard or third-party collector types are used to create user-defined collection sets.</span></span> <span data-ttu-id="14b0d-174">コレクション アイテム用の新しいデータ テーブルを必要とするコレクター型がある場合は、このスキーマにそのテーブルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="14b0d-174">Any collector type that requires a new data table for a collection item can create that table in this schema.</span></span> <span data-ttu-id="14b0d-175">このスキーマに新しいテーブルを追加できるのは、mdw_writer ロールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="14b0d-175">New tables can be added in this schema by members of the mdw_writer role.</span></span> <span data-ttu-id="14b0d-176">スキーマにそれ以外の変更を加えられるのは、mdw_admin ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="14b0d-176">Any other changes to the schema can only be made by members of the mdw_admin role.</span></span>  
  
 <span data-ttu-id="14b0d-177">データベース テーブルの列のデータ型とコンテンツの詳細情報については、各テーブルに適したデータ コレクターのストアド プロシージャに関するマニュアルの記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14b0d-177">You can get detailed data type and content information for the database table columns by reading the documentation for the appropriate data collector stored procedure for each of the tables.</span></span>  
  
### <a name="best-practices"></a><span data-ttu-id="14b0d-178">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="14b0d-178">Best Practices</span></span>  
 <span data-ttu-id="14b0d-179">管理データ ウェアハウスの操作に関して推奨するベスト プラクティスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="14b0d-179">When working with the management data warehouse, we recommend following these best practices:</span></span>  
  
-   <span data-ttu-id="14b0d-180">新しいコレクター型を追加する場合を除き、管理データ ウェアハウスのテーブルのメタデータは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="14b0d-180">Do not modify the metadata of management data warehouse tables unless you are adding a new collector type.</span></span>  
  
-   <span data-ttu-id="14b0d-181">管理データ ウェアハウスのデータは直接変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="14b0d-181">Do not directly modify the data in the management data warehouse.</span></span> <span data-ttu-id="14b0d-182">収集済みのデータに変更を加えると、収集したデータの正当性がなくなります。</span><span class="sxs-lookup"><span data-stu-id="14b0d-182">Changing the data that you have collected invalidates the legitimacy of the collected data.</span></span>  
  
-   <span data-ttu-id="14b0d-183">インスタンスとアプリケーション データにアクセスするには、テーブルを直接使用する代わりに、データ コレクターで提供される、ドキュメントに記載のストアド プロシージャと関数を使用してください。</span><span class="sxs-lookup"><span data-stu-id="14b0d-183">Instead of directly using the tables, use the documented stored procedures and functions that are provided with the data collector to access instance and application data.</span></span> <span data-ttu-id="14b0d-184">テーブル名と定義は変更できます。これらは、アプリケーションを更新するときには必ず変更してください。テーブル名と定義は、将来のリリースでは変更される可能性がある情報です。</span><span class="sxs-lookup"><span data-stu-id="14b0d-184">The table names and definitions can change, do change when you update the application, and might change in future releases.</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="14b0d-185">変更履歴</span><span class="sxs-lookup"><span data-stu-id="14b0d-185">Change History</span></span>  
  
|<span data-ttu-id="14b0d-186">変更内容</span><span class="sxs-lookup"><span data-stu-id="14b0d-186">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="14b0d-187">「core スキーマ」セクションに core.performance_counter_report_group_items テーブルを追加しました。</span><span class="sxs-lookup"><span data-stu-id="14b0d-187">Added the core.performance_counter_report_group_items table to the "Core schema" section.</span></span>|  
|<span data-ttu-id="14b0d-188">「snapshots スキーマ」セクションのテーブルの一覧を更新しました。</span><span class="sxs-lookup"><span data-stu-id="14b0d-188">Updated the list of tables in the "Snapshots schema" section.</span></span> <span data-ttu-id="14b0d-189">snapshots.os_memory_clerks、snapshots.sql_process_and_system_memory、および snapshots.io_virtual_file_stats を追加しました。</span><span class="sxs-lookup"><span data-stu-id="14b0d-189">Added snapshots.os_memory_clerks,snapshots.sql_process_and_system_memory, and snapshots.io_virtual_file_stats.</span></span> <span data-ttu-id="14b0d-190">snapshots.os_process_memory および snapshots.distinct_query_stats を削除しました。</span><span class="sxs-lookup"><span data-stu-id="14b0d-190">Removedsnapshots.os_process_memory and snapshots.distinct_query_stats.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14b0d-191">参照</span><span class="sxs-lookup"><span data-stu-id="14b0d-191">See Also</span></span>  
 <span data-ttu-id="14b0d-192">[管理データ ウェアハウスのストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="14b0d-192">[Management Data Warehouse Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="14b0d-193">[データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="14b0d-193">[Data Collector Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="14b0d-194">[[データ コレクション]](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="14b0d-194">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="14b0d-195">コレクション セット レポートの表示 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="14b0d-195">View a Collection Set Report &#40;SQL Server Management Studio&#41;</span></span>](view-a-collection-set-report-sql-server-management-studio.md)  
  
  
