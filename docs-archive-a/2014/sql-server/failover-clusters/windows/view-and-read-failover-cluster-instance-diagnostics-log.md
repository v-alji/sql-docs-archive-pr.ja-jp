---
title: フェールオーバー クラスター インスタンスの診断ログを表示して読む方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 68074bd5-be9d-4487-a320-5b51ef8e2b2d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 774dc4ec4a02c72420d004909cb7e6ee1b31f3a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640520"
---
# <a name="view-and-read-failover-cluster-instance-diagnostics-log"></a><span data-ttu-id="b7728-102">フェールオーバー クラスター インスタンスの診断ログを表示して読む方法</span><span class="sxs-lookup"><span data-stu-id="b7728-102">View and Read Failover Cluster Instance Diagnostics Log</span></span>
  <span data-ttu-id="b7728-103">SQL Server Resource DLL のすべての重大なエラーと警告イベントが、Windows イベント ログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="b7728-103">All critical errors and warning events for the SQL Server Resource DLL are written to the Windows event log.</span></span> <span data-ttu-id="b7728-104">[sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) システム ストアド プロシージャによってキャプチャされる SQL Server に固有の診断情報の実行ログは、SQL Server フェールオーバー クラスター診断ログ ファイル (*SQLDIAG* ログとも呼ばれます) に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="b7728-104">A running log of the diagnostic information specific to SQL Server is captured by the [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) system stored procedure and is written to the SQL Server failover cluster diagnostics (also known as the *SQLDIAG* logs) log files.</span></span>  
  
-   <span data-ttu-id="b7728-105">**作業を開始する準備:**  [推奨事項](#Recommendations)、 [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="b7728-105">**Before you begin:**  [Recommendations](#Recommendations), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="b7728-106">**診断ログの表示:**  [SQL Server Management Studio の使用](#SSMSProcedure)、 [Transact-SQL の使用](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="b7728-106">**To View the Diagnostic Log, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
-   <span data-ttu-id="b7728-107">**診断ログ設定の構成:** [Transact-SQL の使用](#TsqlConfigure)</span><span class="sxs-lookup"><span data-stu-id="b7728-107">**To Configure Diagnostic Log settings, using:** [Transact-SQL](#TsqlConfigure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b7728-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="b7728-108">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b7728-109">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b7728-109">Recommendations</span></span>  
 <span data-ttu-id="b7728-110">既定では、SQLDIAG は SQL Server インスタンスディレクトリのローカルログフォルダーに格納されます。たとえば、' C\Program are SQL \<InstanceName> です。AlwaysOn フェールオーバークラスターインスタンス (FCI) の所有ノードの \MSSQL\LOG '。</span><span class="sxs-lookup"><span data-stu-id="b7728-110">By default, the SQLDIAG are stored under a local LOG folder of the SQL Server instance directory, for example, 'C\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\LOG' of the owning node of the AlwaysOn Failover Cluster Instance (FCI).</span></span> <span data-ttu-id="b7728-111">各 SQLDIAG ログ ファイルのサイズは 100 MB に固定されています。</span><span class="sxs-lookup"><span data-stu-id="b7728-111">The size of each SQLDIAG log file is fixed at 100 MB.</span></span> <span data-ttu-id="b7728-112">10 個のログ ファイルがコンピューターに格納された後、新しいログとして再利用されます。</span><span class="sxs-lookup"><span data-stu-id="b7728-112">Ten such log files are stored on the computer before they are recycled for new logs.</span></span>  
  
 <span data-ttu-id="b7728-113">ログには、拡張イベント ファイル形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b7728-113">The logs use the extended events file format.</span></span> <span data-ttu-id="b7728-114">**sys.fn_xe_file_target_read_file** システム関数は、拡張イベントによって作成されるファイルの読み取りに使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b7728-114">The **sys.fn_xe_file_target_read_file** system function can be used to read the files that are created by Extended Events.</span></span> <span data-ttu-id="b7728-115">行ごとに、XML 形式の 1 つのイベントが返されます。</span><span class="sxs-lookup"><span data-stu-id="b7728-115">One event, in XML format, is returned per row.</span></span> <span data-ttu-id="b7728-116">XML データを結果セットとして解析するには、システム ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b7728-116">Query the system view to parse the XML data as a result-set.</span></span> <span data-ttu-id="b7728-117">詳細については、「[sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7728-117">For more information, see [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b7728-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b7728-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b7728-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="b7728-119">Permissions</span></span>  
 <span data-ttu-id="b7728-120">**fn_xe_file_target_read_file**を実行するには、VIEW SERVER STATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b7728-120">VIEW SERVER STATE permission is needed to run **fn_xe_file_target_read_file**.</span></span>  
  
 <span data-ttu-id="b7728-121">SQL Server Management Studio を管理者として開きます。</span><span class="sxs-lookup"><span data-stu-id="b7728-121">Open SQL Server Management Studio as Administrator</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b7728-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b7728-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b7728-123">**診断ログ ファイルを表示するには**</span><span class="sxs-lookup"><span data-stu-id="b7728-123">**To view the Diagnostic log files:**</span></span>  
  
1.  <span data-ttu-id="b7728-124">**[ファイル]** メニューから、 **[開く]**、 **[ファイル]** を選択し、表示する診断ログ ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b7728-124">From the **File** menu, select **Open**, **File**, and choose the diagnostic log file you want to view.</span></span>  
  
2.  <span data-ttu-id="b7728-125">イベントは、右ペインに行として表示されます。既定では、 **名前**と **タイムスタンプ** の 2 つの列だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b7728-125">The events are displayed as rows in the right pane, and by default **name**, and **timestamp** are the only two columns displayed.</span></span>  
  
     <span data-ttu-id="b7728-126">また、 **[ExtendedEvents]** メニューがアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="b7728-126">This also activates the **ExtendedEvents** menu.</span></span>  
  
3.  <span data-ttu-id="b7728-127">他の列を表示するには、 **[ExtendedEvents]** メニューにアクセスし、 **[列の選択]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b7728-127">To see more columns, go the **ExtendedEvents** menu, and select **Choose Columns**.</span></span>  
  
     <span data-ttu-id="b7728-128">ダイアログ ボックスが開き、表示対象として選択できる列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b7728-128">A dialog box opens with the available columns allowing you to select the columns for display.</span></span>  
  
4.  <span data-ttu-id="b7728-129">**[ExtendedEvents]** メニューを使用し、 **[フィルター]** オプションを選択することによって、イベント データをフィルター選択したり並べ替えたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="b7728-129">You can filter, and sort the event data using the **ExtendedEvents** menu and selecting the **Filter** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b7728-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b7728-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="b7728-131">**診断ログ ファイルを表示するには**</span><span class="sxs-lookup"><span data-stu-id="b7728-131">**To view the Diagnostic log files:**</span></span>  
  
 <span data-ttu-id="b7728-132">SQLDIAG ログ ファイル内のすべてのログ アイテムを表示するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="b7728-132">To view all the log items in the SQLDIAG log file, use the following query:</span></span>  
  
```  
SELECT  
xml_data.value('(event/@name)[1]','varchar(max)') AS 'Name'  
,xml_data.value('(event/@package)[1]','varchar(max)') AS 'Package'  
,xml_data.value('(event/@timestamp)[1]','datetime') AS 'Time'  
,xml_data.value('(event/data[@name=''state'']/value)[1]','int') AS 'State'  
,xml_data.value('(event/data[@name=''state_desc'']/text)[1]','varchar(max)') AS 'State Description'  
,xml_data.value('(event/data[@name=''failure_condition_level'']/value)[1]','int') AS 'Failure Conditions'  
,xml_data.value('(event/data[@name=''node_name'']/value)[1]','varchar(max)') AS 'Node_Name'  
,xml_data.value('(event/data[@name=''instancename'']/value)[1]','varchar(max)') AS 'Instance Name'  
,xml_data.value('(event/data[@name=''creation time'']/value)[1]','datetime') AS 'Creation Time'  
,xml_data.value('(event/data[@name=''component'']/value)[1]','varchar(max)') AS 'Component'  
,xml_data.value('(event/data[@name=''data'']/value)[1]','varchar(max)') AS 'Data'  
,xml_data.value('(event/data[@name=''info'']/value)[1]','varchar(max)') AS 'Info'  
FROM  
 ( SELECT object_name AS 'event'  
  ,CONVERT(xml,event_data) AS 'xml_data'  
  FROM sys.fn_xe_file_target_read_file('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log\SQLNODE1_MSSQLSERVER_SQLDIAG_0_129936003752530000.xel',NULL,NULL,NULL)   
)   
AS XEventData  
ORDER BY Time;  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="b7728-133">WHERE 句を使用して、特定のコンポーネントまたは状態の結果にフィルターを適用することができます。</span><span class="sxs-lookup"><span data-stu-id="b7728-133">You can filter the results for specific components or state using the WHERE clause.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlConfigure"></a> <span data-ttu-id="b7728-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b7728-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="b7728-135">**診断ログのプロパティを構成するには**</span><span class="sxs-lookup"><span data-stu-id="b7728-135">**To configure the Diagnostic Log Properties**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7728-136">この手順の例については、このセクションの後半の「 [例 (Transact-SQL)](#TsqlExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7728-136">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
 <span data-ttu-id="b7728-137">データ定義言語 (DDL) ステートメントを使用すると `ALTER SERVER CONFIGURATION` 、 [Sp_server_diagnostics &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)プロシージャによってキャプチャされた診断データのログ記録を開始または停止したり、SQLDIAG ログの構成パラメーター (ログファイルのロールオーバー数、ログファイルのサイズ、ファイルの場所など) を設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="b7728-137">Using the Data Definition Language (DDL) statement, `ALTER SERVER CONFIGURATION`, you can start or stop logging diagnostic data captured by the [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) procedure, and set SQLDIAG log configuration parameters such as the log file rollover count, log file size, and file location.</span></span> <span data-ttu-id="b7728-138">構文の詳細については、「 [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7728-138">For syntax details, see [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="ConfigTsqlExample"></a> <span data-ttu-id="b7728-139">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b7728-139">Examples (Transact-SQL)</span></span>  
  
####  <a name="setting-diagnostic-log-options"></a><a name="TsqlExample"></a> <span data-ttu-id="b7728-140">Setting diagnostic log options</span><span class="sxs-lookup"><span data-stu-id="b7728-140">Setting diagnostic log options</span></span>  
 <span data-ttu-id="b7728-141">このセクションの例では、診断ログ オプションの値を設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b7728-141">The examples in this section show how to set the values for the diagnostic log option.</span></span>  
  
##### <a name="a-starting-diagnostic-logging"></a><span data-ttu-id="b7728-142">A.</span><span class="sxs-lookup"><span data-stu-id="b7728-142">A.</span></span> <span data-ttu-id="b7728-143">診断ログの記録を開始する</span><span class="sxs-lookup"><span data-stu-id="b7728-143">Starting diagnostic logging</span></span>  
 <span data-ttu-id="b7728-144">次の例では、診断データのログ記録を開始します。</span><span class="sxs-lookup"><span data-stu-id="b7728-144">The following example starts the logging of diagnostic data.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG ON;  
```  
  
##### <a name="b-stopping-diagnostic-logging"></a><span data-ttu-id="b7728-145">B.</span><span class="sxs-lookup"><span data-stu-id="b7728-145">B.</span></span> <span data-ttu-id="b7728-146">診断ログの記録を停止する</span><span class="sxs-lookup"><span data-stu-id="b7728-146">Stopping diagnostic logging</span></span>  
 <span data-ttu-id="b7728-147">次の例では、診断データのログ記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="b7728-147">The following example stops the logging of diagnostic data.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG OFF;  
```  
  
##### <a name="c-specifying-the-location-of-the-diagnostic-logs"></a><span data-ttu-id="b7728-148">C.</span><span class="sxs-lookup"><span data-stu-id="b7728-148">C.</span></span> <span data-ttu-id="b7728-149">診断ログの場所を指定する</span><span class="sxs-lookup"><span data-stu-id="b7728-149">Specifying the location of the diagnostic logs</span></span>  
 <span data-ttu-id="b7728-150">次の例では、診断ログの場所を、指定されたファイル パスに設定します。</span><span class="sxs-lookup"><span data-stu-id="b7728-150">The following example sets the location of the diagnostic logs to the specified file path.</span></span>  
  
```  
ALTER SERVER CONFIGURATION  
SET DIAGNOSTICS LOG PATH = 'C:\logs';  
```  
  
##### <a name="d-specifying-the-maximum-size-of-each-diagnostic-log"></a><span data-ttu-id="b7728-151">D.</span><span class="sxs-lookup"><span data-stu-id="b7728-151">D.</span></span> <span data-ttu-id="b7728-152">各診断ログの最大サイズを指定する</span><span class="sxs-lookup"><span data-stu-id="b7728-152">Specifying the maximum size of each diagnostic log</span></span>  
 <span data-ttu-id="b7728-153">次の例では、各診断ログの最大サイズを 10 MB に設定します。</span><span class="sxs-lookup"><span data-stu-id="b7728-153">The following example set the maximum size of each diagnostic log to 10 megabytes.</span></span>  
  
```  
ALTER SERVER CONFIGURATION   
SET DIAGNOSTICS LOG MAX_SIZE = 10 MB;  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7728-154">参照</span><span class="sxs-lookup"><span data-stu-id="b7728-154">See Also</span></span>  
 [<span data-ttu-id="b7728-155">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="b7728-155">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
  
  
