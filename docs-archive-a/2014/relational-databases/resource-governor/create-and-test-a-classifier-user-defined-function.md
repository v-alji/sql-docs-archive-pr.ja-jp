---
title: ユーザー定義の分類子関数の作成とテスト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, classifier function create
- classifier function [SQL Server], test
- classifier function [SQL Server], create
- Resource Governor, classifier function test
ms.assetid: 7866b3c9-385b-40c6-aca5-32d3337032be
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b8e5371762e38cf2b3ac8c1d506b467dcfa7e3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715165"
---
# <a name="create-and-test-a-classifier-user-defined-function"></a><span data-ttu-id="7a171-102">ユーザー定義の分類子関数の作成とテスト</span><span class="sxs-lookup"><span data-stu-id="7a171-102">Create and Test a Classifier User-Defined Function</span></span>
  <span data-ttu-id="7a171-103">このトピックでは、ユーザー定義 (UDF) の分類子関数を作成してテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a171-103">This topic shows how to create and test a classifier user-defined function (UDF).</span></span> <span data-ttu-id="7a171-104">この手順では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ エディターで [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="7a171-104">The steps involve executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="7a171-105">次の手順で紹介する例のように、ユーザー定義の分類子関数の作成はかなり複雑になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a171-105">The example shown in the following procedure illustrates the possibilities for creating a fairly complex classifier user-defined function.</span></span>  
  
 <span data-ttu-id="7a171-106">この例では次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7a171-106">In our example:</span></span>  
  
-   <span data-ttu-id="7a171-107">指定された時間範囲内の実稼働プロセスに対し、リソース プール (pProductionProcessing) とワークロード グループ (gProductionProcessing) を作成します。</span><span class="sxs-lookup"><span data-stu-id="7a171-107">A resource pool (pProductionProcessing) and workload group (gProductionProcessing) are created for production processing during a specified time range.</span></span>  
  
-   <span data-ttu-id="7a171-108">実稼働プロセスの要件を満たしていない接続を処理するために、リソース プール (pOffHoursProcessing) とワークロード グループ (gOffHoursProcessing) を作成します。</span><span class="sxs-lookup"><span data-stu-id="7a171-108">A resource pool (pOffHoursProcessing) and workload group (gOffHoursProcessing) are created for handling connections that do not meet the requirements for production processing.</span></span>  
  
-   <span data-ttu-id="7a171-109">ログイン時間に対して評価可能な開始時間と終了時間を保持するためのテーブル (TblClassificationTimeTable) を master に作成します。</span><span class="sxs-lookup"><span data-stu-id="7a171-109">A table (TblClassificationTimeTable) is created in master to hold start and end times that can be evaluated against a login time.</span></span> <span data-ttu-id="7a171-110">リソース ガバナーが分類子関数にスキーマ バインドを使用するため、このテーブルは master に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a171-110">This must be created in master because Resource Governor uses schema binding for classifier functions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a171-111">サイズが大きく、頻繁に更新されるテーブルは、master に格納しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="7a171-111">As a best practice, you should not store large, frequently updated tables in master.</span></span>  
  
 <span data-ttu-id="7a171-112">分類子関数を使用するとログイン時間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="7a171-112">The classifier function extends the login time.</span></span> <span data-ttu-id="7a171-113">関数が複雑すぎると、ログインがタイムアウトになったり、接続速度が低下したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="7a171-113">An overly complex function can cause logins to time out or slow down fast connections.</span></span>  
  
### <a name="to-create-the-classifier-user-defined-function"></a><span data-ttu-id="7a171-114">ユーザー定義の分類子関数を作成するには</span><span class="sxs-lookup"><span data-stu-id="7a171-114">To create the classifier user-defined function</span></span>  
  
1.  <span data-ttu-id="7a171-115">新しいリソース プールとワークロード グループを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="7a171-115">Create and configure the new resource pools and workload groups.</span></span> <span data-ttu-id="7a171-116">各ワークロード グループを適切なリソース プールに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7a171-116">Assign each workload group to the appropriate resource pool.</span></span>  
  
    ```  
    --- Create a resource pool for production processing  
    --- and set limits.  
    USE master  
    GO  
    CREATE RESOURCE POOL pProductionProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 100,  
         MIN_CPU_PERCENT = 50  
    )  
    GO  
    --- Create a workload group for production processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gProductionProcessing  
    WITH  
    (  
         IMPORTANCE = MEDIUM  
    )  
    --- Assign the workload group to the production processing  
    --- resource pool.  
    USING pProductionProcessing  
    GO  
    --- Create a resource pool for off-hours processing  
    --- and set limits.  
  
    CREATE RESOURCE POOL pOffHoursProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 50,  
         MIN_CPU_PERCENT = 0  
    )  
    GO  
    --- Create a workload group for off-hours processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gOffHoursProcessing  
    WITH  
    (  
         IMPORTANCE = LOW  
    )  
    --- Assign the workload group to the off-hours processing  
    --- resource pool.  
    USING pOffHoursProcessing  
    GO  
    ```  
  
2.  <span data-ttu-id="7a171-117">メモリ内の構成を更新します。</span><span class="sxs-lookup"><span data-stu-id="7a171-117">Update the in-memory configuration.</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
    ```  
  
3.  <span data-ttu-id="7a171-118">テーブルを作成し、実稼働プロセスの時間範囲の開始時間と終了時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="7a171-118">Create a table and define the start and end times for the production processing time range.</span></span>  
  
    ```  
    USE master  
    GO  
    CREATE TABLE tblClassificationTimeTable  
    (  
         strGroupName     sysname          not null,  
         tStartTime       time              not null,  
         tEndTime         time              not null  
    )  
    GO  
    --- Add time values that the classifier will use to  
    --- determine the workload group for a session.  
    INSERT into tblClassificationTimeTable VALUES('gProductionProcessing', '6:35 AM', '6:15 PM')  
    go  
    ```  
  
4.  <span data-ttu-id="7a171-119">時刻関数および参照テーブル内の時間に対して評価可能な値を使用する分類子関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="7a171-119">Create the classifier function that uses time functions and values that can be evaluated against the times in the lookup table.</span></span> <span data-ttu-id="7a171-120">分類子関数における参照テーブルの使用については、このトピックの「分類子関数に参照テーブルを使用する際のベスト プラクティス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a171-120">For information about using Lookup Tables in a classifier function, see "Best practices for using Lookup Tables in a classifier function" in this topic.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="7a171-121">日付と時刻のデータ型および関数の拡張セットが導入されました。</span><span class="sxs-lookup"><span data-stu-id="7a171-121">introduced an expanded set of date and time data types and functions.</span></span> <span data-ttu-id="7a171-122">詳細については、「[日付と時刻のデータ型および関数&#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a171-122">For more information, see [Date and Time Data Types and Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).</span></span>  
  
    ```  
    CREATE FUNCTION fnTimeClassifier()  
    RETURNS sysname  
    WITH SCHEMABINDING  
    AS  
    BEGIN  
         DECLARE @strGroup sysname  
         DECLARE @loginTime time  
         SET @loginTime = CONVERT(time,GETDATE())  
         SELECT TOP 1 @strGroup = strGroupName  
              FROM dbo.tblClassificationTimeTable  
              WHERE tStartTime <= @loginTime and tEndTime >= @loginTime  
         IF(@strGroup is not null)  
         BEGIN  
              RETURN @strGroup  
         END  
    --- Use the default workload group if there is no match  
    --- on the lookup.  
         RETURN N'gOffHoursProcessing'  
    END  
    GO  
    ```  
  
5.  <span data-ttu-id="7a171-123">分類子関数を登録し、メモリ内の構成を更新します。</span><span class="sxs-lookup"><span data-stu-id="7a171-123">Register the classifier function and update the in-memory configuration.</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR with (CLASSIFIER_FUNCTION = dbo.fnTimeClassifier)  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
    ```  
  
### <a name="to-verify-the-resource-pools-workload-groups-and-the-classifier-user-defined-function"></a><span data-ttu-id="7a171-124">リソース プール、ワークロード グループ、およびユーザー定義の分類子関数を確認するには</span><span class="sxs-lookup"><span data-stu-id="7a171-124">To verify the resource pools, workload groups, and the classifier user-defined function</span></span>  
  
1.  <span data-ttu-id="7a171-125">次のクエリを使用して、リソース プールとワークロード グループの構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="7a171-125">Obtain the resource pool and workload group configuration by using the following query.</span></span>  
  
    ```  
    USE master  
    SELECT * FROM sys.resource_governor_resource_pools  
    SELECT * FROM sys.resource_governor_workload_groups  
    GO  
    ```  
  
2.  <span data-ttu-id="7a171-126">次のクエリを使用して、分類子関数が存在し、有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7a171-126">Verify that the classifier function exists and is enabled by using the following queries.</span></span>  
  
    ```  
    --- Get the classifier function Id and state (enabled).  
    SELECT * FROM sys.resource_governor_configuration  
    GO  
    --- Get the classifer function name and the name of the schema  
    --- that it is bound to.  
    SELECT   
          object_schema_name(classifier_function_id) AS [schema_name],  
          object_name(classifier_function_id) AS [function_name]  
    FROM sys.dm_resource_governor_configuration  
  
    ```  
  
3.  <span data-ttu-id="7a171-127">次のクエリを使用して、リソース プールとワークロード グループの現在のランタイム データを取得します。</span><span class="sxs-lookup"><span data-stu-id="7a171-127">Obtain the current runtime data for the resource pools and workload groups by using the following query.</span></span>  
  
    ```  
    SELECT * FROM sys.dm_resource_governor_resource_pools  
    SELECT * FROM sys.dm_resource_governor_workload_groups  
    GO  
    ```  
  
4.  <span data-ttu-id="7a171-128">次のクエリを使用して、各グループにあるセッションを確認します。</span><span class="sxs-lookup"><span data-stu-id="7a171-128">Find out what sessions are in each group by using the following query.</span></span>  
  
    ```  
    SELECT s.group_id, CAST(g.name as nvarchar(20)), s.session_id, s.login_time, CAST(s.host_name as nvarchar(20)), CAST(s.program_name AS nvarchar(20))  
              FROM sys.dm_exec_sessions s  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
              ON g.group_id = s.group_id  
    ORDER BY g.name  
    GO  
    ```  
  
5.  <span data-ttu-id="7a171-129">次のクエリを使用して、各グループにある要求を確認します。</span><span class="sxs-lookup"><span data-stu-id="7a171-129">Find out which requests are in each group by using the following query.</span></span>  
  
    ```  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, r.start_time, r.command, r.sql_handle, t.text   
               FROM sys.dm_exec_requests r  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
                ON g.group_id = r.group_id  
         CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name  
    GO  
    ```  
  
6.  <span data-ttu-id="7a171-130">次のクエリを使用して、分類子関数で実行されている要求を確認します。</span><span class="sxs-lookup"><span data-stu-id="7a171-130">Find out what requests are running in the classifier by using the following query.</span></span>  
  
    ```  
    SELECT s.group_id, g.name, s.session_id, s.login_time, s.host_name, s.program_name   
               FROM sys.dm_exec_sessions s  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
               ON g.group_id = s.group_id  
                     AND 'preconnect' = s.status  
    ORDER BY g.name  
    GO  
  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, r.start_time, r.command, r.sql_handle, t.text   
               FROM sys.dm_exec_requests r  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
               ON g.group_id = r.group_id  
                     AND 'preconnect' = r.status  
         CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name  
    GO  
    ```  
  
### <a name="best-practices-for-using-lookup-tables-in-a-classifier-function"></a><span data-ttu-id="7a171-131">分類子関数に参照テーブルを使用する際のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="7a171-131">Best practices for using Lookup Tables in a classifier function</span></span>  
  
1.  <span data-ttu-id="7a171-132">どうしても必要である場合を除き、参照テーブルは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7a171-132">Do not use a lookup table unless it is absolutely necessary.</span></span> <span data-ttu-id="7a171-133">使用する必要がある場合は、関数そのものに参照テーブルをハードコーディングすることができます。ただし、そのためには、分類子関数に伴う複雑さや動的な変化とのバランスを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a171-133">If you need to use a lookup table, it can be hard coded into the function itself; however, this needs to be balanced with the complexity and dynamic changes of the classifier function.</span></span>  
  
2.  <span data-ttu-id="7a171-134">参照テーブルに対して実行される I/O を制限します。</span><span class="sxs-lookup"><span data-stu-id="7a171-134">Limit the I/O performed for lookup tables.</span></span>  
  
    1.  <span data-ttu-id="7a171-135">TOP 1 を使用して、返される行数を 1 行に絞り込みます。</span><span class="sxs-lookup"><span data-stu-id="7a171-135">Use the TOP 1 to return only one row.</span></span>  
  
    2.  <span data-ttu-id="7a171-136">テーブルの行数を最小限にします。</span><span class="sxs-lookup"><span data-stu-id="7a171-136">Minimize the number of rows in the table.</span></span>  
  
    3.  <span data-ttu-id="7a171-137">テーブルのすべての行が単一のページまたは少数のページに収まるようにします。</span><span class="sxs-lookup"><span data-stu-id="7a171-137">Make all rows of the table exist on a single page, or a small number of pages.</span></span>  
  
    4.  <span data-ttu-id="7a171-138">Index Seek 操作を使用して検出された行に、シーク列ができるだけ多く使用されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7a171-138">Confirm that rows found using the Index Seek operations use as many seeking columns as possible.</span></span>  
  
    5.  <span data-ttu-id="7a171-139">複数のテーブルを結合によって使用することを検討している場合は、単一のテーブルに非正規化します。</span><span class="sxs-lookup"><span data-stu-id="7a171-139">De-normalize to a single table if you are considering using multiple tables with joins.</span></span>  
  
3.  <span data-ttu-id="7a171-140">参照テーブルでのブロックを回避します。</span><span class="sxs-lookup"><span data-stu-id="7a171-140">Prevent blocking on the lookup table.</span></span>  
  
    1.  <span data-ttu-id="7a171-141">`NOLOCK` ヒントを使用してブロックを回避するか、 `SET LOCK_TIMEOUT` (最大値は 1000 ミリ秒) を関数に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a171-141">Use the `NOLOCK` hint to prevent blocking or use `SET LOCK_TIMEOUT` in the function with a maximum value of 1000 milliseconds.</span></span>  
  
    2.  <span data-ttu-id="7a171-142">テーブルは、master データベース内に存在している必要があります</span><span class="sxs-lookup"><span data-stu-id="7a171-142">Table(s) must exist in the master database.</span></span> <span data-ttu-id="7a171-143">(クライアント コンピューターの接続試行時に復旧が保証されるデータベースは、master データベースだけです)。</span><span class="sxs-lookup"><span data-stu-id="7a171-143">(The master database is the only database that is guaranteed to be recovered when the client computers attempt to connect).</span></span>  
  
    3.  <span data-ttu-id="7a171-144">テーブル名は必ずスキーマ付きで完全修飾します。</span><span class="sxs-lookup"><span data-stu-id="7a171-144">Always fully-qualify the table name with the schema.</span></span> <span data-ttu-id="7a171-145">master データベースであることがわかっているため、データベース名は不要です。</span><span class="sxs-lookup"><span data-stu-id="7a171-145">The database name is not necessary since it has to be the master database.</span></span>  
  
    4.  <span data-ttu-id="7a171-146">テーブルにトリガーがないようにします。</span><span class="sxs-lookup"><span data-stu-id="7a171-146">No triggers on the table.</span></span>  
  
    5.  <span data-ttu-id="7a171-147">テーブルの内容を更新する場合は、ライターがリーダーをブロックすることのないように、必ずスナップショット分離レベル トランザクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a171-147">If you are updating the table contents, make sure to use a snapshot isolation level transaction to prevent Writer blocking Readers.</span></span> <span data-ttu-id="7a171-148">この点は `NOLOCK` ヒントを使用して回避することもできます。</span><span class="sxs-lookup"><span data-stu-id="7a171-148">Note that using the `NOLOCK` hint should also mitigate this.</span></span>  
  
    6.  <span data-ttu-id="7a171-149">テーブルの内容を変更する場合、可能であれば、分類子関数を無効にします。</span><span class="sxs-lookup"><span data-stu-id="7a171-149">If possible, disable the classifier function when changing the table contents.</span></span>  
  
        > [!WARNING]  
        >  <span data-ttu-id="7a171-150">以上のベスト プラクティスに従うことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7a171-150">We highly recommend following these best practices.</span></span> <span data-ttu-id="7a171-151">ベスト プラクティスに従うことのできない事情がある場合は、問題の発生を事前に防ぐためにも、Microsoft サポートにお問い合わせいただくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7a171-151">If there are issues that prevent you from following the best practices, we recommend that you contact Microsoft Support so that you can proactively prevent any future problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a171-152">参照</span><span class="sxs-lookup"><span data-stu-id="7a171-152">See Also</span></span>  
 <span data-ttu-id="7a171-153">[リソース ガバナー](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="7a171-153">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="7a171-154">[リソース ガバナーの有効化](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="7a171-154">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="7a171-155">[リソース ガバナー リソース プール](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="7a171-155">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="7a171-156">[リソース ガバナー ワークロード グループ](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="7a171-156">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="7a171-157">[テンプレートを使用してリソース ガバナーを構成する](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="7a171-157">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 <span data-ttu-id="7a171-158">[リソース ガバナー プロパティの表示](view-resource-governor-properties.md) </span><span class="sxs-lookup"><span data-stu-id="7a171-158">[View Resource Governor Properties](view-resource-governor-properties.md) </span></span>  
 <span data-ttu-id="7a171-159">[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7a171-159">[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql) </span></span>  
 <span data-ttu-id="7a171-160">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7a171-160">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="7a171-161">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7a171-161">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="7a171-162">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7a171-162">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 [<span data-ttu-id="7a171-163">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7a171-163">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
