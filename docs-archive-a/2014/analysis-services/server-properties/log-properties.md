---
title: ログのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- QueryLogFileSize property
- QueryLogTableName property
- TraceBackgroundDistributionPeriod property
- TraceMaxRowsetSize property
- NullKeyConvertedToUnknown property
- CrashReportsFolder property
- TraceDefinitionFile property
- SQLDumperFlagsOn property
- KeyErrorLimit property
- SnapshotDefinitionFile property
- MinidumpErrorList property
- ErrorLogFileName property
- KeyDuplicate property
- IgnoreDataTruncation property
- logs [Analysis Services]
- Enabled property
- FileSizeMB property
- TraceFileWriteTrailerPeriod property
- TraceQueryResponseTextChunkSize property
- File property
- FileBufferSize property
- TraceRowsetBackgroundFlushPeriod property
- ErrorLogFileSize property
- TraceRequestParameters property
- KeyErrorLimitAction property
- CreateQueryLogTable property
- LogDir property
- TraceBackgroundFlushPeriod property
- TraceFileBufferSize property
- SQLDumperFlagsOff property
- QueryLogConnectionString property
- KeyNotFound property
- KeyErrorLogFile property
- TraceReportFQDN property
- KeyErrorAction property
- QueryLogFileName property
- MessageLogs property
- MiniDumpFlagsOn property
- SnapshotFrequencySec property
- QueryLogSampling property
- CreateAndSendCrashReports property
- LogDurationSec property
ms.assetid: 33fd90ee-cead-48f0-8ff9-9b458994c766
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3761ce3dca232db8968a2a7cba083dcc5554d792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743486"
---
# <a name="log-properties"></a><span data-ttu-id="0f01a-102">ログのプロパティ</span><span class="sxs-lookup"><span data-stu-id="0f01a-102">Log Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0f01a-103">では、次の表に示すログ サーバー プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0f01a-103">supports the log server properties listed in the following tables.</span></span> <span data-ttu-id="0f01a-104">その他のサーバー プロパティとその設定方法の詳細については、「 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
## <a name="general"></a><span data-ttu-id="0f01a-105">全般</span><span class="sxs-lookup"><span data-stu-id="0f01a-105">General</span></span>  
 `File`  
 <span data-ttu-id="0f01a-106">サーバーのログ ファイルの名前を識別する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-106">A string property that identifies the name of the server log file.</span></span> <span data-ttu-id="0f01a-107">このプロパティは、データベース テーブル (既定の動作) ではなく、ディスク ファイルがログ記録に使用される場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="0f01a-107">This property only applies when a disk file is used for logging, as opposed to a database table (the default behavior).</span></span>  
  
 <span data-ttu-id="0f01a-108">このプロパティの既定値は msmdsrv.log です。</span><span class="sxs-lookup"><span data-stu-id="0f01a-108">The default value for this property is msmdsrv.log.</span></span>  
  
 `FileBufferSize`  
 <span data-ttu-id="0f01a-109">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MessageLogs`  
 <span data-ttu-id="0f01a-110">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="error-log"></a><span data-ttu-id="0f01a-111">エラー ログ</span><span class="sxs-lookup"><span data-stu-id="0f01a-111">Error Log</span></span>  
 <span data-ttu-id="0f01a-112">次のプロパティをサーバー インスタンス レベルで設定し、他のツールとデザイナーに表示されるエラーの構成の既定値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0f01a-112">You can set these properties at the server instance level to modify the default values for Error Configuration that appear in other tools and designers.</span></span> <span data-ttu-id="0f01a-113">詳細については、「 [SSAS-多次元&#41;の &#40;キューブ、パーティション、およびディメンションの処理のエラー構成](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)」を参照してください <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0f01a-113">See [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md) and <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> for more information.</span></span>  
  
 <span data-ttu-id="0f01a-114">**ErrorLog\ErrorLogFileName**</span><span class="sxs-lookup"><span data-stu-id="0f01a-114">**ErrorLog\ErrorLogFileName**</span></span>  
 <span data-ttu-id="0f01a-115">サーバーによる処理操作の実行時に既定値として使用されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-115">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="0f01a-116">**ErrorLog\ErrorLogFileSize**</span><span class="sxs-lookup"><span data-stu-id="0f01a-116">**ErrorLog\ErrorLogFileSize**</span></span>  
 <span data-ttu-id="0f01a-117">サーバーによる処理操作の実行時に既定値として使用されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-117">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="0f01a-118">**ErrorLog\KeyErrorAction**</span><span class="sxs-lookup"><span data-stu-id="0f01a-118">**ErrorLog\KeyErrorAction**</span></span>  
 <span data-ttu-id="0f01a-119">`KeyNotFound` エラーが発生した場合に、サーバーが実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-119">Specifies the action taken by the server when a `KeyNotFound` error occurs.</span></span> <span data-ttu-id="0f01a-120">このエラーへの有効な応答は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-120">Valid responses to this error include:</span></span>  
  
-   <span data-ttu-id="0f01a-121">`ConvertToUnknown` は、不明なメンバーにエラーのキー値を割り当てるようにサーバーに指示します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-121">`ConvertToUnknown` tells the server to allocate the error key value to the unknown member.</span></span>  
  
-   <span data-ttu-id="0f01a-122">`DiscardRecord` は、レコードを除外するようにサーバーに指示します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-122">`DiscardRecord` tells the server to exclude the record.</span></span>  
  
 <span data-ttu-id="0f01a-123">**ErrorLog\KeyErrorLogFile**</span><span class="sxs-lookup"><span data-stu-id="0f01a-123">**ErrorLog\KeyErrorLogFile**</span></span>  
 <span data-ttu-id="0f01a-124">サービス アカウントが読み取り/書き込み権限を持つフォルダーにある、.log ファイル拡張子を持つ必要があるユーザー定義のファイル名です。</span><span class="sxs-lookup"><span data-stu-id="0f01a-124">This is a user-defined filename that must have a .log file extension, located in a folder on which the service account has read-write permissions.</span></span> <span data-ttu-id="0f01a-125">このログ ファイルには、処理中に生成されたエラーのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0f01a-125">This log file will only contain errors generated during processing.</span></span> <span data-ttu-id="0f01a-126">詳細情報が必要な場合はフライト レコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-126">Use the Flight Recorder if you require more detailed information.</span></span>  
  
 <span data-ttu-id="0f01a-127">**ErrorLog\KeyErrorLimit**</span><span class="sxs-lookup"><span data-stu-id="0f01a-127">**ErrorLog\KeyErrorLimit**</span></span>  
 <span data-ttu-id="0f01a-128">処理が失敗するまでにサーバーが許可するデータ整合性エラーの最大数です。</span><span class="sxs-lookup"><span data-stu-id="0f01a-128">This is the maximum number of data integrity errors that the server will allow before failing the processing.</span></span> <span data-ttu-id="0f01a-129">値が 1 の場合は、数に制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-129">A value of -1 indicates that there is no limit.</span></span> <span data-ttu-id="0f01a-130">既定値は 0 です。これは、最初のエラーが発生した後に処理が停止することを意味します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-130">The default is 0, which means processing stops after the first error occurs.</span></span> <span data-ttu-id="0f01a-131">整数に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f01a-131">You can also set it to a whole number.</span></span>  
  
 <span data-ttu-id="0f01a-132">**ErrorLog\KeyErrorLimitAction**</span><span class="sxs-lookup"><span data-stu-id="0f01a-132">**ErrorLog\KeyErrorLimitAction**</span></span>  
 <span data-ttu-id="0f01a-133">キー エラー数が上限に達した場合にサーバーが実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-133">Specifies the action taken by the server when the number of key errors has reached the upper limit.</span></span> <span data-ttu-id="0f01a-134">このアクションへの有効な応答は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-134">Valid responses to this action include:</span></span>  
  
-   <span data-ttu-id="0f01a-135">`StopProcessing` は、エラーの上限に到達した場合に処理を停止するようにサーバーに指示します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-135">`StopProcessing` tells the server to stop processing when the error limit is reached.</span></span>  
  
-   <span data-ttu-id="0f01a-136">`StopLogging` は、エラーの上限に到達した場合にエラーの記録を停止するものの、処理を継続するようにサーバーに指示します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-136">`StopLogging` tells the server to stop logging errors when the error limit is reached, but allow processing to continue.</span></span>  
  
 <span data-ttu-id="0f01a-137">**ErrorLog\ LogErrorTypes\KeyNotFound**</span><span class="sxs-lookup"><span data-stu-id="0f01a-137">**ErrorLog\ LogErrorTypes\KeyNotFound**</span></span>  
 <span data-ttu-id="0f01a-138">`KeyNotFound` エラーが発生した場合に、サーバーが実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-138">Specifies the action taken by the server when a `KeyNotFound` error occurs.</span></span> <span data-ttu-id="0f01a-139">このエラーへの有効な応答は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-139">Valid responses to this error include:</span></span>  
  
-   <span data-ttu-id="0f01a-140">`IgnoreError` は、エラーを記録せずに処理を継続するか、キー エラーの上限に達するまでカウントするようにサーバーに指示します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-140">`IgnoreError` tells the server to continue processing without logging the error or counting it towards the key error limit.</span></span> <span data-ttu-id="0f01a-141">エラーを無視すると、エラー カウントに追加したり画面またはログ ファイルに記録することなく、処理を継続します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-141">By ignoring the error, you simply allow processing to continue without adding to the error count or logging it to the screen or log file.</span></span> <span data-ttu-id="0f01a-142">レコードにデータの整合性の問題があり、データベースに追加できません。</span><span class="sxs-lookup"><span data-stu-id="0f01a-142">The record in question has a data integrity problem and cannot be added to the database.</span></span> <span data-ttu-id="0f01a-143">レコードは、`KeyErrorAction` プロパティで指定されているとおりに、破棄されるか、不明なメンバーに集計されます。</span><span class="sxs-lookup"><span data-stu-id="0f01a-143">The record will either be discarded or aggregated to Unknown Member, as determined by the `KeyErrorAction` property.</span></span>  
  
-   <span data-ttu-id="0f01a-144">`ReportAndContinue` は、エラーを記録して、キー エラーの上限に達するまでカウントし、処理を継続するようにサーバーに指示します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-144">`ReportAndContinue` tells the server to log the error, count it towards the key error limit, and continue processing.</span></span> <span data-ttu-id="0f01a-145">エラーをトリガーするレコードは、破棄されるか、不明メンバーに変換されます。</span><span class="sxs-lookup"><span data-stu-id="0f01a-145">The record triggering the error is discarded or converted to Unknown Member.</span></span>  
  
-   <span data-ttu-id="0f01a-146">`ReportAndStop` は、エラーを記録し、キー エラーの上限に関係なく処理を直ちに停止するようにサーバーに指示します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-146">`ReportAndStop` tells the server to log the error and stop processing immediately, regardless of the key error limit.</span></span> <span data-ttu-id="0f01a-147">エラーをトリガーするレコードは、破棄されるか、不明メンバーに変換されます。</span><span class="sxs-lookup"><span data-stu-id="0f01a-147">The record triggering the error is discarded or converted to Unknown Member.</span></span>  
  
 <span data-ttu-id="0f01a-148">**ErrorLog\ LogErrorTypes\KeyDuplicate**</span><span class="sxs-lookup"><span data-stu-id="0f01a-148">**ErrorLog\ LogErrorTypes\KeyDuplicate**</span></span>  
 <span data-ttu-id="0f01a-149">重複したキーが見つかった場合に、サーバーが実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-149">Specifies the action taken by the server when a duplicate key is found.</span></span> <span data-ttu-id="0f01a-150">有効な値は、エラーが発生しなかったかのように処理を継続する `IgnoreError`、エラーを記録して処理を継続する `ReportAndContinue`、エラー数がエラーの上限に達していなくてもエラーを記録して直ちに処理を停止する `ReportAndStop` です。</span><span class="sxs-lookup"><span data-stu-id="0f01a-150">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="0f01a-151">**ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**</span><span class="sxs-lookup"><span data-stu-id="0f01a-151">**ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**</span></span>  
 <span data-ttu-id="0f01a-152">NULL キーが不明なメンバーに変換された場合にサーバーが実行する操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-152">Specifies the action taken by the server when a null key has been converted to Unknown Member.</span></span> <span data-ttu-id="0f01a-153">有効な値は、エラーが発生しなかったかのように処理を継続する `IgnoreError`、エラーを記録して処理を継続する `ReportAndContinue`、エラー数がエラーの上限に達していなくてもエラーを記録して直ちに処理を停止する `ReportAndStop` です。</span><span class="sxs-lookup"><span data-stu-id="0f01a-153">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="0f01a-154">**ErrorLog\ LogErrorTypes\NullKeyNotAllowed**</span><span class="sxs-lookup"><span data-stu-id="0f01a-154">**ErrorLog\ LogErrorTypes\NullKeyNotAllowed**</span></span>  
 <span data-ttu-id="0f01a-155">`NullProcessing` がディメンション属性の `Error` に設定されている場合にサーバーが実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-155">Specifies the action taken by the server when `NullProcessing` is set to `Error` for a dimension attribute.</span></span> <span data-ttu-id="0f01a-156">エラーは、指定された属性で NULL 値が許可されていない場合に生成されます。</span><span class="sxs-lookup"><span data-stu-id="0f01a-156">An error is generated when a null value is not allowed in a given attribute.</span></span> <span data-ttu-id="0f01a-157">このエラー構成プロパティは、次の手順を通知します。つまり、エラーを報告してエラーの上限に達するまで処理を継続します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-157">This error configuration property informs the next step, which is to report the error and continue processing until the error limit is reached.</span></span> <span data-ttu-id="0f01a-158">有効な値は、エラーが発生しなかったかのように処理を継続する `IgnoreError`、エラーを記録して処理を継続する `ReportAndContinue`、エラー数がエラーの上限に達していなくてもエラーを記録して直ちに処理を停止する `ReportAndStop` です。</span><span class="sxs-lookup"><span data-stu-id="0f01a-158">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="0f01a-159">**ErrorLog\ LogErrorTypes\CalculationError**</span><span class="sxs-lookup"><span data-stu-id="0f01a-159">**ErrorLog\ LogErrorTypes\CalculationError**</span></span>  
 <span data-ttu-id="0f01a-160">サーバーによる処理操作の実行時に既定値として使用されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-160">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="0f01a-161">**ErrorLog\IgnoreDataTruncation**</span><span class="sxs-lookup"><span data-stu-id="0f01a-161">**ErrorLog\IgnoreDataTruncation**</span></span>  
 <span data-ttu-id="0f01a-162">サーバーによる処理操作の実行時に既定値として使用されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-162">A property used as a default during processing operation performed by the server.</span></span>  
  
## <a name="exception"></a><span data-ttu-id="0f01a-163">例外</span><span class="sxs-lookup"><span data-stu-id="0f01a-163">Exception</span></span>  
 <span data-ttu-id="0f01a-164">**Exception\CreateAndSendCrashReports**</span><span class="sxs-lookup"><span data-stu-id="0f01a-164">**Exception\CreateAndSendCrashReports**</span></span>  
 <span data-ttu-id="0f01a-165">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-165">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-166">**Exception\CrashReportsFolder**</span><span class="sxs-lookup"><span data-stu-id="0f01a-166">**Exception\CrashReportsFolder**</span></span>  
 <span data-ttu-id="0f01a-167">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-167">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-168">**Exception\SQLDumperFlagsOn**</span><span class="sxs-lookup"><span data-stu-id="0f01a-168">**Exception\SQLDumperFlagsOn**</span></span>  
 <span data-ttu-id="0f01a-169">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-169">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-170">**Exception\SQLDumperFlagsOff**</span><span class="sxs-lookup"><span data-stu-id="0f01a-170">**Exception\SQLDumperFlagsOff**</span></span>  
 <span data-ttu-id="0f01a-171">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-171">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-172">**Exception\MiniDumpFlagsOn**</span><span class="sxs-lookup"><span data-stu-id="0f01a-172">**Exception\MiniDumpFlagsOn**</span></span>  
 <span data-ttu-id="0f01a-173">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-173">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-174">**Exception\MinidumpErrorList**</span><span class="sxs-lookup"><span data-stu-id="0f01a-174">**Exception\MinidumpErrorList**</span></span>  
 <span data-ttu-id="0f01a-175">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-175">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="flight-recorder"></a><span data-ttu-id="0f01a-176">Flight Recorder</span><span class="sxs-lookup"><span data-stu-id="0f01a-176">Flight Recorder</span></span>  
 <span data-ttu-id="0f01a-177">**FlightRecorder\Enabled**</span><span class="sxs-lookup"><span data-stu-id="0f01a-177">**FlightRecorder\Enabled**</span></span>  
 <span data-ttu-id="0f01a-178">フライト レコーダー機能が有効かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-178">A Boolean property that indicates whether the flight recorder feature is enabled.</span></span>  
  
 <span data-ttu-id="0f01a-179">**FlightRecorder\FileSizeMB**</span><span class="sxs-lookup"><span data-stu-id="0f01a-179">**FlightRecorder\FileSizeMB**</span></span>  
 <span data-ttu-id="0f01a-180">フライト レコーダーのディスク ファイルのサイズを MB 単位で定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-180">A signed 32-bit integer property that defines the size of the flight recorder disk file, in megabytes.</span></span>  
  
 <span data-ttu-id="0f01a-181">**FlightRecorder\LogDurationSec**</span><span class="sxs-lookup"><span data-stu-id="0f01a-181">**FlightRecorder\LogDurationSec**</span></span>  
 <span data-ttu-id="0f01a-182">フライト レコーダーがロール オーバーされる頻度を秒単位で定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-182">A signed 32-bit integer property that defines the frequency that the flight recorder is rolled over, in seconds.</span></span>  
  
 <span data-ttu-id="0f01a-183">**FlightRecorder\SnapshotDefinitionFile**</span><span class="sxs-lookup"><span data-stu-id="0f01a-183">**FlightRecorder\SnapshotDefinitionFile**</span></span>  
 <span data-ttu-id="0f01a-184">スナップショット定義ファイルの名前を定義する文字列プロパティです。このファイルには、スナップショットの取得時にサーバーに発行される検出コマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0f01a-184">A string property that defines the name of the snapshot definition file, containing discover commands that are issued to the server when a snapshot is taken.</span></span>  
  
 <span data-ttu-id="0f01a-185">このプロパティの既定値は空白です。その場合、既定で使用されるファイル名は FlightRecorderSnapshotDef.xml になります。</span><span class="sxs-lookup"><span data-stu-id="0f01a-185">The default value for this property is blank, which in turn defaults to file name FlightRecorderSnapshotDef.xml.</span></span>  
  
 <span data-ttu-id="0f01a-186">**FlightRecorder\SnapshotFrequencySec**</span><span class="sxs-lookup"><span data-stu-id="0f01a-186">**FlightRecorder\SnapshotFrequencySec**</span></span>  
 <span data-ttu-id="0f01a-187">スナップショットの頻度を秒単位で定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-187">A signed 32-bit integer property that defines the snapshot frequency, in seconds.</span></span>  
  
 <span data-ttu-id="0f01a-188">**FlightRecorder\TraceDefinitionFile**</span><span class="sxs-lookup"><span data-stu-id="0f01a-188">**FlightRecorder\TraceDefinitionFile**</span></span>  
 <span data-ttu-id="0f01a-189">フライト レコーダーのトレース定義ファイルの名前を指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-189">A string property that specifies the name of the flight recorder trace definition file.</span></span>  
  
 <span data-ttu-id="0f01a-190">このプロパティの既定値は空白です。その場合、既定で使用されるファイル名は FlightRecorderTraceDef.xml になります。</span><span class="sxs-lookup"><span data-stu-id="0f01a-190">The default value for this property is blank, which in turn defaults to FlightRecorderTraceDef.xml.</span></span>  
  
## <a name="query-log"></a><span data-ttu-id="0f01a-191">クエリ ログ</span><span class="sxs-lookup"><span data-stu-id="0f01a-191">Query Log</span></span>  
 <span data-ttu-id="0f01a-192">**適用対象:** 多次元サーバーモードのみ</span><span class="sxs-lookup"><span data-stu-id="0f01a-192">**Applies to:** Multidimensional server mode only</span></span>  
  
 <span data-ttu-id="0f01a-193">**QueryLog\QueryLogFileName**</span><span class="sxs-lookup"><span data-stu-id="0f01a-193">**QueryLog\QueryLogFileName**</span></span>  
 <span data-ttu-id="0f01a-194">クエリ ログ ファイルの名前を指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-194">A string property that specifies the name of the query log file.</span></span> <span data-ttu-id="0f01a-195">このプロパティは、データベース テーブル (既定の動作) ではなく、ディスク ファイルがログ記録に使用される場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="0f01a-195">This property only applies when a disk file is used for logging, as opposed to a database table (the default behavior).</span></span>  
  
 <span data-ttu-id="0f01a-196">**QueryLog\QueryLogSampling**</span><span class="sxs-lookup"><span data-stu-id="0f01a-196">**QueryLog\QueryLogSampling**</span></span>  
 <span data-ttu-id="0f01a-197">クエリ ログのサンプリング レートを指定する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-197">A signed 32-bit integer property that specifies the query log sampling rate.</span></span>  
  
 <span data-ttu-id="0f01a-198">このプロパティの既定値は 10 であり、10 回のサーバー クエリごとに 1 回がログ記録されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-198">The default value for this property is 10, meaning that 1 out of every 10 server queries is logged.</span></span>  
  
 <span data-ttu-id="0f01a-199">**QueryLog\QueryLogFileSize**</span><span class="sxs-lookup"><span data-stu-id="0f01a-199">**QueryLog\QueryLogFileSize**</span></span>  
 <span data-ttu-id="0f01a-200">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-200">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-201">**QueryLog\QueryLogConnectionString**</span><span class="sxs-lookup"><span data-stu-id="0f01a-201">**QueryLog\QueryLogConnectionString**</span></span>  
 <span data-ttu-id="0f01a-202">クエリ ログ データベースへの接続を指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-202">A string property that specifies the connection to the query log database.</span></span>  
  
 <span data-ttu-id="0f01a-203">**QueryLog\QueryLogTableName**</span><span class="sxs-lookup"><span data-stu-id="0f01a-203">**QueryLog\QueryLogTableName**</span></span>  
 <span data-ttu-id="0f01a-204">クエリ ログ テーブルの名前を指定する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-204">A string property that specifies the name of the query log table.</span></span>  
  
 <span data-ttu-id="0f01a-205">このプロパティの既定値は OlapQueryLog です。</span><span class="sxs-lookup"><span data-stu-id="0f01a-205">The default value for this property is OlapQueryLog.</span></span>  
  
 <span data-ttu-id="0f01a-206">**QueryLog\CreateQueryLogTable**</span><span class="sxs-lookup"><span data-stu-id="0f01a-206">**QueryLog\CreateQueryLogTable**</span></span>  
 <span data-ttu-id="0f01a-207">クエリ ログ テーブルを作成するかどうかを指定するブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0f01a-207">A Boolean property that specifies whether to create the query log table.</span></span>  
  
 <span data-ttu-id="0f01a-208">このプロパティの既定値は False であり、サーバーによってログ テーブルが自動的に作成されず、クエリ イベントがログ記録されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="0f01a-208">The default value for this property is false, which indicates the server will not automatically create the log table and will not log query events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f01a-209">クエリログの構成の詳細については、「 [Analysis Services のログ操作](../instances/log-operations-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-209">For more information about configuring the query log, see [Log operations in Analysis Services](../instances/log-operations-in-analysis-services.md).</span></span>  
  
## <a name="trace"></a><span data-ttu-id="0f01a-210">トレース</span><span class="sxs-lookup"><span data-stu-id="0f01a-210">Trace</span></span>  
 <span data-ttu-id="0f01a-211">**Trace\TraceBackgroundDistributionPeriod**</span><span class="sxs-lookup"><span data-stu-id="0f01a-211">**Trace\TraceBackgroundDistributionPeriod**</span></span>  
 <span data-ttu-id="0f01a-212">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-212">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-213">**Trace\TraceBackgroundFlushPeriod**</span><span class="sxs-lookup"><span data-stu-id="0f01a-213">**Trace\TraceBackgroundFlushPeriod**</span></span>  
 <span data-ttu-id="0f01a-214">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-214">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-215">**Trace\TraceFileBufferSize**</span><span class="sxs-lookup"><span data-stu-id="0f01a-215">**Trace\TraceFileBufferSize**</span></span>  
 <span data-ttu-id="0f01a-216">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-216">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-217">**Trace\TraceFileWriteTrailerPeriod**</span><span class="sxs-lookup"><span data-stu-id="0f01a-217">**Trace\TraceFileWriteTrailerPeriod**</span></span>  
 <span data-ttu-id="0f01a-218">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-218">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-219">**Trace\TraceMaxRowsetSize**</span><span class="sxs-lookup"><span data-stu-id="0f01a-219">**Trace\TraceMaxRowsetSize**</span></span>  
 <span data-ttu-id="0f01a-220">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-220">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-221">**Trace\TraceProtocolTraffic**</span><span class="sxs-lookup"><span data-stu-id="0f01a-221">**Trace\TraceProtocolTraffic**</span></span>  
 <span data-ttu-id="0f01a-222">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-222">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-223">**Trace\TraceQueryResponseTextChunkSize**</span><span class="sxs-lookup"><span data-stu-id="0f01a-223">**Trace\TraceQueryResponseTextChunkSize**</span></span>  
 <span data-ttu-id="0f01a-224">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-224">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-225">**Trace\TraceReportFQDN**</span><span class="sxs-lookup"><span data-stu-id="0f01a-225">**Trace\TraceReportFQDN**</span></span>  
 <span data-ttu-id="0f01a-226">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-226">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-227">**Trace\TraceRequestParameters**</span><span class="sxs-lookup"><span data-stu-id="0f01a-227">**Trace\TraceRequestParameters**</span></span>  
 <span data-ttu-id="0f01a-228">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-228">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0f01a-229">**Trace\TraceRowsetBackgroundFlushPeriod**</span><span class="sxs-lookup"><span data-stu-id="0f01a-229">**Trace\TraceRowsetBackgroundFlushPeriod**</span></span>  
 <span data-ttu-id="0f01a-230">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f01a-230">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f01a-231">参照</span><span class="sxs-lookup"><span data-stu-id="0f01a-231">See Also</span></span>  
 <span data-ttu-id="0f01a-232">[Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="0f01a-232">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="0f01a-233">Analysis Services インスタンスのサーバー モードの決定</span><span class="sxs-lookup"><span data-stu-id="0f01a-233">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
