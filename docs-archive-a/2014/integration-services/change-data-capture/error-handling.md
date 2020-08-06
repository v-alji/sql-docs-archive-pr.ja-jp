---
title: エラー処理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ff79e19d-afca-42a4-81b0-62d759380d11
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 083af496c60fb11afaf85068ba980e54986134d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712318"
---
# <a name="error-handling"></a><span data-ttu-id="00c87-102">エラー処理</span><span class="sxs-lookup"><span data-stu-id="00c87-102">Error Handling</span></span>
  <span data-ttu-id="00c87-103">Oracle CDC インスタンスでは、単一の Oracle ソース データベース (Oracle RAC クラスターは単一のデータベースと見なされます) から変更を検出し、対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに含まれる CDC データベースの変更テーブルにコミット済みの変更を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="00c87-103">An Oracle CDC Instance mines changes from a single Oracle source database (an Oracle RAC cluster is considered a single database) and writes the committed changes to change tables in a CDC database in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="00c87-104">CDC インスタンスでは、 **cdc.xdbcdc_state**というシステム テーブルで状態を管理します。</span><span class="sxs-lookup"><span data-stu-id="00c87-104">A CDC Instance maintains its state in a system table called **cdc.xdbcdc_state**.</span></span> <span data-ttu-id="00c87-105">このテーブルをクエリすると、CDC インスタンスの状態をいつでも確認することができます。</span><span class="sxs-lookup"><span data-stu-id="00c87-105">This table can be queried any time to find the state of the CDC Instance.</span></span> <span data-ttu-id="00c87-106">cdc.xdbcdc_state テーブルの詳細については、「 [cdc.xdbcdc_state](the-oracle-cdc-databases.md#bkmk_cdcxdbcdc_state)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="00c87-106">For more information about the cdc.xdbcdc_state table, see [cdc.xdbcdc_state](the-oracle-cdc-databases.md#bkmk_cdcxdbcdc_state).</span></span>  
  
 <span data-ttu-id="00c87-107">次の表は、xdbcdc_state テーブルで示される CDC インスタンスの状態について説明したものです。</span><span class="sxs-lookup"><span data-stu-id="00c87-107">The table below describes the CDC Instance states in the xdbcdc_state table.</span></span>  
  
 <span data-ttu-id="00c87-108">各状態について、cdc.xdbcdc_state テーブル内の対応する列で次の 2 つのことが示されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-108">For each state, the following two indications are shown for the corresponding columns in the cdc.xdbcdc_state table:</span></span>  
  
-   <span data-ttu-id="00c87-109">インスタンスがアクティブでない (Windows プロセスで現在処理されていない) ことを示します。</span><span class="sxs-lookup"><span data-stu-id="00c87-109">Instance is not active (there is no Windows process currently handling it).</span></span> <span data-ttu-id="00c87-110">**[active]** 列の値が 1 の場合は、この Oracle CDC インスタンスを処理する Oracle CDC Service のサブプロセスが実行されています。</span><span class="sxs-lookup"><span data-stu-id="00c87-110">If the **active** column value is 1, a subprocess of the Oracle CDC Service handling this specific Oracle CDC Instance is running.</span></span>  
  
-   <span data-ttu-id="00c87-111">**[error]** 列の値が 0 の場合、Oracle CDC インスタンスがエラー状態ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="00c87-111">If the **error** column value is 0, the Oracle CDC Instance is not in an error condition.</span></span> <span data-ttu-id="00c87-112">**[error]** 列の値が 1 の場合は、エラーが発生しており、Oracle CDC インスタンスで変更を処理できません。</span><span class="sxs-lookup"><span data-stu-id="00c87-112">If the **error** column value is 1, there is an error that prevents the Oracle CDC Instance from processing changes.</span></span>  
  
     <span data-ttu-id="00c87-113">**[error]** 列の値が 1 で、 **[active]** 列の値も 1 の場合は、Oracle CDC インスタンスで回復可能なエラーが発生しています。このエラーは自動的に解決できます。</span><span class="sxs-lookup"><span data-stu-id="00c87-113">If the **error** column has a value of 1 and the **active** column value is also 1, then a recoverable error is occurring for the Oracle CDC Instance, which can be resolved automatically.</span></span> <span data-ttu-id="00c87-114">[error] 列の値が 1 で、[active] 列の値が 0 の場合は、通常、処理を再開する前に手動で問題を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00c87-114">If the error column has a value of 1 and the active column has a value of 0, then in most cases a manual workaround may be needed to resolve the problem before processing can be resumed.</span></span>  
  
 <span data-ttu-id="00c87-115">次の表に、Oracle CDC インスタンスの状態テーブルで報告されるさまざまな状態コードを示します。</span><span class="sxs-lookup"><span data-stu-id="00c87-115">The following table describes the various status codes that the Oracle CDC Instance may report in its state table.</span></span>  
  
|<span data-ttu-id="00c87-116">Status</span><span class="sxs-lookup"><span data-stu-id="00c87-116">Status</span></span>|<span data-ttu-id="00c87-117">Active 状態コード</span><span class="sxs-lookup"><span data-stu-id="00c87-117">Active Status Code</span></span>|<span data-ttu-id="00c87-118">Error 状態コード</span><span class="sxs-lookup"><span data-stu-id="00c87-118">Error Status Code</span></span>|<span data-ttu-id="00c87-119">説明</span><span class="sxs-lookup"><span data-stu-id="00c87-119">Descriptions</span></span>|  
|------------|------------------------|-----------------------|------------------|  
|<span data-ttu-id="00c87-120">ABORTED</span><span class="sxs-lookup"><span data-stu-id="00c87-120">ABORTED</span></span>|<span data-ttu-id="00c87-121">0</span><span class="sxs-lookup"><span data-stu-id="00c87-121">0</span></span>|<span data-ttu-id="00c87-122">1</span><span class="sxs-lookup"><span data-stu-id="00c87-122">1</span></span>|<span data-ttu-id="00c87-123">Oracle CDC インスタンスが実行されていません。</span><span class="sxs-lookup"><span data-stu-id="00c87-123">The Oracle CDC Instance is not running.</span></span> <span data-ttu-id="00c87-124">ABORTED 副状態は、ACTIVE だった Oracle CDC インスタンスが予期せず停止したことを示します。</span><span class="sxs-lookup"><span data-stu-id="00c87-124">The ABORTED substatus indicates that the Oracle CDC Instance was ACTIVE and then has stopped unexpectedly.</span></span><br /><br /> <span data-ttu-id="00c87-125">ABORTED 副状態になるのは、実行されていない Oracle CDC インスタンスの状態が ACTIVE になっていることが Oracle CDC Service のメイン インスタンスで検出された場合です。</span><span class="sxs-lookup"><span data-stu-id="00c87-125">The ABORTED substatus is established by the Oracle CDC Service main instance when it detects that the Oracle CDC Instance is not running while its status is ACTIVE.</span></span>|  
|<span data-ttu-id="00c87-126">ERROR</span><span class="sxs-lookup"><span data-stu-id="00c87-126">ERROR</span></span>|<span data-ttu-id="00c87-127">0</span><span class="sxs-lookup"><span data-stu-id="00c87-127">0</span></span>|<span data-ttu-id="00c87-128">1</span><span class="sxs-lookup"><span data-stu-id="00c87-128">1</span></span>|<span data-ttu-id="00c87-129">Oracle CDC インスタンスが実行されていません。</span><span class="sxs-lookup"><span data-stu-id="00c87-129">The Oracle CDC Instance is not running.</span></span> <span data-ttu-id="00c87-130">ERROR 状態は、回復できないエラーが発生したために ACTIVE だった CDC インスタンスが無効になったことを示します。</span><span class="sxs-lookup"><span data-stu-id="00c87-130">The ERROR status indicates that the CDC instance was ACTIVE but then encountered an error that is not recoverable and disabled itself.</span></span> <span data-ttu-id="00c87-131">ERROR 状態には、次の副状態コードがあります。</span><span class="sxs-lookup"><span data-stu-id="00c87-131">The ERROR status contains the following substatus codes:</span></span><br /><br /> <span data-ttu-id="00c87-132">MISCONFIGURED: 回復できない構成エラーが検出されました。</span><span class="sxs-lookup"><span data-stu-id="00c87-132">MISCONFIGURED: An unrecoverable configuration error was detected.</span></span><br /><br /> <span data-ttu-id="00c87-133">PASSWORD-REQUIRED: Change Data Capture Designer for Oracle by Attunity のパスワードが設定されていないか、構成されているパスワードが無効です。</span><span class="sxs-lookup"><span data-stu-id="00c87-133">PASSWORD-REQUIRED: There is no password set for the Change Data Capture Designer for Oracle by Attunity or the configured password is not valid.</span></span> <span data-ttu-id="00c87-134">サービスの非対称キーのパスワードが変更されたことが原因として考えられます。</span><span class="sxs-lookup"><span data-stu-id="00c87-134">This can be because of a change to the service asymmetric key password.</span></span>|  
|<span data-ttu-id="00c87-135">RUNNING</span><span class="sxs-lookup"><span data-stu-id="00c87-135">RUNNING</span></span>|<span data-ttu-id="00c87-136">1</span><span class="sxs-lookup"><span data-stu-id="00c87-136">1</span></span>|<span data-ttu-id="00c87-137">0</span><span class="sxs-lookup"><span data-stu-id="00c87-137">0</span></span>|<span data-ttu-id="00c87-138">CDC インスタンスが実行されていて、変更レコードが処理されています。</span><span class="sxs-lookup"><span data-stu-id="00c87-138">The CDC instance is running and is processing change records.</span></span> <span data-ttu-id="00c87-139">RUNNING 状態には、次の副状態コードがあります。</span><span class="sxs-lookup"><span data-stu-id="00c87-139">The RUNNING status contains the following substatus codes:</span></span><br /><br /> <span data-ttu-id="00c87-140">IDLE: すべての変更レコードが処理され、対象の制御 ( **_CT**) テーブルに格納されました。</span><span class="sxs-lookup"><span data-stu-id="00c87-140">IDLE: All change records were processed and stored into the target control (**_CT**) tables.</span></span> <span data-ttu-id="00c87-141">制御テーブルにアクティブなトランザクションはありません。</span><span class="sxs-lookup"><span data-stu-id="00c87-141">There is no active transaction with the control tables.</span></span><br /><br /> <span data-ttu-id="00c87-142">PROCESSING: 制御 ( **_CT**) テーブルにまだ書き込まれていない、処理中の変更レコードがあります。</span><span class="sxs-lookup"><span data-stu-id="00c87-142">PROCESSING: There are change records being processed that are not yet written to the control (**_CT**) tables.</span></span>|  
|<span data-ttu-id="00c87-143">STOPPED</span><span class="sxs-lookup"><span data-stu-id="00c87-143">STOPPED</span></span>|<span data-ttu-id="00c87-144">0</span><span class="sxs-lookup"><span data-stu-id="00c87-144">0</span></span>|<span data-ttu-id="00c87-145">0</span><span class="sxs-lookup"><span data-stu-id="00c87-145">0</span></span>|<span data-ttu-id="00c87-146">CDC インスタンスが実行されていません。</span><span class="sxs-lookup"><span data-stu-id="00c87-146">The CDC instance is not running.</span></span> <span data-ttu-id="00c87-147">STOP 副状態は、ACTIVE だった CDC インスタンスが適切に停止されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="00c87-147">The STOP substatus indicates that the CDC instance was ACTIVE and then was stopped correctly.</span></span>|  
|<span data-ttu-id="00c87-148">SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="00c87-148">SUSPENDED</span></span>|<span data-ttu-id="00c87-149">1</span><span class="sxs-lookup"><span data-stu-id="00c87-149">1</span></span>|<span data-ttu-id="00c87-150">1</span><span class="sxs-lookup"><span data-stu-id="00c87-150">1</span></span>|<span data-ttu-id="00c87-151">CDC インスタンスが実行されていますが、回復可能なエラーにより処理が中断されています。</span><span class="sxs-lookup"><span data-stu-id="00c87-151">The CDC instance is running but processing is suspended due to a recoverable error.</span></span> <span data-ttu-id="00c87-152">SUSPENDED 状態には、次の副状態コードがあります。</span><span class="sxs-lookup"><span data-stu-id="00c87-152">The SUSPENDED status contains the following substatus codes:</span></span><br /><br /> <span data-ttu-id="00c87-153">DISCONNECTED: ソース Oracle データベースとの接続を確立できません。</span><span class="sxs-lookup"><span data-stu-id="00c87-153">DISCONNECTED: The connection with the source Oracle database cannot be established.</span></span> <span data-ttu-id="00c87-154">接続が回復すると処理が再開されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-154">Processing will resume once connection is restored.</span></span><br /><br /> <span data-ttu-id="00c87-155">STORAGE: 記憶領域がいっぱいです。</span><span class="sxs-lookup"><span data-stu-id="00c87-155">STORAGE: The storage is full.</span></span> <span data-ttu-id="00c87-156">記憶領域に空きができると処理が再開されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-156">Processing will resume when storage becomes available.</span></span> <span data-ttu-id="00c87-157">この状態は、状態テーブルを更新できないために表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="00c87-157">In some cases, this status may not appear because the status table cannot be updated.</span></span><br /><br /> <span data-ttu-id="00c87-158">LOGGER: ロガーは Oracle に接続されていますが、一時的な問題が発生しており、Oracle トランザクション ログを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="00c87-158">LOGGER: The logger is connected to Oracle but it cannot read the Oracle transaction logs because of a temporary problem.</span></span>|  
|<span data-ttu-id="00c87-159">DATAERROR</span><span class="sxs-lookup"><span data-stu-id="00c87-159">DATAERROR</span></span>|<span data-ttu-id="00c87-160">x</span><span class="sxs-lookup"><span data-stu-id="00c87-160">x</span></span>|<span data-ttu-id="00c87-161">x</span><span class="sxs-lookup"><span data-stu-id="00c87-161">x</span></span>|<span data-ttu-id="00c87-162">この状態コードは、 **xdbcdc_trace** テーブルにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-162">This status code is only used for the **xdbcdc_trace** table.</span></span> <span data-ttu-id="00c87-163">**xdbcdc_state** テーブルには表示されません。</span><span class="sxs-lookup"><span data-stu-id="00c87-163">It does not appear in the **xdbcdc_state** table.</span></span> <span data-ttu-id="00c87-164">この状態のトレース レコードは、Oracle のログ レコードに問題があることを示します。</span><span class="sxs-lookup"><span data-stu-id="00c87-164">Trace records with this status indicate a problem with an Oracle log record.</span></span> <span data-ttu-id="00c87-165">問題があるログ レコードは、 **[data]** 列に BLOB として格納されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-165">The bad log record is stored in the **data** column as a BLOB.</span></span> <span data-ttu-id="00c87-166">DATAERROR 状態には、次の副状態コードがあります。</span><span class="sxs-lookup"><span data-stu-id="00c87-166">The DATAERROR status contains the following substatus codes:</span></span><br /><br /> <span data-ttu-id="00c87-167">BADRECORD: アタッチされたログ レコードを解析できませんでした。</span><span class="sxs-lookup"><span data-stu-id="00c87-167">BADRECORD: The attached log record could not be parsed.</span></span><br /><br /> <span data-ttu-id="00c87-168">CONVERT-ERROR: 一部の列のデータをキャプチャ テーブル内の対象の列に変換できませんでした。</span><span class="sxs-lookup"><span data-stu-id="00c87-168">CONVERT-ERROR: The data in some columns could not be converted to the target columns in the capture table.</span></span> <span data-ttu-id="00c87-169">この状態は、変換エラーについてのトレース レコードを生成するように構成で指定されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-169">This status may appear only if the configuration specifies that conversion errors should produce trace records.</span></span>|  
  
 <span data-ttu-id="00c87-170">Oracle CDC Service の状態は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納されるため、データベース内の状態の値にサービスの実際の状態が反映されていない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="00c87-170">Because the Oracle CDC Service state is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], there may be cases where the state value in the database might not reflect the actual state of the service.</span></span> <span data-ttu-id="00c87-171">最も一般的なシナリオは、サービスと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の間の接続が失われ、なんらかの理由で再開できない場合です。</span><span class="sxs-lookup"><span data-stu-id="00c87-171">The most common scenario is when the service loses its connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and cannot resume it (for any reason).</span></span> <span data-ttu-id="00c87-172">この場合、 **cdc.xdbcdc_state** に最新の状態が格納されなくなります。</span><span class="sxs-lookup"><span data-stu-id="00c87-172">In that case, the state stored in **cdc.xdbcdc_state** becomes stale.</span></span> <span data-ttu-id="00c87-173">最終更新のタイムスタンプ (UTC) から 1 分以上経過していれば、古い状態を示していると考えられます。</span><span class="sxs-lookup"><span data-stu-id="00c87-173">If the last update timestamp (UTC) is more than a minute old, the state is probably stale.</span></span> <span data-ttu-id="00c87-174">この場合は、Windows イベント ビューアーを使用して、サービスの状態に関する詳しい情報を確認してください。</span><span class="sxs-lookup"><span data-stu-id="00c87-174">In this case, use the Windows Event Viewer to find additional information about the status of the service.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="00c87-175">エラー処理</span><span class="sxs-lookup"><span data-stu-id="00c87-175">Error Handling</span></span>  
 <span data-ttu-id="00c87-176">ここでは、Oracle CDC Service でのエラーの処理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="00c87-176">This section describes how the Oracle CDC Service handles errors.</span></span>  
  
### <a name="logging"></a><span data-ttu-id="00c87-177">ログ記録</span><span class="sxs-lookup"><span data-stu-id="00c87-177">Logging</span></span>  
 <span data-ttu-id="00c87-178">Oracle CDC Service では、次のいずれかにエラー情報を出力します。</span><span class="sxs-lookup"><span data-stu-id="00c87-178">The Oracle CDC Service creates error information in one of the following places.</span></span>  
  
-   <span data-ttu-id="00c87-179">Windows イベント ログ。エラーのログ記録で、Oracle CDC Service のライフ サイクル イベント (開始、停止、対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続や再接続) を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-179">The Windows event log, which is used with logging errors and to indicate Oracle CDC Service life cycle events (starting, stopping, (re)connection to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance).</span></span>  
  
-   <span data-ttu-id="00c87-180">MSXDBCDC.dbo.xdbcdc_trace テーブル。Oracle CDC Service のメイン プロセスで、一般的なログ記録とトレースに使用されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-180">The MSXDBCDC.dbo.xdbcdc_trace table, which is used for general logging and tracing by the Oracle CDC Service main process.</span></span>  
  
-   <span data-ttu-id="00c87-181">\<cdc-database>.cdc.xdbcdc_trace テーブル。Oracle CDC インスタンスで、一般的なログ記録とトレースに使用されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-181">The \<cdc-database>.cdc.xdbcdc_trace table, which is used for general logging and tracing by Oracle CDC Instances.</span></span> <span data-ttu-id="00c87-182">つまり、特定の Oracle CDC インスタンスに関連するエラーは、そのインスタンスのトレース テーブルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-182">This means that errors related to a specific Oracle CDC Instance are logged to that instance's trace table.</span></span>  
  
 <span data-ttu-id="00c87-183">Oracle CDC Service で情報が記録される状況は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="00c87-183">Information is logged by the Oracle CDC service when the service:</span></span>  
  
-   <span data-ttu-id="00c87-184">サービス コントロール マネージャーによって開始または停止された。</span><span class="sxs-lookup"><span data-stu-id="00c87-184">Is started or stopped by the service control manager.</span></span>  
  
-   <span data-ttu-id="00c87-185">関連付けられている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続できない (エラーの発生後に接続が正常に確立された場合も含む)。</span><span class="sxs-lookup"><span data-stu-id="00c87-185">Cannot connect to the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and when it successfully establishes a connection following a failure.</span></span>  
  
-   <span data-ttu-id="00c87-186">Oracle CDC Service インスタンスの起動時にエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="00c87-186">Encounters an error starting Oracle CDC Service instances.</span></span>  
  
-   <span data-ttu-id="00c87-187">Oracle CDC インスタンスが中止されたことが検出された。</span><span class="sxs-lookup"><span data-stu-id="00c87-187">Detects that an Oracle CDC Instance has aborted.</span></span>  
  
-   <span data-ttu-id="00c87-188">予期しないエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="00c87-188">Encounters an unexpected error.</span></span>  
  
 <span data-ttu-id="00c87-189">CDC インスタンスで情報が記録される状況は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="00c87-189">Information is logged by the CDC instance when the instance:</span></span>  
  
-   <span data-ttu-id="00c87-190">有効または無効になった。</span><span class="sxs-lookup"><span data-stu-id="00c87-190">Is enabled or disabled.</span></span>  
  
-   <span data-ttu-id="00c87-191">エラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="00c87-191">Encounters an error.</span></span>  
  
-   <span data-ttu-id="00c87-192">回復可能なエラーから回復した。</span><span class="sxs-lookup"><span data-stu-id="00c87-192">Recovers from a recoverable error.</span></span>  
  
 <span data-ttu-id="00c87-193">さらに、トレース テーブルを使用して、トラブルシューティングのための詳細なトレース情報が記録されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-193">The trace table is also used for recording detailed trace information for troubleshooting.</span></span>  
  
### <a name="handling-source-oracle-connection-errors"></a><span data-ttu-id="00c87-194">ソース Oracle との接続エラーの処理</span><span class="sxs-lookup"><span data-stu-id="00c87-194">Handling Source Oracle Connection Errors</span></span>  
 <span data-ttu-id="00c87-195">Oracle CDC Service では、ソース Oracle データベースとの固定接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="00c87-195">The Oracle CDC Service needs a persistent connection with the source Oracle database.</span></span> <span data-ttu-id="00c87-196">サービスの構成とは関係がない接続エラー (ネットワーク エラーなど) の多くは、一時的なエラーと見なされます。</span><span class="sxs-lookup"><span data-stu-id="00c87-196">Many connection errors that are unrelated to the service configuration (such as networking errors) are considered transient.</span></span> <span data-ttu-id="00c87-197">したがって、Oracle CDC Service と Oracle データベースの間の接続を確立できない場合 (起動時か作業中に切断された後)、サービスの状態は SUSPENDED/DISCONNECTED になり、定期的に接続が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-197">Therefore, if the Oracle CDC Service cannot establish connection with the Oracle database (either on start or during work following a disconnection), the service changes its state to SUSPENDED/DISCONNECTED and enters a retry loop where the connection is retried at regular intervals.</span></span> <span data-ttu-id="00c87-198">この場合、接続が再確立されると処理が続行されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-198">When the connection is re-established, processing continues.</span></span>  
  
 <span data-ttu-id="00c87-199">それ以外に、一時的なエラーでない接続エラーもあります (たとえば、資格情報が正しくない、必要な特権がない、データベースのアドレスが正しくないなど)。</span><span class="sxs-lookup"><span data-stu-id="00c87-199">Other types of connection errors are not transient (for example, bad credentials, insufficient privileges, and bad database address).</span></span> <span data-ttu-id="00c87-200">それらのエラーが発生した場合は、Oracle CDC Service の状態は ERROR/MISCONFIGURED または ERROR/PASSWORD-REQUIRED になり、サービスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="00c87-200">When these errors occur, the Oracle CDC Service state is set to ERROR/MISCONFIGURED or to ERROR/PASSWORD-REQUIRED and the service is disabled.</span></span> <span data-ttu-id="00c87-201">この場合、処理を再開するには、基になるエラーを解決してから、CDC Oracle インスタンスを手動で再び有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="00c87-201">When the user fixes the underlying error, the Oracle CDC Instance should be manually re-enabled for processing to resume.</span></span>  
  
 <span data-ttu-id="00c87-202">一時的なエラーかどうかが明確でない場合は、一時的なエラーと想定して対処することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="00c87-202">When it is not clear whether the error is transient, it is best to assume it is transient.</span></span>  
  
### <a name="handling-target-sql-server-connection-errors"></a><span data-ttu-id="00c87-203">対象の SQL Server との接続エラーの処理</span><span class="sxs-lookup"><span data-stu-id="00c87-203">Handling Target SQL Server Connection Errors</span></span>  
 <span data-ttu-id="00c87-204">Oracle CDC Service では、対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの固定接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="00c87-204">The Oracle CDC Service needs a persistent connection to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="00c87-205">この接続は次の目的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-205">This connection is used to:</span></span>  
  
-   <span data-ttu-id="00c87-206">この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを実行する同じ名前のサービスがほかにないことを確認する。</span><span class="sxs-lookup"><span data-stu-id="00c87-206">Ensure that there are no other services by the same name currently working with this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="00c87-207">有効または無効にする Oracle CDC インスタンスを確認し、そのサブプロセスを開始 (または停止) する。</span><span class="sxs-lookup"><span data-stu-id="00c87-207">Check which Oracle CDC Instance is enabled or disabled and start (or stop) its subprocess.</span></span>  
  
 <span data-ttu-id="00c87-208">対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとの接続を確立し、この名前で実行されている Oracle CDC Service がこのサービスだけであることを確認したら、有効にする Oracle CDC インスタンスを確認し、それらによるプロセスの処理を開始することができます (その後、無効になったらそれらのプロセスを停止します)。</span><span class="sxs-lookup"><span data-stu-id="00c87-208">When the service establishes a connection with the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and verifies that it is the only Oracle CDC service by this name that is working, it can check which Oracle CDC instances are enabled and start their handling processes (afterward the service stops these processes when they are disabled).</span></span> <span data-ttu-id="00c87-209">Oracle CDC インスタンスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続を使用して、CDC Oracle インスタンスの CDC データベースと連携します。</span><span class="sxs-lookup"><span data-stu-id="00c87-209">The Oracle CDC instances use their [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections to work with the CDC database of the Oracle CDC instance.</span></span>  
  
 <span data-ttu-id="00c87-210">対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続できなかった場合のエラーの処理方法は、そのエラーが一時的なエラーであるかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="00c87-210">How errors are handled when the connection to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fails depends on whether the errors are transient.</span></span>  
  
 <span data-ttu-id="00c87-211">一時的でない既知のエラー (資格情報が正しくない、必要な特権がない、接続情報が正しくないなど) の場合は、Windows イベント ログにエラーが記録され、サービスが停止します ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続できないため、トレース テーブルには書き込まれません)。</span><span class="sxs-lookup"><span data-stu-id="00c87-211">For known non-transient errors (such as bad credentials, insufficient privileges, bad connection information), the service logs an error to the Windows event log and stops (it cannot write to the trace table because it cannot connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).</span></span> <span data-ttu-id="00c87-212">この場合は、エラーを解決し、Oracle CDC Windows サービスを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00c87-212">In this case, the user must resolve the error and restart the Oracle CDC Windows service.</span></span>  
  
 <span data-ttu-id="00c87-213">一時的なエラーや予期しないエラーの場合は、操作が繰り返し再試行され、相当な時間が経過してもエラーが解決しないと、CDC Service の CDC インスタンスのサブプロセスが停止されて、最初の接続試行に戻ります (この時点で、指定された CDC サービスの制御が既に別のコンピューターの Oracle CDC Service に移っている場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="00c87-213">For transient errors and unexpected errors, the operation is retried several times and if the failure persists for a significant time period, the CDC Service stops its CDC Instance subprocesses and goes back to its initial connection attempt (by this time, an Oracle CDC Service on another machine may have already taken control of the named CDC service).</span></span>  
  
### <a name="handling-target-sql-server-storage-full-errors"></a><span data-ttu-id="00c87-214">対象の SQL Server の記憶領域に空きがない場合のエラーの処理</span><span class="sxs-lookup"><span data-stu-id="00c87-214">Handling Target SQL Server Storage Full Errors</span></span>  
 <span data-ttu-id="00c87-215">Oracle CDC Service では、新しい変更データを対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC データベースに挿入できないことを検出した場合、イベント ログに警告を書き込み、トレース レコードの挿入を試行します (この操作も同じ理由で失敗する可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="00c87-215">When the Oracle CDC Service detects that it cannot insert new change data into the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC database, it writes a warning to the event log and tries to insert a trace record (although that may fail for the same reason).</span></span> <span data-ttu-id="00c87-216">処理が成功するまで、この操作が一定の間隔で再試行されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-216">It then retries the operation in a specific interval until it is successful.</span></span>  
  
### <a name="handling-oracle-cdc-errors"></a><span data-ttu-id="00c87-217">Oracle CDC のエラーの処理</span><span class="sxs-lookup"><span data-stu-id="00c87-217">Handling Oracle CDC Errors</span></span>  
 <span data-ttu-id="00c87-218">Oracle CDC インスタンスでは、Oracle トランザクション ログを読み取って処理します。</span><span class="sxs-lookup"><span data-stu-id="00c87-218">The Oracle CDC Instance reads the Oracle transaction log and processes it.</span></span> <span data-ttu-id="00c87-219">CDC の処理でエラーが発生すると、 **cdc.xdbcdc_state** テーブルで報告されます。ユーザーは、報告されたエラーに基づいて手動で対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00c87-219">If the CDC processing encounters an error, it is reported in the **cdc.xdbcdc_state** table and the user needs to manually intervene based on the reported error.</span></span>  
  
 <span data-ttu-id="00c87-220">たとえば、Oracle CDC インスタンスがアクティブにならない時間がしばらく続き、必要な Oracle トランザクション ログ ファイルを使用できなくなったとします。</span><span class="sxs-lookup"><span data-stu-id="00c87-220">For example, the Oracle CDC Instance may not be active for an extended duration and the required Oracle transaction log files are no longer available.</span></span> <span data-ttu-id="00c87-221">この場合、Oracle CDC インスタンスで処理を再開するには、必要なログを Oracle DBA で復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00c87-221">In this case, the Oracle DBA must restore the required logs for the Oracle CDC Instance to resume processing.</span></span>  
  
### <a name="handling-unexpected-oracle-cdc-instance-failures"></a><span data-ttu-id="00c87-222">Oracle CDC インスタンスの予期しないエラーの処理</span><span class="sxs-lookup"><span data-stu-id="00c87-222">Handling Unexpected Oracle CDC Instance Failures</span></span>  
 <span data-ttu-id="00c87-223">Oracle CDC Service では、CDC インスタンスのサブプロセスを監視しています。</span><span class="sxs-lookup"><span data-stu-id="00c87-223">The Oracle CDC Service monitors its CDC Instance subprocesses.</span></span> <span data-ttu-id="00c87-224">CDC インスタンスのサブプロセスが中止されると、MSXDBCDC.dbo.xdbcdc_databases テーブルでそのサブプロセスが無効になり、cdc.xdbcdc_state の状態が ABORTED に更新されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-224">When a CDC Instance subprocess aborts, the CDC Service disables it in the MSXDBCDC.dbo.xdbcdc_databases table and updates its cdc.xdbcdc_state status to ABORTED.</span></span> <span data-ttu-id="00c87-225">この場合、詳細な分析のために、標準の Windows エラー報告ダイアログ ボックスでこのエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="00c87-225">In this case, the standard Windows Error Reporting dialog box is used to report this error for further analysis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c87-226">参照</span><span class="sxs-lookup"><span data-stu-id="00c87-226">See Also</span></span>  
 <span data-ttu-id="00c87-227">[Attunity の Change Data Capture Designer for Oracle](change-data-capture-designer-for-oracle-by-attunity.md) </span><span class="sxs-lookup"><span data-stu-id="00c87-227">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span></span>  
 [<span data-ttu-id="00c87-228">Oracle CDC インスタンス</span><span class="sxs-lookup"><span data-stu-id="00c87-228">The Oracle CDC Instance</span></span>](the-oracle-cdc-instance.md)  