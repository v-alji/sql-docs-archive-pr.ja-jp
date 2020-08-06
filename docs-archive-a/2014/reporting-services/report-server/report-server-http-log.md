---
title: レポート サーバーの HTTP ログ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- HTTP [Reporting Services]
ms.assetid: 6cc433b7-165c-4b16-9034-79256dd6735f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 46adee4fb65361bb9b338c89b6e370ce1da68f9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633755"
---
# <a name="report-server-http-log"></a><span data-ttu-id="d2e5a-102">レポート サーバーの HTTP ログ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-102">Report Server HTTP Log</span></span>
  <span data-ttu-id="d2e5a-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーの HTTP ログ ファイルには、レポート サーバーによって処理された HTTP 要求および HTTP 応答がすべて記録されます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Report Server HTTP log files keep a record of every HTTP request and response handled by the report server.</span></span> <span data-ttu-id="d2e5a-104">要求のオーバーフローやタイムアウト エラーは、レポート サーバーに到達しないため、ログ ファイルには記録されません。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-104">Because request overflow and timeout errors do not reach the report server, they are not recorded in the log file.</span></span>  
  
 <span data-ttu-id="d2e5a-105">HTTP ログは既定では有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-105">HTTP logging is not enabled by default.</span></span> <span data-ttu-id="d2e5a-106">HTTP ログを有効にするには、インストールでこの機能を使用するように**ReportingServicesService.exe.config**構成ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-106">To enable the HTTP logging, modify the **ReportingServicesService.exe.config** configuration file to use this feature in your installation.</span></span>  
  
## <a name="viewing-log-information"></a><span data-ttu-id="d2e5a-107">ログ情報の表示</span><span class="sxs-lookup"><span data-stu-id="d2e5a-107">Viewing Log Information</span></span>  
 <span data-ttu-id="d2e5a-108">ログは、ASCII テキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-108">The log is an ASCII text file.</span></span> <span data-ttu-id="d2e5a-109">任意のテキスト エディターでファイルを閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-109">You can use any text editor to view the file.</span></span> <span data-ttu-id="d2e5a-110">レポート サーバーの HTTP ログ ファイルは、IIS における W3C 拡張ログ ファイルに相当し、同様のフィールドが使用されています。そのため、既存の IIS ログ ファイル ビューアーを使用して、レポート サーバーの HTTP ログ ファイルを閲覧することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-110">The Report Server HTTP log file is equivalent to the W3C extended log file in IIS and uses similar fields so that you can use existing IIS log file viewers to read the report server HTTP log file.</span></span> <span data-ttu-id="d2e5a-111">次の表に、HTTP ログ ファイルの補足情報を示します。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-111">The following table provides additional information about the HTTP log file:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2e5a-112">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="d2e5a-112">**File name**</span></span>|<span data-ttu-id="d2e5a-113">既定では、ログ ファイル名は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-113">By default, the log file name(s) are</span></span><br /><br /> `ReportServerService_HTTP_<timestamp>.log.`<br /><br /> <span data-ttu-id="d2e5a-114">ReportingServicesService.exe.config ファイルで HttpTraceFileName 属性を変更することにより、ファイル名のプレフィックスをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-114">You can customize the prefix of the file name by modifying the HttpTraceFileName attribute in the ReportingServicesService.exe.config file.</span></span> <span data-ttu-id="d2e5a-115">タイムスタンプには、協定世界時 (UTC) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-115">The timestamp is based on Coordinated Universal Time (UTC).</span></span>|  
|<span data-ttu-id="d2e5a-116">**ファイルの場所**</span><span class="sxs-lookup"><span data-stu-id="d2e5a-116">**File location**</span></span>|<span data-ttu-id="d2e5a-117">ファイルは、次の場所に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-117">The files are written to the following location:</span></span><br /><br /> `\Microsoft SQL Server\<SQL Server Instance>\Reporting Services\LogFiles`|  
|<span data-ttu-id="d2e5a-118">**ファイル形式**</span><span class="sxs-lookup"><span data-stu-id="d2e5a-118">**File format**</span></span>|<span data-ttu-id="d2e5a-119">このファイルは EN-US 形式です。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-119">The file is in EN-US format.</span></span> <span data-ttu-id="d2e5a-120">ASCII テキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-120">It is an ASCII text file.</span></span>|  
|<span data-ttu-id="d2e5a-121">**ファイルの作成および保存**</span><span class="sxs-lookup"><span data-stu-id="d2e5a-121">**File creation and retention**</span></span>|<span data-ttu-id="d2e5a-122">HTTP ログは、構成ファイルでログ機能を有効にし、サービスを再開した後、レポート サーバーによって HTTP 要求が処理されて初めて作成されます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-122">The HTTP log is created after you enable it in the configuration file, restart the service, and the report server handles an HTTP request.</span></span> <span data-ttu-id="d2e5a-123">設定を構成したにもかかわらず、ログ ファイルが確認できない場合は、レポートを開くか、レポート サーバー アプリケーション (レポート マネージャーなど) を起動して、HTTP 要求を生成すると、ログ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-123">If you configure the settings but do not see the log file, open a report or start a report server application (such as Report Manager) to generate an HTTP request to create the file.</span></span><br /><br /> <span data-ttu-id="d2e5a-124">ログ ファイルの新しいインスタンスは、各サービスが再開され、その後、HTTP 要求がレポート サーバーに送信されると作成されます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-124">A new instance of the log file will be created after each service restart and subsequent HTTP request to the report server.</span></span><br /><br /> <span data-ttu-id="d2e5a-125">既定では、トレース ログのサイズの上限は 32 MB であり、14 日後に削除されます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-125">By default, trace logs are limited to 32 megabytes and deleted after 14 days.</span></span>|  
  
## <a name="configuration-settings-for-report-server-http-log"></a><span data-ttu-id="d2e5a-126">レポート サーバーの HTTP ログの構成設定</span><span class="sxs-lookup"><span data-stu-id="d2e5a-126">Configuration Settings for Report Server HTTP Log</span></span>  
 <span data-ttu-id="d2e5a-127">レポートサーバーの HTTP ログを構成するには、メモ帳を使用して**ReportingServicesService.exe.config**ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-127">To configure the Report Server HTTP log, use Notepad to modify the **ReportingServicesService.exe.config** file.</span></span> <span data-ttu-id="d2e5a-128">構成ファイルは、\Program Files\Microsoft SQL Server\MSSQL.n\Reporting Services\ReportServer\Bin フォルダーに格納されています。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-128">The configuration file is located in the \Program Files\Microsoft SQL Server\MSSQL.n\Reporting Services\ReportServer\Bin folder.</span></span>  
  
 <span data-ttu-id="d2e5a-129">HTTP サーバーを有効にするには、`http:4` を、ReportingServicesService.exe.config ファイルの RStrace セクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-129">To enable the HTTP server, add `http:4` to the RStrace section of the ReportingServicesService.exe.config file.</span></span> <span data-ttu-id="d2e5a-130">その他の HTTP ログ ファイル エントリはすべてオプションです。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-130">All other HTTP log file entries are optional.</span></span> <span data-ttu-id="d2e5a-131">次の例には、RStrace セクションに上書きする形でセクション全体を貼り付けて、不要な設定を削除するだけで済むように、すべての設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-131">The following example includes all settings so that you can paste the whole section over the RStrace section, and then delete the settings you do not need.</span></span>  
  
```  
   <RStrace>  
         <add name="FileName" value="ReportServerService_" />  
         <add name="FileSizeLimitMb" value="32" />  
         <add name="KeepFilesForDays" value="14" />  
         <add name="Prefix" value="tid, time" />  
         <add name="TraceListeners" value="debugwindow, file" />  
         <add name="TraceFileMode" value="unique" />  
         <add name="HttpTraceFileName" value="ReportServerService_HTTP_" />  
         <add name="HttpTraceSwitches" value="date,time, clientip,username,serverip,serverport,host,method,uristem,uriquery,protocolstatus,bytesreceived,timetaken,protocolversion,useragent,cookiereceived,cookiesent,referrer" />  
         <add name="Components" value="all:3,http:4" />  
   </RStrace>  
```  
  
## <a name="log-file-fields"></a><span data-ttu-id="d2e5a-132">ログ ファイル フィールド</span><span class="sxs-lookup"><span data-stu-id="d2e5a-132">Log File Fields</span></span>  
 <span data-ttu-id="d2e5a-133">次の表は、ログで利用できるフィールドの一覧です。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-133">The following table describes the fields that are available in the log.</span></span> <span data-ttu-id="d2e5a-134">ログに含めるフィールドは、`HTTPTraceSwitches` 構成設定で指定できます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-134">The field list is configurable; you can specify which fields to include through the `HTTPTraceSwitches` configuration setting.</span></span> <span data-ttu-id="d2e5a-135">を指定しない場合、**既定**の列によって、フィールドがログファイルに自動的に含まれるかどうかが指定され `HTTPTraceSwitches` ます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-135">The **Default** column specifies whether the field will be included in the log file automatically if you do not specify `HTTPTraceSwitches`.</span></span>  
  
|<span data-ttu-id="d2e5a-136">フィールド</span><span class="sxs-lookup"><span data-stu-id="d2e5a-136">Field</span></span>|<span data-ttu-id="d2e5a-137">説明</span><span class="sxs-lookup"><span data-stu-id="d2e5a-137">Description</span></span>|<span data-ttu-id="d2e5a-138">Default</span><span class="sxs-lookup"><span data-stu-id="d2e5a-138">Default</span></span>|  
|-----------|-----------------|-------------|  
|<span data-ttu-id="d2e5a-139">HttpTraceFileName</span><span class="sxs-lookup"><span data-stu-id="d2e5a-139">HttpTraceFileName</span></span>|<span data-ttu-id="d2e5a-140">この値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-140">This value is optional.</span></span> <span data-ttu-id="d2e5a-141">既定値は ReportServerServiceHTTP_ です。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-141">The default value is ReportServerServiceHTTP_.</span></span> <span data-ttu-id="d2e5a-142">別のファイル名前付け規則 (ログ ファイルを一元管理する場合はサーバー名など) を使用する場合は、異なる値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-142">You can specify a different value if want to use a different file naming convention (for example, to include the server name if you are saving log files to a central location).</span></span>|<span data-ttu-id="d2e5a-143">はい</span><span class="sxs-lookup"><span data-stu-id="d2e5a-143">Yes</span></span>|  
|<span data-ttu-id="d2e5a-144">HTTPTraceSwitches</span><span class="sxs-lookup"><span data-stu-id="d2e5a-144">HttpTraceSwitches</span></span>|<span data-ttu-id="d2e5a-145">この値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-145">This value is optional.</span></span> <span data-ttu-id="d2e5a-146">指定した場合、ログ ファイルに使用するフィールドをコンマ区切り形式で構成できます。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-146">If you specify it, you can configure the fields used in the log file in comma-delimited format.</span></span>|<span data-ttu-id="d2e5a-147">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-147">No</span></span>|  
|<span data-ttu-id="d2e5a-148">Date</span><span class="sxs-lookup"><span data-stu-id="d2e5a-148">Date</span></span>|<span data-ttu-id="d2e5a-149">アクティビティが発生した日付。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-149">The date when the activity occurred.</span></span>|<span data-ttu-id="d2e5a-150">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-150">No</span></span>|  
|<span data-ttu-id="d2e5a-151">Time</span><span class="sxs-lookup"><span data-stu-id="d2e5a-151">Time</span></span>|<span data-ttu-id="d2e5a-152">アクティビティが発生した時刻。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-152">The time when the activity occurred.</span></span>|<span data-ttu-id="d2e5a-153">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-153">No</span></span>|  
|<span data-ttu-id="d2e5a-154">ClientIp</span><span class="sxs-lookup"><span data-stu-id="d2e5a-154">ClientIp</span></span>|<span data-ttu-id="d2e5a-155">レポート サーバーにアクセスしているクライアントの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-155">The IP address of the client accessing the report server.</span></span>|<span data-ttu-id="d2e5a-156">はい</span><span class="sxs-lookup"><span data-stu-id="d2e5a-156">Yes</span></span>|  
|<span data-ttu-id="d2e5a-157">UserName</span><span class="sxs-lookup"><span data-stu-id="d2e5a-157">UserName</span></span>|<span data-ttu-id="d2e5a-158">レポート サーバーにアクセスしたユーザー名。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-158">The name of the user who accessed the report server.</span></span>|<span data-ttu-id="d2e5a-159">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-159">No</span></span>|  
|<span data-ttu-id="d2e5a-160">ServerPort</span><span class="sxs-lookup"><span data-stu-id="d2e5a-160">ServerPort</span></span>|<span data-ttu-id="d2e5a-161">接続に使用されたポート番号。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-161">The port number used for the connection.</span></span>|<span data-ttu-id="d2e5a-162">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-162">No</span></span>|  
|<span data-ttu-id="d2e5a-163">Host</span><span class="sxs-lookup"><span data-stu-id="d2e5a-163">Host</span></span>|<span data-ttu-id="d2e5a-164">ホスト ヘッダーの内容。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-164">The content of the host header.</span></span>|<span data-ttu-id="d2e5a-165">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-165">No</span></span>|  
|<span data-ttu-id="d2e5a-166">方法</span><span class="sxs-lookup"><span data-stu-id="d2e5a-166">Method</span></span>|<span data-ttu-id="d2e5a-167">クライアントから呼び出されたアクションまたは SOAP メソッド。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-167">The action or SOAP method called from the client.</span></span>|<span data-ttu-id="d2e5a-168">はい</span><span class="sxs-lookup"><span data-stu-id="d2e5a-168">Yes</span></span>|  
|<span data-ttu-id="d2e5a-169">UriStem</span><span class="sxs-lookup"><span data-stu-id="d2e5a-169">UriStem</span></span>|<span data-ttu-id="d2e5a-170">アクセスされたリソース。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-170">The resource accessed.</span></span>|<span data-ttu-id="d2e5a-171">はい</span><span class="sxs-lookup"><span data-stu-id="d2e5a-171">Yes</span></span>|  
|<span data-ttu-id="d2e5a-172">UriQuery</span><span class="sxs-lookup"><span data-stu-id="d2e5a-172">UriQuery</span></span>|<span data-ttu-id="d2e5a-173">リソースへのアクセスに使用されたクエリ。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-173">The query used to access the resource.</span></span>|<span data-ttu-id="d2e5a-174">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-174">No</span></span>|  
|<span data-ttu-id="d2e5a-175">ProtocolStatus</span><span class="sxs-lookup"><span data-stu-id="d2e5a-175">ProtocolStatus</span></span>|<span data-ttu-id="d2e5a-176">HTTP 状態コード。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-176">The HTTP status code.</span></span>|<span data-ttu-id="d2e5a-177">はい</span><span class="sxs-lookup"><span data-stu-id="d2e5a-177">Yes</span></span>|  
|<span data-ttu-id="d2e5a-178">BytesReceived</span><span class="sxs-lookup"><span data-stu-id="d2e5a-178">BytesReceived</span></span>|<span data-ttu-id="d2e5a-179">サーバーが受信したバイト数。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-179">The number of bytes received by the server.</span></span>|<span data-ttu-id="d2e5a-180">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-180">No</span></span>|  
|<span data-ttu-id="d2e5a-181">TimeTaken</span><span class="sxs-lookup"><span data-stu-id="d2e5a-181">TimeTaken</span></span>|<span data-ttu-id="d2e5a-182">HTTP.SYS が要求データを返してから、サーバーが最後の送信を完了するまでのミリ秒単位の時間 (ネットワークの伝送時間を除く)。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-182">The time (in milliseconds) from the instant HTTP.SYS returns request data until the server finishes the last send, excluding network transmission time.</span></span>|<span data-ttu-id="d2e5a-183">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-183">No</span></span>|  
|<span data-ttu-id="d2e5a-184">ProtocolVersion</span><span class="sxs-lookup"><span data-stu-id="d2e5a-184">ProtocolVersion</span></span>|<span data-ttu-id="d2e5a-185">クライアントが使用するプロトコル バージョン。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-185">The protocol version used by the client.</span></span>|<span data-ttu-id="d2e5a-186">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-186">No</span></span>|  
|<span data-ttu-id="d2e5a-187">UserAgent</span><span class="sxs-lookup"><span data-stu-id="d2e5a-187">UserAgent</span></span>|<span data-ttu-id="d2e5a-188">クライアントが使用しているブラウザーの種類。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-188">The browser type used by the client.</span></span>|<span data-ttu-id="d2e5a-189">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-189">No</span></span>|  
|<span data-ttu-id="d2e5a-190">CookieReceived</span><span class="sxs-lookup"><span data-stu-id="d2e5a-190">CookieReceived</span></span>|<span data-ttu-id="d2e5a-191">サーバーが受信したクッキーの内容。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-191">The content of the cookie received by the server.</span></span>|<span data-ttu-id="d2e5a-192">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-192">No</span></span>|  
|<span data-ttu-id="d2e5a-193">CookieSent</span><span class="sxs-lookup"><span data-stu-id="d2e5a-193">CookieSent</span></span>|<span data-ttu-id="d2e5a-194">サーバーによって送信されたクッキーの内容。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-194">The content of the cookie sent by the server.</span></span>|<span data-ttu-id="d2e5a-195">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-195">No</span></span>|  
|<span data-ttu-id="d2e5a-196">Referrer</span><span class="sxs-lookup"><span data-stu-id="d2e5a-196">Referrer</span></span>|<span data-ttu-id="d2e5a-197">クライアントが直前に訪問したサイト。</span><span class="sxs-lookup"><span data-stu-id="d2e5a-197">The previous site visited by the client.</span></span>|<span data-ttu-id="d2e5a-198">いいえ</span><span class="sxs-lookup"><span data-stu-id="d2e5a-198">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2e5a-199">参照</span><span class="sxs-lookup"><span data-stu-id="d2e5a-199">See Also</span></span>  
 <span data-ttu-id="d2e5a-200">[Report Server Service Trace Log](report-server-service-trace-log.md) </span><span class="sxs-lookup"><span data-stu-id="d2e5a-200">[Report Server Service Trace Log](report-server-service-trace-log.md) </span></span>  
 <span data-ttu-id="d2e5a-201">[Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="d2e5a-201">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 [<span data-ttu-id="d2e5a-202">エラーとイベントのリファレンス (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="d2e5a-202">Errors and Events Reference &#40;Reporting Services&#41;</span></span>](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  