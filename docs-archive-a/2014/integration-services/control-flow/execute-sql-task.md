---
title: SQL 実行タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- batches [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e77b9f442ae8478c57d5b0e68955b541eda38aff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713389"
---
# <a name="execute-sql-task"></a><span data-ttu-id="ec963-102">SQL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="ec963-102">Execute SQL Task</span></span>
  <span data-ttu-id="ec963-103">SQL 実行タスクは、パッケージ内の SQL ステートメントやストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="ec963-103">The Execute SQL task runs SQL statements or stored procedures from a package.</span></span> <span data-ttu-id="ec963-104">このタスクには、1 つの SQL ステートメントまたは順に実行される複数の SQL ステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ec963-104">The task can contain either a single SQL statement or multiple SQL statements that run sequentially.</span></span> <span data-ttu-id="ec963-105">SQL 実行タスクは、次の目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec963-105">You can use the Execute SQL task for the following purposes:</span></span>  
  
-   <span data-ttu-id="ec963-106">データを挿入する準備として、テーブルまたはビューを切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="ec963-106">Truncate a table or view in preparation for inserting data.</span></span>  
  
-   <span data-ttu-id="ec963-107">テーブル、ビューなどのデータベース オブジェクトを、作成、変更、および削除します。</span><span class="sxs-lookup"><span data-stu-id="ec963-107">Create, alter, and drop database objects such as tables and views.</span></span>  
  
-   <span data-ttu-id="ec963-108">データの読み込みを行う前にファクト テーブルとディメンション テーブルを再作成します。</span><span class="sxs-lookup"><span data-stu-id="ec963-108">Re-create fact and dimension tables before loading data into them.</span></span>  
  
-   <span data-ttu-id="ec963-109">ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="ec963-109">Run stored procedures.</span></span> <span data-ttu-id="ec963-110">SQL ステートメントで、一時テーブルから結果を返すストアド プロシージャが呼び出される場合は、WITH RESULT SETS オプションを使用して結果セットのメタデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="ec963-110">If the SQL statement invokes a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
-   <span data-ttu-id="ec963-111">クエリから返された行セットを変数に保存します。</span><span class="sxs-lookup"><span data-stu-id="ec963-111">Save the rowset returned from a query into a variable.</span></span>  
  
 <span data-ttu-id="ec963-112">SQL 実行タスクを Foreach ループや For ループ コンテナーと組み合わせて使用すると、複数の SQL ステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ec963-112">The Execute SQL task can be used in combination with the Foreach Loop and For Loop containers to run multiple SQL statements.</span></span> <span data-ttu-id="ec963-113">これらのコンテナーには、パッケージ内での繰り返し制御フローが実装されているため、SQL 実行タスクを繰り返して実行できます。</span><span class="sxs-lookup"><span data-stu-id="ec963-113">These containers implement repeating control flows in a package and they can run the Execute SQL task repeatedly.</span></span> <span data-ttu-id="ec963-114">たとえば、Foreach ループ コンテナーを使用すると、パッケージはフォルダー内のファイルを列挙して SQL 実行タスクを繰り返して実行し、各ファイルに格納された SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ec963-114">For example, using the Foreach Loop container, a package can enumerate files in a folder and run an Execute SQL task repeatedly to execute the SQL statement stored in each file.</span></span>  
  
## <a name="connecting-to-a-data-source"></a><span data-ttu-id="ec963-115">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="ec963-115">Connecting to a Data Source</span></span>  
 <span data-ttu-id="ec963-116">SQL 実行タスクでは、さまざまな種類の接続マネージャーを使用して、SQL ステートメントまたはストアド プロシージャを実行するデータ ソースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="ec963-116">The Execute SQL task can use different types of connection managers to connect to the data source where it runs the SQL statement or stored procedure.</span></span> <span data-ttu-id="ec963-117">このタスクが使用できる接続の種類の一覧を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="ec963-117">The task can use the connection types listed in the following table.</span></span>  
  
|<span data-ttu-id="ec963-118">接続の種類</span><span class="sxs-lookup"><span data-stu-id="ec963-118">Connection type</span></span>|<span data-ttu-id="ec963-119">[ODBC 入力元エディター]</span><span class="sxs-lookup"><span data-stu-id="ec963-119">Connection manager</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="ec963-120">EXCEL</span><span class="sxs-lookup"><span data-stu-id="ec963-120">EXCEL</span></span>|[<span data-ttu-id="ec963-121">Excel 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ec963-121">Excel Connection Manager</span></span>](../connection-manager/excel-connection-manager.md)|  
|<span data-ttu-id="ec963-122">OLE DB (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="ec963-122">OLE DB</span></span>|[<span data-ttu-id="ec963-123">OLE DB 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ec963-123">OLE DB Connection Manager</span></span>](../connection-manager/ole-db-connection-manager.md)|  
|<span data-ttu-id="ec963-124">ODBC</span><span class="sxs-lookup"><span data-stu-id="ec963-124">ODBC</span></span>|[<span data-ttu-id="ec963-125">ODBC 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ec963-125">ODBC Connection Manager</span></span>](../connection-manager/odbc-connection-manager.md)|  
|<span data-ttu-id="ec963-126">ADO (ADO)</span><span class="sxs-lookup"><span data-stu-id="ec963-126">ADO</span></span>|[<span data-ttu-id="ec963-127">ADO 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ec963-127">ADO Connection Manager</span></span>](../connection-manager/ado-connection-manager.md)|  
|<span data-ttu-id="ec963-128">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ec963-128">ADO.NET</span></span>|[<span data-ttu-id="ec963-129">ADO.NET 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ec963-129">ADO.NET Connection Manager</span></span>](../connection-manager/ado-net-connection-manager.md)|  
|<span data-ttu-id="ec963-130">SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="ec963-130">SQLMOBILE</span></span>|[<span data-ttu-id="ec963-131">SQL Server Compact Edition 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="ec963-131">SQL Server Compact Edition Connection Manager</span></span>](../connection-manager/sql-server-compact-edition-connection-manager.md)|  
  
## <a name="creating-sql-statements"></a><span data-ttu-id="ec963-132">SQL ステートメントの作成</span><span class="sxs-lookup"><span data-stu-id="ec963-132">Creating SQL Statements</span></span>  
 <span data-ttu-id="ec963-133">このタスクでは、タスクのプロパティを SQL ステートメントの実行元として使用できます。タスクのプロパティには、ステートメント、単数または複数のステートメントが含まれるファイルへの接続、またはステートメントが含まれる変数名を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ec963-133">The source of the SQL statements used by this task can be a task property that contains a statement, a connection to a file that contains one or multiple statements, or the name of a variable that contains a statement.</span></span> <span data-ttu-id="ec963-134">SQL ステートメントは、実行元のデータベース管理システム (DBMS) の言語仕様に従って作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec963-134">The SQL statements must be written in the dialect of the source database management system (DBMS).</span></span> <span data-ttu-id="ec963-135">詳細については、「[Integration Services &#40;SSIS&#41; のクエリ](../integration-services-ssis-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-135">For more information, see [Integration Services &#40;SSIS&#41; Queries](../integration-services-ssis-queries.md).</span></span>  
  
 <span data-ttu-id="ec963-136">SQL ステートメントがファイルに格納されている場合、タスクはファイル接続マネージャーを使用してそのファイルに接続します。</span><span class="sxs-lookup"><span data-stu-id="ec963-136">If the SQL statements are stored in a file, the task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="ec963-137">詳しくは「 [File Connection Manager](../connection-manager/file-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec963-137">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="ec963-138">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでは、 **[SQL 実行タスク エディター]** ダイアログ ボックスを使用して SQL ステートメントを入力できます。また、SQL クエリを作成するためのグラフィカル ユーザー インターフェイスである **クエリ ビルダー**を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec963-138">In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can use the **Execute SQL Task Editor** dialog box to type SQL statements, or use **Query Builder**, a graphical user interface for creating SQL queries.</span></span> <span data-ttu-id="ec963-139">詳細については、「[SQL 実行タスク エディター &#40;[全般] タブ&#41;](../execute-sql-task-editor-general-page.md)」と「[クエリ ](../query-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-139">For more information, see [Execute SQL Task Editor &#40;General Page&#41;](../execute-sql-task-editor-general-page.md) and [Query Builder](../query-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec963-140">有効な SQL ステートメントが SQL 実行タスクの外部に記述されている場合、SQL 実行タスクは解析に失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="ec963-140">Valid SQL statements written outside the Execute SQL task may not be parsed successfully by the Execute SQL task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec963-141">SQL 実行タスクは `RecognizeAll` ParseMode の列挙値を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec963-141">The Execute SQL Task uses the `RecognizeAll` ParseMode enumeration value.</span></span> <span data-ttu-id="ec963-142">詳細については、「 [ManagedBatchParser 名前空間](https://go.microsoft.com/fwlink/?LinkId=223617)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-142">For more information, see [ManagedBatchParser Namespace](https://go.microsoft.com/fwlink/?LinkId=223617).</span></span>  
  
## <a name="sending-multiple-statements-in-a-batch"></a><span data-ttu-id="ec963-143">複数のステートメントの一括送信</span><span class="sxs-lookup"><span data-stu-id="ec963-143">Sending Multiple Statements in a Batch</span></span>  
 <span data-ttu-id="ec963-144">SQL 実行タスクに複数のステートメントが含まれる場合、それらをグループ化してバッチとして実行できます。</span><span class="sxs-lookup"><span data-stu-id="ec963-144">If you include multiple statements in an Execute SQL task, you can group them and run them as a batch.</span></span> <span data-ttu-id="ec963-145">バッチの開始と終了を知らせるには、GO コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec963-145">To signal the end of a batch, use the GO command.</span></span> <span data-ttu-id="ec963-146">2 つの GO コマンド間にあるすべての SQL ステートメントは、OLE DB プロバイダーにバッチで送信されて実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec963-146">All the SQL statements between two GO commands are sent in a batch to the OLE DB provider to be run.</span></span> <span data-ttu-id="ec963-147">SQL コマンドには、GO コマンドで分割された複数のバッチを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ec963-147">The SQL command can include multiple batches separated by GO commands.</span></span>  
  
 <span data-ttu-id="ec963-148">グループ化してバッチに含めることができる SQL ステートメントの種類には制限があります。</span><span class="sxs-lookup"><span data-stu-id="ec963-148">There are restrictions on the kinds of SQL statements that you can group in a batch.</span></span> <span data-ttu-id="ec963-149">詳細については、「 [ステートメントのバッチ](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-149">For more information, see [Batches of Statements](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md).</span></span>  
  
 <span data-ttu-id="ec963-150">SQL 実行タスクで SQL ステートメントのバッチを実行する場合、バッチには次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="ec963-150">If the Execute SQL task runs a batch of SQL statements, the following rules apply to the batch:</span></span>  
  
-   <span data-ttu-id="ec963-151">結果セットを返すことができるのは、バッチの最初のステートメント 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="ec963-151">Only one statement can return a result set and it must be the first statement in the batch.</span></span>  
  
-   <span data-ttu-id="ec963-152">結果セットで結果のバインドを使用する場合、クエリは同じ数の列を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec963-152">If the result set uses result bindings, the queries must return the same number of columns.</span></span> <span data-ttu-id="ec963-153">クエリが異なる数の列を返した場合、タスクは失敗します。</span><span class="sxs-lookup"><span data-stu-id="ec963-153">If the queries return a different number of columns, the task fails.</span></span> <span data-ttu-id="ec963-154">ただし、タスクが失敗しても、そのタスクによって実行された DELETE や INSERT などのクエリは成功する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec963-154">However, even if the task fails, the queries that it runs, such as DELETE or INSERT queries, may succeed.</span></span>  
  
-   <span data-ttu-id="ec963-155">結果のバインドで列名を使用する場合、クエリは、タスクで使用される結果セットの名前と同じ名前の列を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec963-155">If the result bindings use column names, the query must return columns that have the same names as the result set names that are used in the task.</span></span> <span data-ttu-id="ec963-156">列が存在しない場合、タスクは失敗します。</span><span class="sxs-lookup"><span data-stu-id="ec963-156">If the columns are missing, the task fails.</span></span>  
  
-   <span data-ttu-id="ec963-157">タスクでパラメーターのバインドを使用する場合、バッチ内のすべてのクエリは、同じ数と種類のパラメーターを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec963-157">If the task uses parameter binding, all the queries in the batch must have the same number and types of parameters.</span></span>  
  
## <a name="running-parameterized-sql-commands"></a><span data-ttu-id="ec963-158">パラメーター化 SQL コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="ec963-158">Running Parameterized SQL Commands</span></span>  
 <span data-ttu-id="ec963-159">SQL ステートメントとストアド プロシージャでは多くの場合、入力パラメーター、出力パラメーター、およびリターン コードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec963-159">SQL statements and stored procedures frequently use input parameters, output parameters, and return codes.</span></span> <span data-ttu-id="ec963-160">SQL 実行タスクでは、`Input`、`Output`、および `ReturnValue` パラメーター型がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ec963-160">The Execute SQL task supports the `Input`, `Output`, and `ReturnValue` parameter types.</span></span> <span data-ttu-id="ec963-161">入力パラメーターには `Input` 型、出力パラメーターには `Output` 型、およびリターン コードには `ReturnValue` 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec963-161">You use the `Input` type for input parameters, `Output` for output parameters, and `ReturnValue` for return codes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec963-162">SQL 実行タスクでは、データ プロバイダーがサポートしている場合のみ、パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec963-162">You can use parameters in an Execute SQL task only if the data provider supports them.</span></span>  
  
 <span data-ttu-id="ec963-163">SQL 実行タスクにおけるパラメーターとリターン コードの使用については、「 [SQL 実行タスクのパラメーターとリターン コード](execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-163">For information on using parameters and return codes in the Execute SQL task, see [Parameters and Return Codes in the Execute SQL Task](execute-sql-task.md).</span></span>  
  
## <a name="specifying-a-result-set-type"></a><span data-ttu-id="ec963-164">結果セットの種類の指定</span><span class="sxs-lookup"><span data-stu-id="ec963-164">Specifying a Result Set Type</span></span>  
 <span data-ttu-id="ec963-165">結果セットが SQL 実行タスクに返されるかどうかは、SQL コマンドの種類によって決まります。</span><span class="sxs-lookup"><span data-stu-id="ec963-165">Depending on the type of SQL command, a result set may or may not be returned to the Execute SQL task.</span></span> <span data-ttu-id="ec963-166">たとえば、通常、SELECT ステートメントは結果セットを返しますが、INSERT ステートメントは返しません。</span><span class="sxs-lookup"><span data-stu-id="ec963-166">For example, a SELECT statement typically returns a result set, but an INSERT statement does not.</span></span> <span data-ttu-id="ec963-167">SELECT ステートメントからの結果セットに含まれる行数は、0 行、1 行、または多数行である場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec963-167">The result set from a SELECT statement can contain zero rows, one row, or many rows.</span></span> <span data-ttu-id="ec963-168">また、ストアド プロシージャは、プロシージャの実行状態を示すリターン コードという整数値を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="ec963-168">Stored procedures can also return an integer value, called a return code, that indicates the execution status of the procedure.</span></span> <span data-ttu-id="ec963-169">この場合、結果セットは 1 行で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ec963-169">In that case, the result set consists of a single row.</span></span>  
  
 <span data-ttu-id="ec963-170">SQL 実行タスクにおける SQL コマンドからの結果セットの取得については、「 [SQL 実行タスクにおける結果セット](../result-sets-in-the-execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-170">For information on retrieving result sets from SQL commands in the Execute SQL task, see [Result Sets in the Execute SQL Task](../result-sets-in-the-execute-sql-task.md).</span></span>  
  
## <a name="troubleshooting-the-execute-sql-task"></a><span data-ttu-id="ec963-171">SQL 実行タスクのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ec963-171">Troubleshooting the Execute SQL Task</span></span>  
 <span data-ttu-id="ec963-172">SQL 実行タスクによる外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="ec963-172">You can log the calls that the Execute SQL task makes to external data providers.</span></span> <span data-ttu-id="ec963-173">このログ機能を使用すると、SQL 実行タスクが実行する SQL コマンドに関するトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ec963-173">You can use this logging capability to troubleshoot the SQL commands that the Execute SQL task runs.</span></span> <span data-ttu-id="ec963-174">SQL 実行タスクによる外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択します。</span><span class="sxs-lookup"><span data-stu-id="ec963-174">To log the calls that the Execute SQL task makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="ec963-175">詳細については、「 [パッケージ実行のトラブルシューティング ツール](../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-175">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="ec963-176">SQL コマンドまたはストアド プロシージャから、複数の結果セットが返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec963-176">Sometimes a SQL command or stored procedure returns multiple result sets.</span></span> <span data-ttu-id="ec963-177">このような結果セットには、`SELECT` クエリの結果である行セットだけでなく、`RAISERROR` ステートメントまたは `PRINT` ステートメントのエラーの結果である単一値も含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec963-177">These result sets include not only rowsets that are the result of `SELECT` queries, but single values that are the result of errors of `RAISERROR` or `PRINT` statements.</span></span> <span data-ttu-id="ec963-178">1 つ目以外の結果セット内のエラーがタスクで無視されるかどうかは、使用する接続マネージャーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ec963-178">Whether the task ignores errors in result sets that occur after the first result set depends on the type of connection manager that is used:</span></span>  
  
-   <span data-ttu-id="ec963-179">OLE DB 接続マネージャーおよび ADO 接続マネージャーを使用する場合、1 つ目の結果セット以外はすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="ec963-179">When you use OLE DB and ADO connection managers, the task ignores the result sets that occur after the first result set.</span></span> <span data-ttu-id="ec963-180">したがって、これらの接続マネージャーでは、SQL コマンドまたはストアド プロシージャから返されるエラーは、1 つ目の結果セットに含まれていない限りタスクで無視されます。</span><span class="sxs-lookup"><span data-stu-id="ec963-180">Therefore, with these connection managers, the task ignores an error returned by an SQL command or a stored procedure when the error is not part of the first result set.</span></span>  
  
-   <span data-ttu-id="ec963-181">ODBC 接続マネージャーおよび ADO.NET 接続マネージャーを使用する場合、1 つ目の結果セット以外も無視されません。</span><span class="sxs-lookup"><span data-stu-id="ec963-181">When you use ODBC and ADO.NET connection managers, the task does not ignore result sets that occur after the first result set.</span></span> <span data-ttu-id="ec963-182">これらの接続マネージャーでは、2 つ目以降の結果セットにエラーが含まれていると、エラーが発生してタスクが失敗します。</span><span class="sxs-lookup"><span data-stu-id="ec963-182">With these connection managers, the task will fail with an error when a result set other than the first result set contains an error.</span></span>  
  
### <a name="custom-log-entries"></a><span data-ttu-id="ec963-183">カスタム ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="ec963-183">Custom Log Entries</span></span>  
 <span data-ttu-id="ec963-184">次の表では、SQL 実行タスクのカスタム ログ エントリを説明します。</span><span class="sxs-lookup"><span data-stu-id="ec963-184">The following table describes the custom log entry for the Execute SQL task.</span></span> <span data-ttu-id="ec963-185">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec963-185">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="ec963-186">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="ec963-186">Log entry</span></span>|<span data-ttu-id="ec963-187">説明</span><span class="sxs-lookup"><span data-stu-id="ec963-187">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|<span data-ttu-id="ec963-188">SQL ステートメントの実行フェーズに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ec963-188">Provides information about the execution phases of the SQL statement.</span></span> <span data-ttu-id="ec963-189">タスクがデータベースへの接続を取得したとき、SQL ステートメントの準備が開始されたとき、および SQL ステートメントの実行が完了した後に、ログ エントリが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ec963-189">Log entries are written when the task acquires connection to the database, when the task starts to prepare the SQL statement, and after the execution of the SQL statement is completed.</span></span> <span data-ttu-id="ec963-190">準備フェーズのログ エントリには、タスクで使用される SQL ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ec963-190">The log entry for the prepare phase includes the SQL statement that the task uses.</span></span>|  
  
## <a name="configuring-the-execute-sql-task"></a><span data-ttu-id="ec963-191">SQL 実行タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ec963-191">Configuring the Execute SQL Task</span></span>  
 <span data-ttu-id="ec963-192">SQL 実行タスクは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="ec963-192">You can configure the Execute SQL task in the following ways:</span></span>  
  
-   <span data-ttu-id="ec963-193">データベースへの接続に使用する接続マネージャーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="ec963-193">Specify the type of connection manager to use to connect to a database.</span></span>  
  
-   <span data-ttu-id="ec963-194">SQL ステートメントが返す結果セットの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="ec963-194">Specify the type of result set that the SQL statement returns.</span></span>  
  
-   <span data-ttu-id="ec963-195">SQL ステートメントのタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="ec963-195">Specify a time-out for the SQL statements.</span></span>  
  
-   <span data-ttu-id="ec963-196">SQL ステートメントの実行元を指定します。</span><span class="sxs-lookup"><span data-stu-id="ec963-196">Specify the source of the SQL statement.</span></span>  
  
-   <span data-ttu-id="ec963-197">SQL ステートメントの準備フェーズをタスクがスキップするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ec963-197">Indicate whether the task skips the prepare phase for the SQL statement.</span></span>  
  
-   <span data-ttu-id="ec963-198">ADO 接続の種類を使用している場合、SQL ステートメントがストアド プロシージャかどうかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec963-198">If you use the ADO connection type, you must indicate whether the SQL statement is a stored procedure.</span></span> <span data-ttu-id="ec963-199">その他の接続の種類では、このプロパティは読み取り専用であり、値は常に `false` です。</span><span class="sxs-lookup"><span data-stu-id="ec963-199">For other connection types, this property is read-only and its value is always `false`.</span></span>  
  
 <span data-ttu-id="ec963-200">プロパティはプログラムによって設定するか、または [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="ec963-200">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="ec963-201">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-201">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="ec963-202">[[SQL 実行タスクエディター] &#40;[全般] ページ&#41;](../execute-sql-task-editor-general-page.md)</span><span class="sxs-lookup"><span data-stu-id="ec963-202">[Execute SQL Task Editor &#40;General Page&#41;](../execute-sql-task-editor-general-page.md)</span></span>  
  
-   <span data-ttu-id="ec963-203">[[SQL 実行タスクエディター] &#40;[パラメーターマッピング] ページ&#41;](../execute-sql-task-editor-parameter-mapping-page.md)</span><span class="sxs-lookup"><span data-stu-id="ec963-203">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../execute-sql-task-editor-parameter-mapping-page.md)</span></span>  
  
-   <span data-ttu-id="ec963-204">[[SQL 実行タスクエディター &#40;結果セット] ページ&#41;](../execute-sql-task-editor-result-set-page.md)</span><span class="sxs-lookup"><span data-stu-id="ec963-204">[Execute SQL Task Editor &#40;Result Set Page&#41;](../execute-sql-task-editor-result-set-page.md)</span></span>  
  
-   <span data-ttu-id="ec963-205">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="ec963-205">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="ec963-206">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-206">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="ec963-207">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="ec963-207">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="configuring-the-execute-sql-task-programmatically"></a><span data-ttu-id="ec963-208">プログラムによる SQL 実行タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ec963-208">Configuring the Execute SQL Task Programmatically</span></span>  
 <span data-ttu-id="ec963-209">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec963-209">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="ec963-210">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ec963-210">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ec963-211">クエリ パラメーターを SQL 実行タスクの変数にマップする方法</span><span class="sxs-lookup"><span data-stu-id="ec963-211">Map Query Parameters to Variables in an Execute SQL Task</span></span>](../map-query-parameters-to-variables-in-an-execute-sql-task.md)  
  
-   [<span data-ttu-id="ec963-212">結果セットを SQL 実行タスクの変数にマップする</span><span class="sxs-lookup"><span data-stu-id="ec963-212">Map Result Sets to Variables in an Execute SQL Task</span></span>](../map-result-sets-to-variables-in-an-execute-sql-task.md)  
  
## <a name="related-content"></a><span data-ttu-id="ec963-213">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ec963-213">Related Content</span></span>  
  
-   [<span data-ttu-id="ec963-214">SQL 実行タスクのパラメーターとリターン コード</span><span class="sxs-lookup"><span data-stu-id="ec963-214">Parameters and Return Codes in the Execute SQL Task</span></span>](execute-sql-task.md)  
  
-   [<span data-ttu-id="ec963-215">SQL 実行タスクにおける結果セット</span><span class="sxs-lookup"><span data-stu-id="ec963-215">Result Sets in the Execute SQL Task</span></span>](../result-sets-in-the-execute-sql-task.md)  
  
-   [<span data-ttu-id="ec963-216">TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="ec963-216">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
-   <span data-ttu-id="ec963-217">mssqltips.com のブログ「 [SQL Server 2012 の新しい日付と時刻の関数](https://go.microsoft.com/fwlink/?LinkId=239783)」</span><span class="sxs-lookup"><span data-stu-id="ec963-217">Blog entry, [New Date and Time Functions in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=239783), on mssqltips.com</span></span>  
  
  
