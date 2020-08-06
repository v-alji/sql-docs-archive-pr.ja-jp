---
title: 'サンプル: WMI Provider for Server Events を使用した SQL Server エージェントアラートの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SQL Server Agent [WMI]
- WMI Provider for Server Events, samples
- sample applications [WMI]
ms.assetid: d44811c7-cd46-4017-b284-c863ca088e8f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f23a3a8738435dc6a27a230f4521300a3ee2470f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717559"
---
# <a name="sample-creating-a-sql-server-agent-alert-by-using-the-wmi-provider-for-server-events"></a><span data-ttu-id="d56bb-102">サンプル:WMI Provider for Server Events の使用による SQL Server エージェント警告の作成</span><span class="sxs-lookup"><span data-stu-id="d56bb-102">Sample: Creating a SQL Server Agent Alert by Using the WMI Provider for Server Events</span></span>
  <span data-ttu-id="d56bb-103">WMI イベント プロバイダーの標準的な使い方の 1 つは、特定のイベントに応答する SQL Server エージェントを作成することです。</span><span class="sxs-lookup"><span data-stu-id="d56bb-103">One common way to use the WMI Event Provider is to create SQL Server Agent alerts that respond to specific events.</span></span> <span data-ttu-id="d56bb-104">次のサンプルでは、後で分析するために、テーブルに XML デッドロック グラフ イベントを保存する簡単な警告を提供しています。</span><span class="sxs-lookup"><span data-stu-id="d56bb-104">The following sample presents a simple alert that saves XML deadlock graph events in a table for later analysis.</span></span> <span data-ttu-id="d56bb-105">SQL Server エージェントは、WQL 要求の送信、WMI イベントの受信、およびイベントに応答したジョブの実行を行います。</span><span class="sxs-lookup"><span data-stu-id="d56bb-105">SQL Server Agent submits a WQL request, receives WMI events, and runs a job in response to the event.</span></span> <span data-ttu-id="d56bb-106">通知メッセージの処理に関連する Service Broker オブジェクトはいくつかありますが、WMI イベント プロバイダーはこれらのオブジェクトの作成および管理の詳細を処理します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-106">Notice that, although several Service Broker objects are involved in processing the notification message, the WMI Event Provider handles the details of creating and managing these objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d56bb-107">例</span><span class="sxs-lookup"><span data-stu-id="d56bb-107">Example</span></span>  
 <span data-ttu-id="d56bb-108">まず、デッドロック グラフ イベントを格納するために、`AdventureWorks` データベースにテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d56bb-108">First, a table is created in the `AdventureWorks` database to hold the deadlock graph event.</span></span> <span data-ttu-id="d56bb-109">このテーブルには 2 つの列があります。`AlertTime` 列は警告が実行される時間、`DeadlockGraph` 列はデッドロック グラフが含まれる XML ドキュメントを格納します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-109">The table contains two columns: The `AlertTime` column holds the time that the alert runs, and the `DeadlockGraph` column holds the XML document that contains the deadlock graph.</span></span>  
  
 <span data-ttu-id="d56bb-110">次に警告が作成されます。</span><span class="sxs-lookup"><span data-stu-id="d56bb-110">Then, the alert is created.</span></span> <span data-ttu-id="d56bb-111">スクリプトは、まず、警告が実行するジョブを作成し、ジョブ ステップをジョブに追加し、そのジョブを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスに指定します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-111">The script first creates the job that the alert will run, adds a job step to the job, and targets the job to the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d56bb-112">次に、スクリプトは警告を作成します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-112">The script then creates the alert.</span></span>  
  
 <span data-ttu-id="d56bb-113">このジョブステップでは、WMI イベントインスタンスの**TextData**プロパティを取得し、その値を**DeadlockEvents**テーブルの**DeadlockGraph**列に挿入します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-113">The job step retrieves the **TextData** property of the WMI event instance and inserts that value into the **DeadlockGraph** column of the **DeadlockEvents** table.</span></span> <span data-ttu-id="d56bb-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、暗黙に文字列を XML 形式に変換することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d56bb-114">Notice that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implicitly converts the string into XML format.</span></span> <span data-ttu-id="d56bb-115">このジョブ ステップでは [!INCLUDE[tsql](../../includes/tsql-md.md)] サブシステムを使用するので、プロシキは指定されません。</span><span class="sxs-lookup"><span data-stu-id="d56bb-115">Because the job step uses the [!INCLUDE[tsql](../../includes/tsql-md.md)] subsystem, the job step does not specify a proxy.</span></span>  
  
 <span data-ttu-id="d56bb-116">警告は、デッドロック グラフ トレース イベントのログが記録されるたびに、ジョブを実行します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-116">The alert runs the job whenever a deadlock graph trace event would be logged.</span></span> <span data-ttu-id="d56bb-117">WMI 警告の場合、SQL Server エージェントは、指定された名前空間および WQL ステートメントを使用して通知クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-117">For a WMI alert, SQL Server Agent creates a notification query using the namespace and WQL statement specified.</span></span> <span data-ttu-id="d56bb-118">この警告の場合、SQL Server エージェントは、ローカル コンピューター上の既定のインスタンスを監視します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-118">For this alert, SQL Server Agent monitors the default instance on the local computer.</span></span> <span data-ttu-id="d56bb-119">WQL ステートメントは、既定のインスタンス内の任意の `DEADLOCK_GRAPH` イベントを要求します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-119">The WQL statement requests any `DEADLOCK_GRAPH` event in the default instance.</span></span> <span data-ttu-id="d56bb-120">警告が監視するインスタンスを変更するには、警告する `MSSQLSERVER` 内の `@wmi_namespace` のインスタンス名を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d56bb-120">To change the instance that the alert monitors, substitute the instance name for `MSSQLSERVER` in the `@wmi_namespace` for the alert.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d56bb-121">SQL Server エージェントが WMI イベントを受信するには、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] **msdb**およびでを有効にする必要があり [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d56bb-121">For SQL Server Agent to receive WMI events, [!INCLUDE[ssSB](../../includes/sssb-md.md)] must be enabled in **msdb** and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
IF OBJECT_ID('DeadlockEvents', 'U') IS NOT NULL  
BEGIN  
    DROP TABLE DeadlockEvents ;  
END ;  
GO  
  
CREATE TABLE DeadlockEvents  
    (AlertTime DATETIME, DeadlockGraph XML) ;  
GO  
-- Add a job for the alert to run.  
  
EXEC  msdb.dbo.sp_add_job @job_name=N'Capture Deadlock Graph',   
    @enabled=1,   
    @description=N'Job for responding to DEADLOCK_GRAPH events' ;  
GO  
  
-- Add a jobstep that inserts the current time and the deadlock graph into  
-- the DeadlockEvents table.  
  
EXEC msdb.dbo.sp_add_jobstep  
    @job_name = N'Capture Deadlock Graph',  
    @step_name=N'Insert graph into LogEvents',  
    @step_id=1,   
    @on_success_action=1,   
    @on_fail_action=2,   
    @subsystem=N'TSQL',   
    @command= N'INSERT INTO DeadlockEvents  
                (AlertTime, DeadlockGraph)  
                VALUES (getdate(), N''$(ESCAPE_SQUOTE(WMI(TextData)))'')',  
    @database_name=N'AdventureWorks' ;  
GO  
  
-- Set the job server for the job to the current instance of SQL Server.  
  
EXEC msdb.dbo.sp_add_jobserver @job_name = N'Capture Deadlock Graph' ;  
GO  
  
-- Add an alert that responds to all DEADLOCK_GRAPH events for  
-- the default instance. To monitor deadlocks for a different instance,  
-- change MSSQLSERVER to the name of the instance.  
  
EXEC msdb.dbo.sp_add_alert @name=N'Respond to DEADLOCK_GRAPH',   
@wmi_namespace=N'\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER',   
    @wmi_query=N'SELECT * FROM DEADLOCK_GRAPH',   
    @job_name='Capture Deadlock Graph' ;  
GO  
```  
  
## <a name="testing-the-sample"></a><span data-ttu-id="d56bb-122">サンプルのテスト</span><span class="sxs-lookup"><span data-stu-id="d56bb-122">Testing the Sample</span></span>  
 <span data-ttu-id="d56bb-123">ジョブの実行を確認するには、デッドロックを発生させます。</span><span class="sxs-lookup"><span data-stu-id="d56bb-123">To see the job run, provoke a deadlock.</span></span> <span data-ttu-id="d56bb-124">で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、2つの**SQL クエリ**タブを開き、両方のクエリを同じインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open two **SQL Query** tabs and connect both queries to the same instance.</span></span> <span data-ttu-id="d56bb-125">次のスクリプトを 2 つのクエリ タブのうちの 1 つで実行します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-125">Run the following script in one of the query tabs.</span></span> <span data-ttu-id="d56bb-126">このスクリプトは、1 つの結果セットを作成して終了します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-126">This script produces one result set and finishes.</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="d56bb-127">2番目の [クエリ] タブで次のスクリプトを実行します。このスクリプトは、1つの結果セットを生成してからブロックし、ロックの取得を待機 `Production.Product` します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-127">Run the following script in the second query tab. This script produces one result set and then blocks, waiting to acquire a lock on `Production.Product`.</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="d56bb-128">最初の [クエリ] タブで、次のスクリプトを実行します。このスクリプトはブロックし、ロックの取得を待機 `Production.Location` しています。</span><span class="sxs-lookup"><span data-stu-id="d56bb-128">Run the following script in the first query tab. This script blocks, waiting to acquire a lock on `Production.Location`.</span></span> <span data-ttu-id="d56bb-129">すぐにタイムアウトになった後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、このスクリプトとサンプル内のスクリプトのどちらかをデッドロックの対象として選択し、トランザクションを終了します。</span><span class="sxs-lookup"><span data-stu-id="d56bb-129">After a short time-out, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will choose either this script or the script in the sample as the deadlock victim and end the transaction.</span></span>  
  
```  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="d56bb-130">デッドロックが発生した後、SQL Server エージェントが警告を有効化してジョブを実行するまで、しばらく待ちます。</span><span class="sxs-lookup"><span data-stu-id="d56bb-130">After provoking the deadlock, wait several moments for SQL Server Agent to activate the alert and run the job.</span></span> <span data-ttu-id="d56bb-131">次のスクリプトを実行して、`DeadlockEvents` テーブルの内容を調べます。</span><span class="sxs-lookup"><span data-stu-id="d56bb-131">Examine the contents of the `DeadlockEvents` table by running the following script:</span></span>  
  
```  
SELECT * FROM DeadlockEvents ;  
GO  
```  
  
 <span data-ttu-id="d56bb-132">`DeadlockGraph` 列には、デッドロック グラフ イベントのすべてのプロパティを示した XML ドキュメントが格納されているはずです。</span><span class="sxs-lookup"><span data-stu-id="d56bb-132">The `DeadlockGraph` column should contain an XML document that shows all the properties of the deadlock graph event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56bb-133">参照</span><span class="sxs-lookup"><span data-stu-id="d56bb-133">See Also</span></span>  
 [<span data-ttu-id="d56bb-134">WMI Provider for Server Events の概念</span><span class="sxs-lookup"><span data-stu-id="d56bb-134">WMI Provider for Server Events Concepts</span></span>](wmi-provider-for-server-events-concepts.md)  
  
  
