---
title: '[SQL 実行タスクエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.general.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: beb39086-28ce-46af-b6d8-f7b4fb8d9069
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 32bec035646c976442eb66ff1270b961835b243b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633221"
---
# <a name="execute-sql-task-editor-general-page"></a><span data-ttu-id="18c71-102">[SQL 実行タスク エディター] ([全般] タブ)</span><span class="sxs-lookup"><span data-stu-id="18c71-102">Execute SQL Task Editor (General Page)</span></span>
  <span data-ttu-id="18c71-103">**[SQL 実行タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、SQL 実行タスクを構成したり、タスクが実行する SQL ステートメントを指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="18c71-103">Use the **General** page of the **Execute SQL Task Editor** dialog box to configure the Execute SQL task and provide the SQL statement that the task runs.</span></span>  
  
 <span data-ttu-id="18c71-104">このタスクの詳細については、「[SQL 実行タスク](control-flow/execute-sql-task.md)」、「[SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)」、および「[SQL 実行タスクにおける結果セット](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18c71-104">To learn about this task, see [Execute SQL Task](control-flow/execute-sql-task.md), [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md), and [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).</span></span> <span data-ttu-id="18c71-105">Transact-SQL クエリ言語の詳細については、「[Transact-SQL リファレンス &#40;データベース エンジン&#41;](/sql/t-sql/language-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18c71-105">To learn more about the Transact-SQL query language, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="18c71-106">静的オプション</span><span class="sxs-lookup"><span data-stu-id="18c71-106">Static Options</span></span>  
 <span data-ttu-id="18c71-107">**名前**</span><span class="sxs-lookup"><span data-stu-id="18c71-107">**Name**</span></span>  
 <span data-ttu-id="18c71-108">ワークフロー内の SQL 実行タスクに一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="18c71-108">Provide a unique name for the Execute SQL task in the workflow.</span></span> <span data-ttu-id="18c71-109">指定された名前は [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="18c71-109">The name that is provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="18c71-110">**説明**</span><span class="sxs-lookup"><span data-stu-id="18c71-110">**Description**</span></span>  
 <span data-ttu-id="18c71-111">SQL 実行タスクの説明です。</span><span class="sxs-lookup"><span data-stu-id="18c71-111">Describe the Execute SQL task.</span></span> <span data-ttu-id="18c71-112">パッケージを自己文書化して目的を明確にし、保守が容易になるように、タスクの目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="18c71-112">As a best practice, to make packages self-documenting and easier to maintain, describe the task in terms of its purpose.</span></span>  
  
 <span data-ttu-id="18c71-113">**[TimeOut]**</span><span class="sxs-lookup"><span data-stu-id="18c71-113">**TimeOut**</span></span>  
 <span data-ttu-id="18c71-114">タスクがタイムアウトになるまでに実行される最大の秒数を指定します。この値に 0 を指定すると、時間は無制限になります。</span><span class="sxs-lookup"><span data-stu-id="18c71-114">Specify the maximum number of seconds the task will run before timing out. A value of 0 indicates an infinite time.</span></span> <span data-ttu-id="18c71-115">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="18c71-115">The default is 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18c71-116">接続してトランザクションを完了するための時間を、 **[TimeOut]** で指定された秒数よりも長く指定することによってスリープ機能をエミュレートする場合、ストアド プロシージャはタイムアウトになりません。</span><span class="sxs-lookup"><span data-stu-id="18c71-116">Stored procedures do not time out if they emulate sleep functionality by providing time for connections to be made and transactions to complete that is greater than the number of seconds specified by **TimeOut**.</span></span> <span data-ttu-id="18c71-117">ただし、クエリを実行するストアド プロシージャは、 **[TimeOut]** で指定された時間制限の影響を常に受けます。</span><span class="sxs-lookup"><span data-stu-id="18c71-117">However, stored procedures that execute queries are always subject to the time restriction specified by **TimeOut**.</span></span>  
  
 <span data-ttu-id="18c71-118">**CodePage**</span><span class="sxs-lookup"><span data-stu-id="18c71-118">**CodePage**</span></span>  
 <span data-ttu-id="18c71-119">変数の Unicode 値を変換するときに使用するコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="18c71-119">Specify the code page to use when translating Unicode values in variables.</span></span> <span data-ttu-id="18c71-120">既定値は、ローカル コンピューターのコード ページです。</span><span class="sxs-lookup"><span data-stu-id="18c71-120">The default value is the code page of the local computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18c71-121">SQL 実行タスクで ADO 接続マネージャーまたは ODBC 接続マネージャーを使用する場合、 **[CodePage]** プロパティは使用できません。</span><span class="sxs-lookup"><span data-stu-id="18c71-121">When the Execute SQL task uses an ADO or ODBC connection manager, the **CodePage** property is not available.</span></span> <span data-ttu-id="18c71-122">ソリューションでコード ページを使用する必要がある場合は、SQL 実行タスクで OLE DB 接続マネージャーまたは ADO.NET 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="18c71-122">If your solution requires the use of a code page, use an OLE DB or an ADO.NET connection manager with the Execute SQL task.</span></span>  
  
 <span data-ttu-id="18c71-123">**[TypeConversionMode]**</span><span class="sxs-lookup"><span data-stu-id="18c71-123">**TypeConversionMode**</span></span>  
 <span data-ttu-id="18c71-124">このプロパティを `Allowed` に設定すると、SQL 実行タスクは出力パラメーターとクエリ結果を結果が割り当てられている変数のデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="18c71-124">When you set this property to `Allowed`, the Execute SQL Task will attempt to convert output parameter and query results to the data type of the variable the results are assigned to.</span></span> <span data-ttu-id="18c71-125">この機能は、結果セットの種類が **単一行** の場合に適用されます。</span><span class="sxs-lookup"><span data-stu-id="18c71-125">This applies to the **Single row** result set type.</span></span>  
  
 <span data-ttu-id="18c71-126">**[ResultSet]**</span><span class="sxs-lookup"><span data-stu-id="18c71-126">**ResultSet**</span></span>  
 <span data-ttu-id="18c71-127">SQL ステートメントの実行によって予測される結果の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="18c71-127">Specify the result type expected by the SQL statement being run.</span></span> <span data-ttu-id="18c71-128">**[単一行]** 、 **[完全な結果セット]** 、 **[XML]** 、または **[なし]** から選択します。</span><span class="sxs-lookup"><span data-stu-id="18c71-128">Choose among **Single row**, **Full result set**, **XML**, or **None**.</span></span>  
  
 <span data-ttu-id="18c71-129">**ConnectionType**</span><span class="sxs-lookup"><span data-stu-id="18c71-129">**ConnectionType**</span></span>  
 <span data-ttu-id="18c71-130">データ ソースへの接続に使用する接続マネージャーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="18c71-130">Choose the type of connection manager to use to connect to the data source.</span></span> <span data-ttu-id="18c71-131">使用可能な接続の種類は、 **[OLE DB]** 、 **[ODBC]** 、 **[ADO]** 、 **[ADO.NET]** 、および **[SQLMOBILE]** です。</span><span class="sxs-lookup"><span data-stu-id="18c71-131">Available connection types include **OLE DB**, **ODBC**, **ADO**, **ADO.NET** and **SQLMOBILE**.</span></span>  
  
 <span data-ttu-id="18c71-132">**関連トピック:** [OLE DB 接続マネージャー](connection-manager/ole-db-connection-manager.md)、[ODBC 接続マネージャー](connection-manager/odbc-connection-manager.md)、[ADO 接続マネージャー](connection-manager/ado-connection-manager.md)、[ADO.NET 接続マネージャー](connection-manager/ado-net-connection-manager.md)、[SQL Server Compact Edition 接続マネージャー](connection-manager/sql-server-compact-edition-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="18c71-132">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [ODBC Connection Manager](connection-manager/odbc-connection-manager.md), [ADO Connection Manager](connection-manager/ado-connection-manager.md), [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [SQL Server Compact Edition Connection Manager](connection-manager/sql-server-compact-edition-connection-manager.md)</span></span>  
  
 <span data-ttu-id="18c71-133">**接続**</span><span class="sxs-lookup"><span data-stu-id="18c71-133">**Connection**</span></span>  
 <span data-ttu-id="18c71-134">定義済みの接続マネージャーの一覧から接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="18c71-134">Choose the connection from a list of defined connection managers.</span></span> <span data-ttu-id="18c71-135">新しい接続を作成するには、[\<**New connection...**>] を選択します。</span><span class="sxs-lookup"><span data-stu-id="18c71-135">To create a new connection, select \<**New connection...**>.</span></span>  
  
 <span data-ttu-id="18c71-136">**[SQLSourceType]**</span><span class="sxs-lookup"><span data-stu-id="18c71-136">**SQLSourceType**</span></span>  
 <span data-ttu-id="18c71-137">タスクが実行する SQL ステートメントのソースの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="18c71-137">Select the source type of the SQL statement that the task runs.</span></span>  
  
 <span data-ttu-id="18c71-138">SQL 実行タスクが使用する接続マネージャーの種類によって、パラメーター化された SQL ステートメントで特定のパラメーター マーカーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18c71-138">Depending on the connection manager type that Execute SQL task uses, you must use specific parameter markers in parameterized SQL statements.</span></span>  
  
 <span data-ttu-id="18c71-139">**関連項目:** : 「 [SQL 実行タスク](control-flow/execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="18c71-139">**Related Topics:** Running Parameterized SQL Commands section in [Execute SQL Task](control-flow/execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="18c71-140">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="18c71-140">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="18c71-141">値</span><span class="sxs-lookup"><span data-stu-id="18c71-141">Value</span></span>|<span data-ttu-id="18c71-142">説明</span><span class="sxs-lookup"><span data-stu-id="18c71-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="18c71-143">**[直接入力]**</span><span class="sxs-lookup"><span data-stu-id="18c71-143">**Direct input**</span></span>|<span data-ttu-id="18c71-144">Transact-SQL ステートメントをソースに設定します。</span><span class="sxs-lookup"><span data-stu-id="18c71-144">Set the source to a Transact-SQL statement.</span></span> <span data-ttu-id="18c71-145">この値を選択すると、動的オプション **[SQLStatement]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18c71-145">Selecting this value displays the dynamic option, **SQLStatement**.</span></span>|  
|<span data-ttu-id="18c71-146">**[ファイル接続]**</span><span class="sxs-lookup"><span data-stu-id="18c71-146">**File connection**</span></span>|<span data-ttu-id="18c71-147">Transact-SQL ステートメントを含んでいるファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="18c71-147">Select a file that contains a Transact-SQL statement.</span></span> <span data-ttu-id="18c71-148">この値を設定すると、動的オプション **[ファイル接続]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18c71-148">Setting this option displays the dynamic option, **FileConnection**.</span></span>|  
|<span data-ttu-id="18c71-149">**変数**</span><span class="sxs-lookup"><span data-stu-id="18c71-149">**Variable**</span></span>|<span data-ttu-id="18c71-150">Transact-SQL ステートメントを定義する変数をソースに設定します。</span><span class="sxs-lookup"><span data-stu-id="18c71-150">Set the source to a variable that defines the Transact-SQL statement.</span></span> <span data-ttu-id="18c71-151">この値を選択すると、動的オプション **[SourceVariable]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18c71-151">Selecting this value displays the dynamic option, **SourceVariable**.</span></span>|  
  
 <span data-ttu-id="18c71-152">**[QueryIsStoredProcedure]**</span><span class="sxs-lookup"><span data-stu-id="18c71-152">**QueryIsStoredProcedure**</span></span>  
 <span data-ttu-id="18c71-153">実行が指定された SQL ステートメントがストアド プロシージャかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="18c71-153">Indicates whether the specified SQL statement to be run is a stored procedure.</span></span> <span data-ttu-id="18c71-154">このプロパティは、タスクが ADO 接続マネージャーを使用する場合のみ、読み取り/書き込みになります。</span><span class="sxs-lookup"><span data-stu-id="18c71-154">This property is read/write only if the task uses the ADO connection manager.</span></span> <span data-ttu-id="18c71-155">それ以外の場合、このプロパティは読み取り専用となり、その値は `false` となります。</span><span class="sxs-lookup"><span data-stu-id="18c71-155">Otherwise the property is read-only and its value is `false`.</span></span>  
  
 <span data-ttu-id="18c71-156">**[BypassPrepare]**</span><span class="sxs-lookup"><span data-stu-id="18c71-156">**BypassPrepare**</span></span>  
 <span data-ttu-id="18c71-157">SQL ステートメントが準備されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="18c71-157">Indicate whether the SQL statement is prepared.</span></span>  <span data-ttu-id="18c71-158">`true` の場合は準備がスキップされ、`false` の場合は実行の前に SQL ステートメントが準備されます。</span><span class="sxs-lookup"><span data-stu-id="18c71-158">`true` skips preparation; `false` prepares the SQL statement before running it.</span></span> <span data-ttu-id="18c71-159">このオプションは、準備をサポートしている OLE DB 接続の場合のみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="18c71-159">This option is available only with OLE DB connections that support preparation.</span></span>  
  
 <span data-ttu-id="18c71-160">**関連トピック:** [準備実行](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)</span><span class="sxs-lookup"><span data-stu-id="18c71-160">**Related Topics:**  [Prepared Execution](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)</span></span>  
  
 <span data-ttu-id="18c71-161">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="18c71-161">**Browse**</span></span>  
 <span data-ttu-id="18c71-162">**[開く]** ダイアログ ボックスを使用して、SQL ステートメントを含むファイルの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="18c71-162">Locate a file that contains a SQL statement by using the **Open** dialog box.</span></span> <span data-ttu-id="18c71-163">ファイルを選択して、ファイルの内容を SQL ステートメントとして **[SQLStatement]** プロパティにコピーします。</span><span class="sxs-lookup"><span data-stu-id="18c71-163">Select a file to copy the contents of the file as a SQL statement into the **SQLStatement** property.</span></span>  
  
 <span data-ttu-id="18c71-164">**[クエリの作成]**</span><span class="sxs-lookup"><span data-stu-id="18c71-164">**Build Query**</span></span>  
 <span data-ttu-id="18c71-165">クエリの作成に使用するグラフィカルなツールである **[クエリ ビルダー]** ダイアログ ボックスを使用して SQL ステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="18c71-165">Create an SQL statement using the **Query Builder** dialog box, a graphical tool used to create queries.</span></span> <span data-ttu-id="18c71-166">このオプションは、 **[SQLSourceType]** オプションが **[直接入力]** に設定されている場合に使用可能です。</span><span class="sxs-lookup"><span data-stu-id="18c71-166">This option is available when the **SQLSourceType** option is set to **Direct input**.</span></span>  
  
 <span data-ttu-id="18c71-167">**[クエリの解析]**</span><span class="sxs-lookup"><span data-stu-id="18c71-167">**Parse Query**</span></span>  
 <span data-ttu-id="18c71-168">SQL ステートメントの構文を検証します。</span><span class="sxs-lookup"><span data-stu-id="18c71-168">Validate the syntax of the SQL statement.</span></span>  
  
## <a name="sqlsourcetype-dynamic-options"></a><span data-ttu-id="18c71-169">[SQLSourceType] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="18c71-169">SQLSourceType Dynamic Options</span></span>  
  
### <a name="sqlsourcetype--direct-input"></a><span data-ttu-id="18c71-170">[SQLSourceType] = [直接入力]</span><span class="sxs-lookup"><span data-stu-id="18c71-170">SQLSourceType = Direct input</span></span>  
 <span data-ttu-id="18c71-171">**[SQLStatement]**</span><span class="sxs-lookup"><span data-stu-id="18c71-171">**SQLStatement**</span></span>  
 <span data-ttu-id="18c71-172">実行する SQL ステートメントをオプション ボックスに入力するか、参照ボタン ([...]) をクリックして **[SQL クエリの入力]** ダイアログ ボックスに SQL ステートメントを入力するか、 **[クエリの作成]** をクリックして **[クエリ ビルダー]** ダイアログ ボックスでステートメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="18c71-172">Type the SQL statement to execute in the option box, or click the browse button (...) to type the SQL statement in the **Enter SQL Query** dialog box, or click **Build Query** to compose the statement using the **Query Builder** dialog box.</span></span>  
  
 <span data-ttu-id="18c71-173">**関連トピック:** [クエリ ビルダー](../../2014/integration-services/query-builder.md)</span><span class="sxs-lookup"><span data-stu-id="18c71-173">**Related Topics:** [Query Builder](../../2014/integration-services/query-builder.md)</span></span>  
  
### <a name="sqlsourcetype--file-connection"></a><span data-ttu-id="18c71-174">[SQLSourceType] = [ファイル接続]</span><span class="sxs-lookup"><span data-stu-id="18c71-174">SQLSourceType = File connection</span></span>  
 <span data-ttu-id="18c71-175">**[FileConnection]**</span><span class="sxs-lookup"><span data-stu-id="18c71-175">**FileConnection**</span></span>  
 <span data-ttu-id="18c71-176">既存のファイル接続マネージャーを選択するか、[\<**New connection...**>] をクリックして、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="18c71-176">Select an existing File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="18c71-177">**関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="18c71-177">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="sqlsourcetype--variable"></a><span data-ttu-id="18c71-178">[SQLSourceType] = [変数]</span><span class="sxs-lookup"><span data-stu-id="18c71-178">SQLSourceType = Variable</span></span>  
 <span data-ttu-id="18c71-179">**[SourceVariable]**</span><span class="sxs-lookup"><span data-stu-id="18c71-179">**SourceVariable**</span></span>  
 <span data-ttu-id="18c71-180">既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="18c71-180">Select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="18c71-181">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="18c71-181">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18c71-182">参照</span><span class="sxs-lookup"><span data-stu-id="18c71-182">See Also</span></span>  
 <span data-ttu-id="18c71-183">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="18c71-183">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="18c71-184">[[SQL 実行タスクエディター] &#40;[パラメーターマッピング] ページ&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span><span class="sxs-lookup"><span data-stu-id="18c71-184">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span></span>  
 <span data-ttu-id="18c71-185">[[SQL 実行タスクエディター &#40;結果セット] ページ&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)</span><span class="sxs-lookup"><span data-stu-id="18c71-185">[Execute SQL Task Editor &#40;Result Set Page&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)</span></span>  
  
  
