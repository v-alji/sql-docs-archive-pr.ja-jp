---
title: ログ記録用のカスタムメッセージ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], custom
- writing log entries
- SSIS packages, logs
- custom messages for logging [Integration Services]
ms.assetid: 3c74bba9-02b7-4bf5-bad5-19278b680730
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2b9f450c74ef6d46876adfde45729c71b3262449
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641173"
---
# <a name="custom-messages-for-logging"></a><span data-ttu-id="aa3f6-102">ログ記録用のカスタム メッセージ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-102">Custom Messages for Logging</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="aa3f6-103">には、パッケージや多くのタスクのログ エントリを書き込むための豊富なカスタム イベントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-103">provides a rich set of custom events for writing log entries for packages and many tasks.</span></span> <span data-ttu-id="aa3f6-104">記録したエントリを使用すれば、定義済みのイベントやユーザー定義メッセージを後の分析用に記録しておくことで、実行の進行状況、結果、および問題点に関する詳細を保管できます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-104">You can use these entries to save detailed information about execution progress, results, and problems by recording predefined events or user-defined messages for later analysis.</span></span> <span data-ttu-id="aa3f6-105">たとえば、一括挿入の開始時刻と終了時刻を記録しておけば、パッケージ実行時のパフォーマンスの問題を特定できます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-105">For example, you can record when a bulk insert begins and ends to identify performance issues when the package runs.</span></span>  
  
 <span data-ttu-id="aa3f6-106">カスタム ログ エントリとは、パッケージ、すべてのコンテナー、およびタスクに使用できる一連の標準的なログ記録イベントとは異なるエントリのセットです。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-106">The custom log entries are a different set of entries than the set of standard logging events that are available for packages and all containers and tasks.</span></span> <span data-ttu-id="aa3f6-107">カスタム ログ エントリは、パッケージ内の特定のタスクに関する有益な情報を取得するように調整されます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-107">The custom log entries are tailored to capture useful information about a specific task in a package.</span></span> <span data-ttu-id="aa3f6-108">たとえば、SQL 実行タスクのカスタム ログ エントリの 1 つに、そのタスクで実行される SQL ステートメントをログに記録するものがあります。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-108">For example, one of the custom log entries for the Execute SQL task records the SQL statement that the task executes in the log.</span></span>  
  
 <span data-ttu-id="aa3f6-109">すべてのログ エントリには、パッケージの開始時と終了時に自動的に書き込まれるログ エントリなど、日付と時刻に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-109">All log entries include date and time information, including the log entries that are automatically written when a package begins and finishes.</span></span> <span data-ttu-id="aa3f6-110">多くのログ イベントでは、ログに複数のエントリが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-110">Many of the log events write multiple entries to the log.</span></span> <span data-ttu-id="aa3f6-111">通常、イベントにいくつか異なるフェーズが含まれている場合に複数のエントリが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-111">This typically occurs when the event has different phases.</span></span> <span data-ttu-id="aa3f6-112">たとえば、`ExecuteSQLExecutingQuery` ログ イベントでは、3 つのエントリが書き込まれます。1 つ目はタスクがデータベースへの接続を取得した後、2 つ目は SQL ステートメントの準備が開始された後、3 つ目は SQL ステートメントの実行が完了した後に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-112">For example, the `ExecuteSQLExecutingQuery` log event writes three entries: one entry after the task acquires a connection to the database, another after the task starts to prepare the SQL statement, and one more after the execution of the SQL statement is completed.</span></span>  
  
 <span data-ttu-id="aa3f6-113">次の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクトには、カスタム ログ エントリがあります。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-113">The following [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects have custom log entries:</span></span>  
  
 [<span data-ttu-id="aa3f6-114">Package</span><span class="sxs-lookup"><span data-stu-id="aa3f6-114">Package</span></span>](#Package)  
  
 [<span data-ttu-id="aa3f6-115">一括挿入タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-115">Bulk Insert Task</span></span>](#BulkInsert)  
  
 [<span data-ttu-id="aa3f6-116">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-116">Data Flow Task</span></span>](#DataFlow)  
  
 [<span data-ttu-id="aa3f6-117">DTS 2000 実行タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-117">Execute DTS 2000 Task</span></span>](#ExecuteDTS200)  
  
 [<span data-ttu-id="aa3f6-118">プロセス実行タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-118">Execute Process Task</span></span>](#ExecuteProcess)  
  
 [<span data-ttu-id="aa3f6-119">SQL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-119">Execute SQL Task</span></span>](#ExecuteSQL)  
  
 [<span data-ttu-id="aa3f6-120">ファイル システム タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-120">File System Task</span></span>](#FileSystem)  
  
 [<span data-ttu-id="aa3f6-121">FTP タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-121">FTP Task</span></span>](#FTP)  
  
 [<span data-ttu-id="aa3f6-122">メッセージ キュー タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-122">Message Queue Task</span></span>](#MessageQueue)  
  
 [<span data-ttu-id="aa3f6-123">スクリプト タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-123">Script Task</span></span>](#Script)  
  
 [<span data-ttu-id="aa3f6-124">メール送信タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-124">Send Mail Task</span></span>](#SendMail)  
  
 [<span data-ttu-id="aa3f6-125">データベース転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-125">Transfer Database Task</span></span>](#TransferDatabase)  
  
 [<span data-ttu-id="aa3f6-126">エラー メッセージ転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-126">Transfer Error Messages Task</span></span>](#TransferErrorMessages)  
  
 [<span data-ttu-id="aa3f6-127">ジョブ転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-127">Transfer Jobs Task</span></span>](#TransferJobs)  
  
 [<span data-ttu-id="aa3f6-128">ログイン転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-128">Transfer Logins Task</span></span>](#TransferLogins)  
  
 [<span data-ttu-id="aa3f6-129">Master ストアド プロシージャ転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-129">Transfer Master Stored Procedures Task</span></span>](#TransferMasterStoredProcedures)  
  
 [<span data-ttu-id="aa3f6-130">SQL Server オブジェクトの転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-130">Transfer SQL Server Objects Task</span></span>](#TransferSQLServerObjects)  
  
 [<span data-ttu-id="aa3f6-131">Web サービス タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-131">Web Services Task</span></span>](#WebServices)  
  
 [<span data-ttu-id="aa3f6-132">WMI データ リーダー タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-132">WMI Data Reader Task</span></span>](#WMIDataReader)  
  
 [<span data-ttu-id="aa3f6-133">WMI イベント監視タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-133">WMI Event Watcher Task</span></span>](#WMIEventWatcher)  
  
 [<span data-ttu-id="aa3f6-134">XML タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-134">XML Task</span></span>](#XML)  
  
## <a name="log-entries"></a><span data-ttu-id="aa3f6-135">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-135">Log Entries</span></span>  
  
###  <a name="package"></a><a name="Package"></a> <span data-ttu-id="aa3f6-136">[パッケージ]</span><span class="sxs-lookup"><span data-stu-id="aa3f6-136">Package</span></span>  
 <span data-ttu-id="aa3f6-137">次の表は、パッケージのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-137">The following table lists the custom log entries for packages.</span></span>  
  
|<span data-ttu-id="aa3f6-138">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-138">Log entry</span></span>|<span data-ttu-id="aa3f6-139">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-139">Description</span></span>|  
|---------------|-----------------|  
|`PackageStart`|<span data-ttu-id="aa3f6-140">パッケージの実行が開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-140">Indicates that the package began to run.</span></span><br /><br /> <span data-ttu-id="aa3f6-141">注: このログ エントリは自動的にログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-141">Note: This log entry is automatically written to the log.</span></span> <span data-ttu-id="aa3f6-142">除外することはできません。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-142">You cannot exclude it.</span></span>|  
|`PackageEnd`|<span data-ttu-id="aa3f6-143">パッケージが完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-143">Indicates that the package completed.</span></span><br /><br /> <span data-ttu-id="aa3f6-144">注: このログ エントリは自動的にログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-144">Note: This log entry is automatically written to the log.</span></span> <span data-ttu-id="aa3f6-145">除外することはできません。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-145">You cannot exclude it.</span></span>|  
|`Diagnostic`|<span data-ttu-id="aa3f6-146">同時実行できる実行可能ファイル数など、パッケージの実行に影響するシステム構成に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-146">Provides information about the system configuration that affects package execution such as the number executables that can be run concurrently.</span></span><br /><br /> <span data-ttu-id="aa3f6-147">`Diagnostic` ログ エントリに、外部データ プロバイダーの呼び出し前後のエントリも含まれています。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-147">The `Diagnostic` log entry also includes before and after entries for calls to external data providers.</span></span> <span data-ttu-id="aa3f6-148">詳細については、「 [トラブルシューティング ツールのパッケージ接続](troubleshooting/troubleshooting-tools-for-package-connectivity.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-148">For more information, see [Troubleshooting Tools Package Connectivity](troubleshooting/troubleshooting-tools-for-package-connectivity.md).</span></span>|  
  
###  <a name="bulk-insert-task"></a><a name="BulkInsert"></a> <span data-ttu-id="aa3f6-149">一括挿入タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-149">Bulk Insert Task</span></span>  
 <span data-ttu-id="aa3f6-150">次の表は、一括挿入タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-150">The following table lists the custom log entries for the Bulk Insert task.</span></span>  
  
|<span data-ttu-id="aa3f6-151">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-151">Log entry</span></span>|<span data-ttu-id="aa3f6-152">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-152">Description</span></span>|  
|---------------|-----------------|  
|`DTSBulkInsertTaskBegin`|<span data-ttu-id="aa3f6-153">一括挿入が開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-153">Indicates that the bulk insert began.</span></span>|  
|`DTSBulkInsertTaskEnd`|<span data-ttu-id="aa3f6-154">一括挿入が終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-154">Indicates that the bulk insert finished.</span></span>|  
|`DTSBulkInsertTaskInfos`|<span data-ttu-id="aa3f6-155">タスクに関する説明情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-155">Provides descriptive information about the task.</span></span>|  
  
###  <a name="data-flow-task"></a><a name="DataFlow"></a> <span data-ttu-id="aa3f6-156">Data Flow Task</span><span class="sxs-lookup"><span data-stu-id="aa3f6-156">Data Flow Task</span></span>  
 <span data-ttu-id="aa3f6-157">次の表は、データ フロー タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-157">The following table lists the custom log entries for the Data Flow task.</span></span>  
  
|<span data-ttu-id="aa3f6-158">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-158">Log entry</span></span>|<span data-ttu-id="aa3f6-159">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-159">Description</span></span>|  
|---------------|-----------------|  
|`BufferSizeTuning`|<span data-ttu-id="aa3f6-160">データ フロー タスクでバッファーのサイズが変更されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-160">Indicates that the Data Flow task changed the size of the buffer.</span></span> <span data-ttu-id="aa3f6-161">このログ エントリはサイズ変更の理由を説明し、一時的な新しいバッファー サイズを表示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-161">The log entry describes the reasons for the size change and lists the temporary new buffer size.</span></span>|  
|`OnPipelinePostEndOfRowset`|<span data-ttu-id="aa3f6-162">`ProcessInput` メソッドの最終呼び出しで設定される、行セットの終了シグナルがコンポーネントに通知されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-162">Denotes that a component has been given its end-of-rowset signal, which is set by the last call of the `ProcessInput` method.</span></span> <span data-ttu-id="aa3f6-163">エントリは、データ フロー内で入力を処理するコンポーネントごとに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-163">An entry is written for each component in the data flow that processes input.</span></span> <span data-ttu-id="aa3f6-164">このエントリには、コンポーネント名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-164">The entry includes the name of the component.</span></span>|  
|`OnPipelinePostPrimeOutput`|<span data-ttu-id="aa3f6-165">コンポーネントが `PrimeOutput` メソッドの最終呼び出しを完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-165">Indicates that the component has completed its last call to the `PrimeOutput` method.</span></span> <span data-ttu-id="aa3f6-166">データ フローによっては、複数のログ エントリが書き込まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-166">Depending on the data flow, multiple log entries may be written.</span></span> <span data-ttu-id="aa3f6-167">コンポーネントがソースの場合、コンポーネントが行の処理を完了したことを意味します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-167">If the component is a source, this means that the component has finished processing rows.</span></span>|  
|`OnPipelinePreEndOfRowset`|<span data-ttu-id="aa3f6-168">コンポーネントが最後にメソッドを呼び出したときに設定された行セットの最後のシグナルを受信しようとしていることを示し `ProcessInput` ます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-168">Indicates that a component is about to receive its end-of-rowset signal, which is set by the last call of the `ProcessInput` method.</span></span> <span data-ttu-id="aa3f6-169">エントリは、データ フロー内で入力を処理するコンポーネントごとに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-169">An entry is written for each component in the data flow that processes input.</span></span> <span data-ttu-id="aa3f6-170">このエントリには、コンポーネント名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-170">The entry includes the name of the component.</span></span>|  
|`OnPipelinePrePrimeOutput`|<span data-ttu-id="aa3f6-171">コンポーネントに、`PrimeOutput` メソッドからの呼び出しが通知されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-171">Indicates that the component is about to receive its call from the `PrimeOutput` method.</span></span> <span data-ttu-id="aa3f6-172">データ フローによっては、複数のログ エントリが書き込まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-172">Depending on the data flow, multiple log entries may be written.</span></span>|  
|`OnPipelineRowsSent`|<span data-ttu-id="aa3f6-173">`ProcessInput` メソッドの呼び出しによってコンポーネント入力に指定された行数を報告します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-173">Reports the number of rows provided to a component input by a call to the `ProcessInput` method.</span></span> <span data-ttu-id="aa3f6-174">ログ エントリにはコンポーネント名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-174">The log entry includes the component name.</span></span>|  
|`PipelineBufferLeak`|<span data-ttu-id="aa3f6-175">バッファー マネージャーの終了後もバッファーを保持しているコンポーネントに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-175">Provides information about any component that kept buffers alive after the buffer manager goes away.</span></span> <span data-ttu-id="aa3f6-176">つまり、バッファー リソースが解放されていないため、メモリ リークの原因になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-176">This means that buffers resources were not released and may cause memory leaks.</span></span> <span data-ttu-id="aa3f6-177">このログ エントリは、コンポーネントの名前とバッファーの ID を含みます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-177">The log entry provides the name of the component and the ID of the buffer.</span></span>|  
|`PipelineExecutionPlan`|<span data-ttu-id="aa3f6-178">データ フローの実行プランを報告します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-178">Reports the execution plan of the data flow.</span></span> <span data-ttu-id="aa3f6-179">バッファーをコンポーネントに送信する方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-179">It provides information about how buffers will be sent to components.</span></span> <span data-ttu-id="aa3f6-180">この情報は、PipelineExecutionTrees エントリと組み合わせて、タスク内での実行内容を示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-180">This information, in combination with the PipelineExecutionTrees entry, describes what is occurring in the task.</span></span>|  
|`PipelineExecutionTrees`|<span data-ttu-id="aa3f6-181">データ フロー内のレイアウトの実行ツリーを報告します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-181">Reports the execution trees of the layout in the data flow.</span></span> <span data-ttu-id="aa3f6-182">データ フロー エンジンのスケジューラは、このツリーを使用して、データ フローの実行プランを構築します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-182">The scheduler of the data flow engine use the trees to build the execution plan of the data flow.</span></span>|  
|`PipelineInitialization`|<span data-ttu-id="aa3f6-183">タスクに関する初期化情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-183">Provides initialization information about the task.</span></span> <span data-ttu-id="aa3f6-184">この情報には、BLOB データの一時的な保存に使用するディレクトリ、既定のバッファー サイズ、およびバッファー内の行数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-184">This information includes the directories to use for temporary storage of BLOB data, the default buffer size, and the number of rows in a buffer.</span></span> <span data-ttu-id="aa3f6-185">データ フロー タスクの構成によっては、複数のログ エントリが書き込まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-185">Depending on the configuration of the Data Flow task, multiple log entries may be written.</span></span>|  
  
###  <a name="execute-dts-2000-task"></a><a name="ExecuteDTS200"></a> <span data-ttu-id="aa3f6-186">DTS 2000 実行タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-186">Execute DTS 2000 Task</span></span>  
 <span data-ttu-id="aa3f6-187">次の表は、DTS 2000 実行タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-187">The following table lists the custom log entries for the Execute DTS 2000 task.</span></span>  
  
|<span data-ttu-id="aa3f6-188">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-188">Log entry</span></span>|<span data-ttu-id="aa3f6-189">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-189">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteDTS80PackageTaskBegin`|<span data-ttu-id="aa3f6-190">タスクが DTS 2000 パッケージの実行を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-190">Indicates that the task began to run a DTS 2000 package.</span></span>|  
|`ExecuteDTS80PackageTaskEnd`|<span data-ttu-id="aa3f6-191">タスクが終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-191">Indicates that the task finished.</span></span><br /><br /> <span data-ttu-id="aa3f6-192">注: DTS 2000 パッケージは、タスク終了後も引き続き実行される場合があります。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-192">Note: The DTS 2000 package may continue to run after the task ends.</span></span>|  
|`ExecuteDTS80PackageTaskTaskInfo`|<span data-ttu-id="aa3f6-193">タスクに関する説明情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-193">Provides descriptive information about the task.</span></span>|  
|`ExecuteDTS80PackageTaskTaskResult`|<span data-ttu-id="aa3f6-194">タスクで実行された DTS 2000 パッケージの実行結果を報告します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-194">Reports the execution result of the DTS 2000 package that the task ran.</span></span>|  
  
###  <a name="execute-process-task"></a><a name="ExecuteProcess"></a> <span data-ttu-id="aa3f6-195">プロセス実行タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-195">Execute Process Task</span></span>  
 <span data-ttu-id="aa3f6-196">次の表は、プロセス実行タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-196">The following table lists the custom log entries for the Execute Process task.</span></span>  
  
|<span data-ttu-id="aa3f6-197">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-197">Log entry</span></span>|<span data-ttu-id="aa3f6-198">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-198">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|<span data-ttu-id="aa3f6-199">タスクで実行するように構成されている実行可能ファイルの実行プロセスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-199">Provides information about the process of running the executable that the task is configured to run.</span></span><br /><br /> <span data-ttu-id="aa3f6-200">2 つのログ エントリが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-200">Two log entries are written.</span></span> <span data-ttu-id="aa3f6-201">1 つのエントリには、タスクで実行される実行可能ファイルの名前と場所が含まれ、もう 1 つのエントリは、実行可能ファイルの終了を記録します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-201">One contains information about the name and location of the executable that the task runs, and the other records the exit from the executable.</span></span>|  
|`ExecuteProcessVariableRouting`|<span data-ttu-id="aa3f6-202">実行可能ファイルの入力と出力にルーティングされる変数に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-202">Provides information about which variables are routed to the input and outputs of the executable.</span></span> <span data-ttu-id="aa3f6-203">ログ エントリは、stdin (入力)、stdout (出力)、および stderr (エラー出力) に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-203">Log entries are written for stdin (the input), stdout (the output), and stderr (the error output).</span></span>|  
  
###  <a name="execute-sql-task"></a><a name="ExecuteSQL"></a> <span data-ttu-id="aa3f6-204">SQL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-204">Execute SQL Task</span></span>  
 <span data-ttu-id="aa3f6-205">次の表では、SQL 実行タスクのカスタム ログ エントリを説明します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-205">The following table describes the custom log entry for the Execute SQL task.</span></span>  
  
|<span data-ttu-id="aa3f6-206">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-206">Log entry</span></span>|<span data-ttu-id="aa3f6-207">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-207">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|<span data-ttu-id="aa3f6-208">SQL ステートメントの実行フェーズに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-208">Provides information about the execution phases of the SQL statement.</span></span> <span data-ttu-id="aa3f6-209">タスクがデータベースへの接続を取得したとき、SQL ステートメントの準備が開始されたとき、および SQL ステートメントの実行が完了した後に、ログ エントリが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-209">Log entries are written when the task acquires connection to the database, when the task starts to prepare the SQL statement, and after the execution of the SQL statement is completed.</span></span> <span data-ttu-id="aa3f6-210">準備フェーズのログ エントリには、タスクで使用される SQL ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-210">The log entry for the prepare phase includes the SQL statement that the task uses.</span></span>|  
  
###  <a name="file-system-task"></a><a name="FileSystem"></a> <span data-ttu-id="aa3f6-211">ファイル システム タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-211">File System Task</span></span>  
 <span data-ttu-id="aa3f6-212">次の表では、ファイル システム タスクのカスタム ログ エントリを説明します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-212">The following table describes the custom log entry for the File System task.</span></span>  
  
|<span data-ttu-id="aa3f6-213">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-213">Log entry</span></span>|<span data-ttu-id="aa3f6-214">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-214">Description</span></span>|  
|---------------|-----------------|  
|`FileSystemOperation`|<span data-ttu-id="aa3f6-215">タスクで実行される操作を報告します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-215">Reports the operation that the task performs.</span></span> <span data-ttu-id="aa3f6-216">ログ エントリは、ファイル システム操作の開始時に書き込まれます。これには、操作の基になるファイルと操作対象のファイルに関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-216">The log entry is written when the file system operation starts and includes information about the source and destination.</span></span>|  
  
###  <a name="ftp-task"></a><a name="FTP"></a> <span data-ttu-id="aa3f6-217">FTP タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-217">FTP Task</span></span>  
 <span data-ttu-id="aa3f6-218">次の表は、FTP タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-218">The following table lists the custom log entries for the FTP task.</span></span>  
  
|<span data-ttu-id="aa3f6-219">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-219">Log entry</span></span>|<span data-ttu-id="aa3f6-220">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-220">Description</span></span>|  
|---------------|-----------------|  
|`FTPConnectingToServer`|<span data-ttu-id="aa3f6-221">タスクで FTP サーバーへの接続が開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-221">Indicates that the task initiated a connection to the FTP server.</span></span>|  
|`FTPOperation`|<span data-ttu-id="aa3f6-222">タスクで実行された FTP 操作の開始および種類を報告します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-222">Reports the beginning of and the type of FTP operation that the task performs.</span></span>|  
  
###  <a name="message-queue-task"></a><a name="MessageQueue"></a> <span data-ttu-id="aa3f6-223">メッセージ キュー タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-223">Message Queue Task</span></span>  
 <span data-ttu-id="aa3f6-224">次の表は、メッセージ キュー タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-224">The following table lists the custom log entries for the Message Queue task.</span></span>  
  
|<span data-ttu-id="aa3f6-225">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-225">Log entry</span></span>|<span data-ttu-id="aa3f6-226">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-226">Description</span></span>|  
|---------------|-----------------|  
|`MSMQAfterOpen`|<span data-ttu-id="aa3f6-227">タスクで開いていたメッセージ キューを終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-227">Indicates that the task finished opening the message queue.</span></span>|  
|`MSMQBeforeOpen`|<span data-ttu-id="aa3f6-228">タスクがメッセージ キューを開く操作を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-228">Indicates that the task began to open the message queue.</span></span>|  
|`MSMQBeginReceive`|<span data-ttu-id="aa3f6-229">タスクがメッセージの受信を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-229">Indicates that the task began to receive a message.</span></span>|  
|`MSMQBeginSend`|<span data-ttu-id="aa3f6-230">タスクがメッセージの送信を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-230">Indicates that the task began to send a message.</span></span>|  
|`MSMQEndReceive`|<span data-ttu-id="aa3f6-231">タスクがメッセージの受信を終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-231">Indicates that the task finished receiving a message.</span></span>|  
|`MSMQEndSend`|<span data-ttu-id="aa3f6-232">タスクがメッセージの送信を終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-232">Indicates that the task finished sending a message</span></span>|  
|`MSMQTaskInfo`|<span data-ttu-id="aa3f6-233">タスクに関する説明情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-233">Provides descriptive information about the task.</span></span>|  
|`MSMQTaskTimeOut`|<span data-ttu-id="aa3f6-234">タスクがタイムアウトしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-234">Indicates that the task timed out.</span></span>|  
  
###  <a name="script-task"></a><a name="Script"></a> <span data-ttu-id="aa3f6-235">スクリプト タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-235">Script Task</span></span>  
 <span data-ttu-id="aa3f6-236">次の表では、スクリプト タスクのカスタム ログ エントリを説明します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-236">The following table describes the custom log entry for the Script task.</span></span>  
  
|<span data-ttu-id="aa3f6-237">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-237">Log entry</span></span>|<span data-ttu-id="aa3f6-238">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-238">Description</span></span>|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|<span data-ttu-id="aa3f6-239">スクリプト内でのログ記録の実装結果を報告します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-239">Reports the results of implementing logging in the script.</span></span> <span data-ttu-id="aa3f6-240">ログ エントリは、`Log` オブジェクトの `Dts` メソッドを呼び出すたびに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-240">A log entry is written for each call to the `Log` method of the `Dts` object.</span></span> <span data-ttu-id="aa3f6-241">このエントリは、コードの実行時に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-241">The entry is written when the code is run.</span></span> <span data-ttu-id="aa3f6-242">詳細については、「 [スクリプト タスクでのログ記録](extending-packages-scripting/task/logging-in-the-script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-242">For more information, see [Logging in the Script Task](extending-packages-scripting/task/logging-in-the-script-task.md).</span></span>|  
  
###  <a name="send-mail-task"></a><a name="SendMail"></a> <span data-ttu-id="aa3f6-243">メール送信タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-243">Send Mail Task</span></span>  
 <span data-ttu-id="aa3f6-244">次の表は、メール送信タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-244">The following table lists the custom log entries for the Send Mail task.</span></span>  
  
|<span data-ttu-id="aa3f6-245">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-245">Log entry</span></span>|<span data-ttu-id="aa3f6-246">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-246">Description</span></span>|  
|---------------|-----------------|  
|`SendMailTaskBegin`|<span data-ttu-id="aa3f6-247">タスクが電子メール メッセージの送信を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-247">Indicates that the task began to send an e-mail message.</span></span>|  
|`SendMailTaskEnd`|<span data-ttu-id="aa3f6-248">タスクが電子メール メッセージの送信を終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-248">Indicates that the task finished sending an e-mail message.</span></span>|  
|`SendMailTaskInfo`|<span data-ttu-id="aa3f6-249">タスクに関する説明情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-249">Provides descriptive information about the task.</span></span>|  
  
###  <a name="transfer-database-task"></a><a name="TransferDatabase"></a> <span data-ttu-id="aa3f6-250">データベース転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-250">Transfer Database Task</span></span>  
 <span data-ttu-id="aa3f6-251">次の表は、データベース転送タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-251">The following table lists the custom log entries for the Transfer Database task.</span></span>  
  
|<span data-ttu-id="aa3f6-252">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-252">Log entry</span></span>|<span data-ttu-id="aa3f6-253">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-253">Description</span></span>|  
|---------------|-----------------|  
|`SourceDB`|<span data-ttu-id="aa3f6-254">タスクでコピーされたデータベースを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-254">Specifies the database that the task copied.</span></span>|  
|`SourceSQLServer`|<span data-ttu-id="aa3f6-255">データベースのコピー元のコンピューターを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-255">Specifies the computer from which the database was copied.</span></span>|  
  
###  <a name="transfer-error-messages-task"></a><a name="TransferErrorMessages"></a> <span data-ttu-id="aa3f6-256">エラー メッセージ転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-256">Transfer Error Messages Task</span></span>  
 <span data-ttu-id="aa3f6-257">次の表は、エラー メッセージ転送タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-257">The following table lists the custom log entries for the Transfer Error Messages task.</span></span>  
  
|<span data-ttu-id="aa3f6-258">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-258">Log entry</span></span>|<span data-ttu-id="aa3f6-259">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-259">Description</span></span>|  
|---------------|-----------------|  
|`TransferErrorMessagesTaskFinishedTransferringObjects`|<span data-ttu-id="aa3f6-260">タスクがエラー メッセージの転送を終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-260">Indicates that the task finished transferring error messages.</span></span>|  
|`TransferErrorMessagesTaskStartTransferringObjects`|<span data-ttu-id="aa3f6-261">タスクがエラー メッセージの転送を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-261">Indicates that the task started to transfer error messages.</span></span>|  
  
###  <a name="transfer-jobs-task"></a><a name="TransferJobs"></a> <span data-ttu-id="aa3f6-262">ジョブ転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-262">Transfer Jobs Task</span></span>  
 <span data-ttu-id="aa3f6-263">次の表は、ジョブ転送タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-263">The following table lists the custom log entries for the Transfer Jobs task.</span></span>  
  
|<span data-ttu-id="aa3f6-264">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-264">Log entry</span></span>|<span data-ttu-id="aa3f6-265">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-265">Description</span></span>|  
|---------------|-----------------|  
|`TransferJobsTaskFinishedTransferringObjects`|<span data-ttu-id="aa3f6-266">タスクが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ジョブの転送を終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-266">Indicates that the task finished transferring [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
|`TransferJobsTaskStartTransferringObjects`|<span data-ttu-id="aa3f6-267">タスクが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ジョブの転送を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-267">Indicates that the task started to transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs.</span></span>|  
  
###  <a name="transfer-logins-task"></a><a name="TransferLogins"></a> <span data-ttu-id="aa3f6-268">ログイン転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-268">Transfer Logins Task</span></span>  
 <span data-ttu-id="aa3f6-269">次の表は、ログイン転送タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-269">The following table lists the custom log entries for the Transfer Logins task.</span></span>  
  
|<span data-ttu-id="aa3f6-270">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-270">Log entry</span></span>|<span data-ttu-id="aa3f6-271">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-271">Description</span></span>|  
|---------------|-----------------|  
|`TransferLoginsTaskFinishedTransferringObjects`|<span data-ttu-id="aa3f6-272">タスクがログインの転送を終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-272">Indicates that the task finished transferring logins.</span></span>|  
|`TransferLoginsTaskStartTransferringObjects`|<span data-ttu-id="aa3f6-273">タスクがログインの転送を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-273">Indicates that the task started to transfer logins.</span></span>|  
  
###  <a name="transfer-master-stored-procedures-task"></a><a name="TransferMasterStoredProcedures"></a> <span data-ttu-id="aa3f6-274">Master ストアド プロシージャ転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-274">Transfer Master Stored Procedures Task</span></span>  
 <span data-ttu-id="aa3f6-275">次の表は、Master ストアド プロシージャ転送タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-275">The following table lists the custom log entries for the Transfer Master Stored Procedures task.</span></span>  
  
|<span data-ttu-id="aa3f6-276">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-276">Log entry</span></span>|<span data-ttu-id="aa3f6-277">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-277">Description</span></span>|  
|---------------|-----------------|  
|`TransferStoredProceduresTaskFinishedTransferringObjects`|<span data-ttu-id="aa3f6-278">**master** データベースに格納されている、ユーザー定義ストアド プロシージャの転送をタスクが完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-278">Indicates that the task finished transferring user-defined stored procedures that are stored in the **master** database.</span></span>|  
|`TransferStoredProceduresTaskStartTransferringObjects`|<span data-ttu-id="aa3f6-279">**master** データベースに格納されている、ユーザー定義ストアド プロシージャの転送をタスクが開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-279">Indicates that the task started to transfer user-defined stored procedures that are stored in the **master** database.</span></span>|  
  
###  <a name="transfer-sql-server-objects-task"></a><a name="TransferSQLServerObjects"></a> <span data-ttu-id="aa3f6-280">SQL Server オブジェクトの転送タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-280">Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="aa3f6-281">次の表は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの転送タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-281">The following table lists the custom log entries for the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task.</span></span>  
  
|<span data-ttu-id="aa3f6-282">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-282">Log entry</span></span>|<span data-ttu-id="aa3f6-283">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-283">Description</span></span>|  
|---------------|-----------------|  
|`TransferSqlServerObjectsTaskFinishedTransferringObjects`|<span data-ttu-id="aa3f6-284">タスクが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース オブジェクトの転送を終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-284">Indicates that the task finished transferring [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database objects.</span></span>|  
|`TransferSqlServerObjectsTaskStartTransferringObjects`|<span data-ttu-id="aa3f6-285">タスクが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベース オブジェクトの転送を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-285">Indicates that the task started to transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database objects.</span></span>|  
  
###  <a name="web-services-task"></a><a name="WebServices"></a> <span data-ttu-id="aa3f6-286">Web サービス タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-286">Web Services Task</span></span>  
 <span data-ttu-id="aa3f6-287">次の表は、Web サービス タスクに対して有効にできるカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-287">The following table lists the custom log entries that you can enable for the Web Services task.</span></span>  
  
|<span data-ttu-id="aa3f6-288">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-288">Log entry</span></span>|<span data-ttu-id="aa3f6-289">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-289">Description</span></span>|  
|---------------|-----------------|  
|`WSTaskBegin`|<span data-ttu-id="aa3f6-290">タスクが Web サービスへのアクセスを開始しました。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-290">The task began to access a Web service.</span></span>|  
|`WSTaskEnd`|<span data-ttu-id="aa3f6-291">タスクが Web サービス メソッドを完了しました。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-291">The task completed a Web service method.</span></span>|  
|`WSTaskInfo`|<span data-ttu-id="aa3f6-292">タスクに関する説明情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-292">Descriptive information about the task.</span></span>|  
  
###  <a name="wmi-data-reader-task"></a><a name="WMIDataReader"></a> <span data-ttu-id="aa3f6-293">WMI データ リーダー タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-293">WMI Data Reader Task</span></span>  
 <span data-ttu-id="aa3f6-294">次の表は、WMI データ リーダー タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-294">The following table lists the custom log entries for the WMI Data Reader task.</span></span>  
  
|<span data-ttu-id="aa3f6-295">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-295">Log entry</span></span>|<span data-ttu-id="aa3f6-296">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-296">Description</span></span>|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|<span data-ttu-id="aa3f6-297">タスクが WMI データの読み取りを開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-297">Indicates that the task began to read WMI data.</span></span>|  
|`WMIDataReaderOperation`|<span data-ttu-id="aa3f6-298">タスクで実行された WQL クエリを報告します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-298">Reports the WQL query that the task ran.</span></span>|  
  
###  <a name="wmi-event-watcher-task"></a><a name="WMIEventWatcher"></a> <span data-ttu-id="aa3f6-299">WMI イベント監視タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-299">WMI Event Watcher Task</span></span>  
 <span data-ttu-id="aa3f6-300">次の表は、WMI イベント監視タスクのカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-300">The following table lists the custom log entries for the WMI Event Watcher task.</span></span>  
  
|<span data-ttu-id="aa3f6-301">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-301">Log entry</span></span>|<span data-ttu-id="aa3f6-302">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-302">Description</span></span>|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|<span data-ttu-id="aa3f6-303">タスクが監視しているイベントが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-303">Denotes that the event occurred that the task was monitoring.</span></span>|  
|`WMIEventWatcherTimedout`|<span data-ttu-id="aa3f6-304">タスクがタイムアウトしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-304">Indicates that the task timed out.</span></span>|  
|`WMIEventWatcherWatchingForWMIEvents`|<span data-ttu-id="aa3f6-305">タスクが WQL クエリの実行を開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-305">Indicates that the task began to execute the WQL query.</span></span> <span data-ttu-id="aa3f6-306">このエントリには、クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-306">The entry includes the query.</span></span>|  
  
###  <a name="xml-task"></a><a name="XML"></a> <span data-ttu-id="aa3f6-307">XML タスク</span><span class="sxs-lookup"><span data-stu-id="aa3f6-307">XML Task</span></span>  
 <span data-ttu-id="aa3f6-308">次の表では、XML タスクのカスタム ログ エントリを説明します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-308">The following table describes the custom log entry for the XML task.</span></span>  
  
|<span data-ttu-id="aa3f6-309">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="aa3f6-309">Log entry</span></span>|<span data-ttu-id="aa3f6-310">説明</span><span class="sxs-lookup"><span data-stu-id="aa3f6-310">Description</span></span>|  
|---------------|-----------------|  
|`XMLOperation`|<span data-ttu-id="aa3f6-311">タスクで実行される操作に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa3f6-311">Provides information about the operation that the task performs</span></span>|   
  
## <a name="see-also"></a><span data-ttu-id="aa3f6-312">参照</span><span class="sxs-lookup"><span data-stu-id="aa3f6-312">See Also</span></span>  
 [<span data-ttu-id="aa3f6-313">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="aa3f6-313">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
