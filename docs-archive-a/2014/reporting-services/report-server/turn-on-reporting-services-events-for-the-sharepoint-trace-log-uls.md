---
title: Turn on Reporting Services events for the SharePoint trace log (ULS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81110ef6-4289-405c-a931-e7e9f49e69ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d1b0a936c234035baf18ca947661de2663195a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640585"
---
# <a name="turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls"></a><span data-ttu-id="9b774-102">Turn on Reporting Services events for the SharePoint trace log (ULS)</span><span class="sxs-lookup"><span data-stu-id="9b774-102">Turn on Reporting Services events for the SharePoint trace log (ULS)</span></span>
  <span data-ttu-id="9b774-103">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]以降では、SharePoint モードの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サーバーから SharePoint 統合ログ サービス (ULS) のトレース ログに [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] イベントを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="9b774-103">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] servers in SharePoint mode can write [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] events to the SharePoint Unified Logging Service (ULS) trace log.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9b774-104">固有のカテゴリは、SharePoint サーバーの全体管理の [監視] ページで利用できます。</span><span class="sxs-lookup"><span data-stu-id="9b774-104">specific categories are available on the Monitoring page of SharePoint Central Administration.</span></span>

 <span data-ttu-id="9b774-105">このトピックの内容</span><span class="sxs-lookup"><span data-stu-id="9b774-105">In this Topic:</span></span>

-   [<span data-ttu-id="9b774-106">ULS ログの一般的な推奨事項</span><span class="sxs-lookup"><span data-stu-id="9b774-106">General ULS Log Recommendations</span></span>](#bkmk_general)

-   [<span data-ttu-id="9b774-107">Reporting Services カテゴリ内の Reporting Services イベントのオン/オフを切り替えるには</span><span class="sxs-lookup"><span data-stu-id="9b774-107">To turn on and off Reporting Services events in the Reporting Services Category</span></span>](#bkmk_turnon)

-   [<span data-ttu-id="9b774-108">推奨構成</span><span class="sxs-lookup"><span data-stu-id="9b774-108">Recommended Configuration</span></span>](#bkmk_recommended)

-   [<span data-ttu-id="9b774-109">ログ エントリの読み取り</span><span class="sxs-lookup"><span data-stu-id="9b774-109">Reading the logs entries</span></span>](#bkmk_readentries)

-   [<span data-ttu-id="9b774-110">SQL Server Reporting Services イベントの一覧</span><span class="sxs-lookup"><span data-stu-id="9b774-110">List of SQL Server Reporting Services Events</span></span>](#bkmk_list)

-   [<span data-ttu-id="9b774-111">PowerShell でのログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="9b774-111">View a Log file with PowerShell</span></span>](#bkmk_powershell)

-   [<span data-ttu-id="9b774-112">トレース ログの場所</span><span class="sxs-lookup"><span data-stu-id="9b774-112">Trace Log Location</span></span>](#bkmk_trace)

##  <a name="general-uls-log-recommendations"></a><a name="bkmk_general"></a> <span data-ttu-id="9b774-113">ULS ログの一般的な推奨事項</span><span class="sxs-lookup"><span data-stu-id="9b774-113">General ULS Log Recommendations</span></span>
 <span data-ttu-id="9b774-114">次の表は、イベントのカテゴリの一覧です。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 環境を監視する場合の推奨されるレベルも記載されています。</span><span class="sxs-lookup"><span data-stu-id="9b774-114">The following table lists event categories and levels that are recommended for monitoring a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] environment..</span></span> <span data-ttu-id="9b774-115">イベントをログに記録した場合、各エントリには、イベントが記録された時刻、プロセス名、およびスレッド ID が記録されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-115">When an event is logged, each entry includes the time the event was logged, the process name, and the thread ID.</span></span>

|<span data-ttu-id="9b774-116">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="9b774-116">Category</span></span>|<span data-ttu-id="9b774-117">Level</span><span class="sxs-lookup"><span data-stu-id="9b774-117">Level</span></span>|<span data-ttu-id="9b774-118">説明</span><span class="sxs-lookup"><span data-stu-id="9b774-118">Description</span></span>|
|--------------|-----------|-----------------|
|<span data-ttu-id="9b774-119">データベース</span><span class="sxs-lookup"><span data-stu-id="9b774-119">Database</span></span>|<span data-ttu-id="9b774-120">"詳細"</span><span class="sxs-lookup"><span data-stu-id="9b774-120">Verbose</span></span>|<span data-ttu-id="9b774-121">データベース アクセスに関連するイベントが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-121">Logs events that involve database access.</span></span>|
|<span data-ttu-id="9b774-122">全般</span><span class="sxs-lookup"><span data-stu-id="9b774-122">General</span></span>|<span data-ttu-id="9b774-123">"詳細"</span><span class="sxs-lookup"><span data-stu-id="9b774-123">Verbose</span></span>|<span data-ttu-id="9b774-124">次の項目へのアクセスを伴うイベントが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-124">Logs events that involve access to the following items:</span></span><br /><br /> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9b774-125">の Web ページ</span><span class="sxs-lookup"><span data-stu-id="9b774-125">Web pages</span></span><br /><br /> <span data-ttu-id="9b774-126">レポート ビューアーの HTTP ハンドラー</span><span class="sxs-lookup"><span data-stu-id="9b774-126">Report Viewer HTTP handler</span></span><br /><br /> <span data-ttu-id="9b774-127">レポート アクセス (.rdl ファイル)</span><span class="sxs-lookup"><span data-stu-id="9b774-127">Report access (.rdl files)</span></span><br /><br /> <span data-ttu-id="9b774-128">データ ソース (.rsds ファイル)</span><span class="sxs-lookup"><span data-stu-id="9b774-128">Data sources (.rsds files)</span></span><br /><br /> <span data-ttu-id="9b774-129">SharePoint サイト上の URL (.smdl ファイル)</span><span class="sxs-lookup"><span data-stu-id="9b774-129">URLs on the SharePoint site (.smdl files)</span></span>|
|<span data-ttu-id="9b774-130">Office Server 全般</span><span class="sxs-lookup"><span data-stu-id="9b774-130">Office Server General</span></span>|<span data-ttu-id="9b774-131">例外</span><span class="sxs-lookup"><span data-stu-id="9b774-131">Exception</span></span>|<span data-ttu-id="9b774-132">ログオンの失敗が記録されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-132">Logs logon failures.</span></span>|
|<span data-ttu-id="9b774-133">トポロジ</span><span class="sxs-lookup"><span data-stu-id="9b774-133">Topology</span></span>|<span data-ttu-id="9b774-134">"詳細"</span><span class="sxs-lookup"><span data-stu-id="9b774-134">Verbose</span></span>|<span data-ttu-id="9b774-135">現在のユーザー情報が記録されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-135">Logs current user information.</span></span>|
|<span data-ttu-id="9b774-136">Web パーツ</span><span class="sxs-lookup"><span data-stu-id="9b774-136">Web Parts</span></span>|<span data-ttu-id="9b774-137">"詳細"</span><span class="sxs-lookup"><span data-stu-id="9b774-137">Verbose</span></span>|<span data-ttu-id="9b774-138">レポート ビューアー Web パーツへのアクセスを伴うイベントが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-138">Logs events that involve access to the Report Viewer Web Part.</span></span>|

##  <a name="to-turn-on-and-off-reporting-services-events-in-the-reporting-services-category"></a><a name="bkmk_turnon"></a> <span data-ttu-id="9b774-139">Reporting Services カテゴリ内の Reporting Services イベントのオン/オフを切り替えるには</span><span class="sxs-lookup"><span data-stu-id="9b774-139">To turn on and off Reporting Services events in the Reporting Services Category</span></span>

1.  <span data-ttu-id="9b774-140">SharePoint サーバーの全体管理で、以下の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="9b774-140">From SharePoint Central Administration</span></span>

2.  <span data-ttu-id="9b774-141">**[監視]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b774-141">Click **Monitoring**.</span></span>

3.  <span data-ttu-id="9b774-142">**[レポート]** グループの **[診断ログの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b774-142">Click **Configure Diagnostic Logging** in the **Reporting** group.</span></span>

4.  <span data-ttu-id="9b774-143">カテゴリの一覧で **[SQL Server Reporting Services]** を探します。</span><span class="sxs-lookup"><span data-stu-id="9b774-143">Find **SQL Server Reporting Services** in the category list.</span></span>

5.  <span data-ttu-id="9b774-144">プラス記号 (+) をクリックして、 **[SQL Server Reporting Services]** の下のサブカテゴリを展開します。</span><span class="sxs-lookup"><span data-stu-id="9b774-144">Click the plus symbol (+) to expand the sub categories under **SQL Server Reporting Services**.</span></span>

6.  <span data-ttu-id="9b774-145">トレース ログに追加するサブカテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b774-145">Select the subcategories to be added to the trace log.</span></span>

7.  <span data-ttu-id="9b774-146">カテゴリの一覧の下部で、 **[トレース ログの記録対象となる重要度の最も低いイベント]** のイベント レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b774-146">At the bottom of the categories list, select an event level for the **Least critical event to report to the trace log**.</span></span> <span data-ttu-id="9b774-147">トレースを無効にするには、 **[なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b774-147">Select **None** to disable tracing.</span></span>

> [!NOTE]
>  <span data-ttu-id="9b774-148">**[イベント ログの記録対象となる重要度の最も低いイベント]** オプションは、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9b774-148">The option **Least critical event to report to the event log** is not supported by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="9b774-149">オプションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-149">The option is ignored.</span></span>

##  <a name="recommended-configuration"></a><a name="bkmk_recommended"></a> <span data-ttu-id="9b774-150">推奨構成</span><span class="sxs-lookup"><span data-stu-id="9b774-150">Recommended Configuration</span></span>
 <span data-ttu-id="9b774-151">次のログ オプションが標準構成として推奨されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-151">The following logging options are recommended as a standard configuration:</span></span>

-   <span data-ttu-id="9b774-152">**HTTP リダイレクター**</span><span class="sxs-lookup"><span data-stu-id="9b774-152">**HTTP Redirector**</span></span>

-   <span data-ttu-id="9b774-153">**SOAP クライアント プロキシ**</span><span class="sxs-lookup"><span data-stu-id="9b774-153">**SOAP Client Proxy**</span></span>

-   <span data-ttu-id="9b774-154">構成に関する問題が発生する場合は、 **[構成ページ]** を追加します。</span><span class="sxs-lookup"><span data-stu-id="9b774-154">If you are experiencing issues with configuration, add **Configuration Pages**.</span></span>

 <span data-ttu-id="9b774-155">現在のファームの診断ログ設定は、すべて次の PowerShell コマンドレットで確認できます。</span><span class="sxs-lookup"><span data-stu-id="9b774-155">You can review all of the current farm diagnostic log settings with the following PowerShell cmdlet:</span></span>

```powershell
Get-SPDiagnosticConfig
```

##  <a name="reading-the-logs-entries"></a><a name="bkmk_readentries"></a> <span data-ttu-id="9b774-156">ログ エントリの読み取り</span><span class="sxs-lookup"><span data-stu-id="9b774-156">Reading the logs entries</span></span>
 <span data-ttu-id="9b774-157">ログ内の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] エントリは、次の方法で書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-157">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] entries in the log are formatted in the following way.</span></span>

1.  <span data-ttu-id="9b774-158">**Product:SQL Server Reporting Services**</span><span class="sxs-lookup"><span data-stu-id="9b774-158">**Product:SQL Server Reporting Services**</span></span>

2.  <span data-ttu-id="9b774-159">**カテゴリ:** サーバーに関連するイベントには、名前の先頭に "Report Server" という文字が付けられます。</span><span class="sxs-lookup"><span data-stu-id="9b774-159">**Category:** Events related to the server will have the characters "Report Server", at the beginning of the name.</span></span> <span data-ttu-id="9b774-160">例: "Report Server Alerting Runtime"。これらのイベントは、レポート サーバーのログ ファイルにも記録されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-160">For example "Report Server Alerting Runtime" These events are also logged to the report server log files.</span></span>

3.  <span data-ttu-id="9b774-161">**カテゴリ:** Web フロントエンド コンポーネントに関連するイベントや、Web フロントエンド コンポーネントから伝えられたイベントには、"Report Server" は付けられません。</span><span class="sxs-lookup"><span data-stu-id="9b774-161">**Category:** Events related to or communicated from a web front-end component do not contain "Report Server".</span></span> <span data-ttu-id="9b774-162">例: "Service Application Proxy" "Report Server Alerting Runtime"。</span><span class="sxs-lookup"><span data-stu-id="9b774-162">For example "Service Application Proxy" Report Server Alerting Runtime".</span></span> <span data-ttu-id="9b774-163">WFE エントリには CorrelationID が含まれますが、サーバー エントリには含まれません。</span><span class="sxs-lookup"><span data-stu-id="9b774-163">The WFE entries do contain a CorrelationID but the server entries do not.</span></span>

##  <a name="list-of-sql-server-reporting-services-events"></a><a name="bkmk_list"></a> <span data-ttu-id="9b774-164">SQL Server Reporting Services イベントの一覧</span><span class="sxs-lookup"><span data-stu-id="9b774-164">List of SQL Server Reporting Services Events</span></span>
 <span data-ttu-id="9b774-165">次の表に示すのは、SQL Server Reporting Services カテゴリに含まれるイベントの一覧です。</span><span class="sxs-lookup"><span data-stu-id="9b774-165">The following table is a list of the events in the SQL Server Reporting Services Category:</span></span>

|<span data-ttu-id="9b774-166">領域の名前</span><span class="sxs-lookup"><span data-stu-id="9b774-166">Area Name</span></span>|<span data-ttu-id="9b774-167">説明またはサンプルのエントリ</span><span class="sxs-lookup"><span data-stu-id="9b774-167">Description or sample entries</span></span>|
|---------------|-----------------------------------|
|<span data-ttu-id="9b774-168">[構成ページ]</span><span class="sxs-lookup"><span data-stu-id="9b774-168">Configuration Pages</span></span>||
|<span data-ttu-id="9b774-169">HTTP リダイレクター</span><span class="sxs-lookup"><span data-stu-id="9b774-169">HTTP Redirector</span></span>||
|<span data-ttu-id="9b774-170">ローカル モード処理</span><span class="sxs-lookup"><span data-stu-id="9b774-170">Local Mode Processing</span></span>||
|<span data-ttu-id="9b774-171">ローカル モード表示</span><span class="sxs-lookup"><span data-stu-id="9b774-171">Local Mode Rendering</span></span>||
|<span data-ttu-id="9b774-172">SOAP クライアント プロキシ</span><span class="sxs-lookup"><span data-stu-id="9b774-172">SOAP Client Proxy</span></span>||
|<span data-ttu-id="9b774-173">UI ページ</span><span class="sxs-lookup"><span data-stu-id="9b774-173">UI Pages</span></span>||
|<span data-ttu-id="9b774-174">Power View</span><span class="sxs-lookup"><span data-stu-id="9b774-174">Power View</span></span>|<span data-ttu-id="9b774-175">**LogClientTraceEvents** API に書き込まれたログ エントリ。</span><span class="sxs-lookup"><span data-stu-id="9b774-175">Log entries that were written to the **LogClientTraceEvents** API.</span></span> <span data-ttu-id="9b774-176">これらのエントリは、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise Edition 用のアドインの機能など、クライアントアプリケーションから供給され [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] てい [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9b774-176">These entries are sourced from client applications, including [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.</span></span><br /><br /> <span data-ttu-id="9b774-177">LogClientTraceEvents API からのすべてのログ エントリは、"SQL Server Reporting Services" の **Category** および "Power View" の **Area** に記録されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-177">All log entries from the LogClientTraceEvents API will be logged under the **Category** of "SQL Server Reporting Services" and the **Area** of "Power View".</span></span><br /><br /> <span data-ttu-id="9b774-178">"Power View" の Area に記録されるエントリの内容は、クライアント アプリケーションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="9b774-178">The content of entries logged with the area of "Power View" is determined by the client application.</span></span>|
|<span data-ttu-id="9b774-179">Report Server Alerting Runtime</span><span class="sxs-lookup"><span data-stu-id="9b774-179">Report Server Alerting Runtime</span></span>||
|<span data-ttu-id="9b774-180">レポート サーバー アプリケーション ドメイン マネージャー</span><span class="sxs-lookup"><span data-stu-id="9b774-180">Report Server App Domain Manager</span></span>||
|<span data-ttu-id="9b774-181">レポート サーバー バッファー済み応答</span><span class="sxs-lookup"><span data-stu-id="9b774-181">Report Server Buffered Response</span></span>||
|<span data-ttu-id="9b774-182">レポート サーバー キャッシュ</span><span class="sxs-lookup"><span data-stu-id="9b774-182">Report Server Cache</span></span>||
|<span data-ttu-id="9b774-183">レポート サーバー カタログ</span><span class="sxs-lookup"><span data-stu-id="9b774-183">Report Server Catalog</span></span>||
|<span data-ttu-id="9b774-184">レポート サーバー チャンク</span><span class="sxs-lookup"><span data-stu-id="9b774-184">Report Server Chunk</span></span>||
|<span data-ttu-id="9b774-185">レポート サーバー クリーンアップ</span><span class="sxs-lookup"><span data-stu-id="9b774-185">Report Server Cleanup</span></span>||
|<span data-ttu-id="9b774-186">レポート サーバー構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="9b774-186">Report Server Configuration Manager</span></span>|<span data-ttu-id="9b774-187">サンプルのエントリ:</span><span class="sxs-lookup"><span data-stu-id="9b774-187">Sample entries:</span></span><br /><br /> <span data-ttu-id="9b774-188">MediumUsing レポート サーバーの内部 URL http://localhost:80/ReportServer。</span><span class="sxs-lookup"><span data-stu-id="9b774-188">MediumUsing report server internal url http://localhost:80/ReportServer.</span></span><br /><br /> <span data-ttu-id="9b774-189">UnexpectedMissing または無効な ExtendedProtectionLevel 設定です</span><span class="sxs-lookup"><span data-stu-id="9b774-189">UnexpectedMissing or Invalid ExtendedProtectionLevel setting</span></span>|
|<span data-ttu-id="9b774-190">レポート サーバー Crypto</span><span class="sxs-lookup"><span data-stu-id="9b774-190">Report Server Crypto</span></span>||
|<span data-ttu-id="9b774-191">レポート サーバー データ拡張機能</span><span class="sxs-lookup"><span data-stu-id="9b774-191">Report Server Data Extension</span></span>||
|<span data-ttu-id="9b774-192">レポート サーバー DB ポーリング</span><span class="sxs-lookup"><span data-stu-id="9b774-192">Report Server DB Polling</span></span>||
|<span data-ttu-id="9b774-193">レポート サーバーの既定値</span><span class="sxs-lookup"><span data-stu-id="9b774-193">Report Server Default</span></span>||
|<span data-ttu-id="9b774-194">レポート サーバー電子メール拡張機能</span><span class="sxs-lookup"><span data-stu-id="9b774-194">Report Server Email Extension</span></span>||
|<span data-ttu-id="9b774-195">レポート サーバー Excel レンダラー</span><span class="sxs-lookup"><span data-stu-id="9b774-195">Report Server Excel Renderer</span></span>||
|<span data-ttu-id="9b774-196">レポート サーバー拡張機能ファクトリ</span><span class="sxs-lookup"><span data-stu-id="9b774-196">Report Server Extension Factory</span></span>||
|<span data-ttu-id="9b774-197">レポート サーバー HTTP ランタイム</span><span class="sxs-lookup"><span data-stu-id="9b774-197">Report Server HTTP Runtime</span></span>||
|<span data-ttu-id="9b774-198">レポート サーバー画像レンダラー</span><span class="sxs-lookup"><span data-stu-id="9b774-198">Report Server Image Renderer</span></span>||
|<span data-ttu-id="9b774-199">レポート サーバー メモリ監視</span><span class="sxs-lookup"><span data-stu-id="9b774-199">Report Server Memory Monitoring</span></span>||
|<span data-ttu-id="9b774-200">レポート サーバー通知</span><span class="sxs-lookup"><span data-stu-id="9b774-200">Report Server Notification</span></span>||
|<span data-ttu-id="9b774-201">レポート サーバー処理</span><span class="sxs-lookup"><span data-stu-id="9b774-201">Report Server Processing</span></span>||
|<span data-ttu-id="9b774-202">レポート サーバー プロバイダー</span><span class="sxs-lookup"><span data-stu-id="9b774-202">Report Server Provider</span></span>||
|<span data-ttu-id="9b774-203">レポート サーバー レンダリング</span><span class="sxs-lookup"><span data-stu-id="9b774-203">Report Server Rendering</span></span>||
|<span data-ttu-id="9b774-204">レポート サーバー レポート プレビュー</span><span class="sxs-lookup"><span data-stu-id="9b774-204">Report Server Report Preview</span></span>||
|<span data-ttu-id="9b774-205">レポート サーバー リソース ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="9b774-205">Report Server Resource Utility</span></span>|<span data-ttu-id="9b774-206">サンプルのエントリ:</span><span class="sxs-lookup"><span data-stu-id="9b774-206">Sample Entries:</span></span><br /><br /> <span data-ttu-id="9b774-207">MediumReporting Services starting SKU: Evaluation</span><span class="sxs-lookup"><span data-stu-id="9b774-207">MediumReporting Services starting SKU: Evaluation</span></span><br /><br /> <span data-ttu-id="9b774-208">MediumEvaluation コピー: 180 日間残っています</span><span class="sxs-lookup"><span data-stu-id="9b774-208">MediumEvaluation copy: 180 days left</span></span>|
|<span data-ttu-id="9b774-209">レポート サーバー実行中ジョブ</span><span class="sxs-lookup"><span data-stu-id="9b774-209">Report Server Running Jobs</span></span>||
|<span data-ttu-id="9b774-210">レポート サーバー実行中要求</span><span class="sxs-lookup"><span data-stu-id="9b774-210">Report Server Running Requests</span></span>||
|<span data-ttu-id="9b774-211">レポート サーバー スケジュール</span><span class="sxs-lookup"><span data-stu-id="9b774-211">Report Server Schedule</span></span>||
|<span data-ttu-id="9b774-212">レポート サーバー セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9b774-212">Report Server Security</span></span>||
|<span data-ttu-id="9b774-213">レポート サーバー サービス コントローラー</span><span class="sxs-lookup"><span data-stu-id="9b774-213">Report Server Service Controller</span></span>||
|<span data-ttu-id="9b774-214">レポート サーバー セッション</span><span class="sxs-lookup"><span data-stu-id="9b774-214">Report Server Session</span></span>||
|<span data-ttu-id="9b774-215">レポート サーバー サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="9b774-215">Report Server Subscription</span></span>||
|<span data-ttu-id="9b774-216">レポート サーバー WCF ランタイム</span><span class="sxs-lookup"><span data-stu-id="9b774-216">Report Server WCF Runtime</span></span>||
|<span data-ttu-id="9b774-217">レポート サーバー Web サーバー</span><span class="sxs-lookup"><span data-stu-id="9b774-217">Report Server Web Server</span></span>||
|<span data-ttu-id="9b774-218">サービス アプリケーション プロキシ</span><span class="sxs-lookup"><span data-stu-id="9b774-218">Service Application Proxy</span></span>||
|<span data-ttu-id="9b774-219">共有サービス</span><span class="sxs-lookup"><span data-stu-id="9b774-219">Shared Service</span></span>|<span data-ttu-id="9b774-220">サンプルのエントリ:</span><span class="sxs-lookup"><span data-stu-id="9b774-220">Sample entries:</span></span><br /><br /> <span data-ttu-id="9b774-221">MediumUpdating ReportingWebServiceApplication</span><span class="sxs-lookup"><span data-stu-id="9b774-221">MediumUpdating ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="9b774-222">コンテンツ データベースへの MediumGranting アクセス。</span><span class="sxs-lookup"><span data-stu-id="9b774-222">MediumGranting access to content databases.</span></span><br /><br /> <span data-ttu-id="9b774-223">ReportingWebServiceApplication の MediumProvisioning インスタンス</span><span class="sxs-lookup"><span data-stu-id="9b774-223">MediumProvisioning instances for ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="9b774-224">ReportingWebServiceApplication の MediumProcessing サービス アカウントの変更</span><span class="sxs-lookup"><span data-stu-id="9b774-224">MediumProcessing service account change for ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="9b774-225">MediumSetting データベース権限。</span><span class="sxs-lookup"><span data-stu-id="9b774-225">MediumSetting database permissions.</span></span>|

##  <a name="view-a-log-file-with-powershell"></a><a name="bkmk_powershell"></a> <span data-ttu-id="9b774-226">PowerShell でのログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="9b774-226">View a Log file with PowerShell</span></span>
 <span data-ttu-id="9b774-227">![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")PowerShell を使用して、ULS ログ ファイルから [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 関連イベントの一覧を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="9b774-227">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")You can use PowerShell to return a list of the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] related events from a ULS Log file.</span></span> <span data-ttu-id="9b774-228">SharePoint 2010 管理シェルから次のコマンドを入力すると、ULS ログ ファイル UESQL11SPOINT-20110606-1530.log から、"**sql server reporting services**" を含む行のフィルターされたリストが返されます。</span><span class="sxs-lookup"><span data-stu-id="9b774-228">Type the following command from the SharePoint 2010 Management Shell to return a filtered list of rows from the file a ULS log file UESQL11SPOINT-20110606-1530.log, that contain "**sql server reporting services**":</span></span>

```powershell
Get-Content -Path "C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS\UESQL11SPOINT-20110606-1530.log" | Select-String "sql server reporting services"
```

 <span data-ttu-id="9b774-229">ULS ログの読み取りに使用できるツールは他にも多数提供されており、ダウンロードして使用できます。</span><span class="sxs-lookup"><span data-stu-id="9b774-229">There are also many tools you can download which will allow you read ULS logs.</span></span> <span data-ttu-id="9b774-230">たとえば、 [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) や [SharePoint ULS Log Viewer](http://ulsviewer.codeplex.com/workitem/list/basic)などがあります。</span><span class="sxs-lookup"><span data-stu-id="9b774-230">For example, the [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) or [SharePoint ULS Log Viewer](http://ulsviewer.codeplex.com/workitem/list/basic).</span></span> <span data-ttu-id="9b774-231">これらはいずれも、CodePlex から入手できます。</span><span class="sxs-lookup"><span data-stu-id="9b774-231">Both are available on CodePlex.</span></span>

 <span data-ttu-id="9b774-232">PowerShell を使用してログ データを表示する方法の詳細については、「 [診断ログを表示する (SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b774-232">For more information on how to use PowerShell to view log data, see [View diagnostic logs (SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx)</span></span>

##  <a name="trace-log-location"></a><a name="bkmk_trace"></a><span data-ttu-id="9b774-233">トレースログの場所</span><span class="sxs-lookup"><span data-stu-id="9b774-233">Trace Log Location</span></span>
 <span data-ttu-id="9b774-234">トレース ログ ファイルは通常、 **c:\Program Files\Common files\Microsoft Shared\Web Server Extensions\14\logs** フォルダーにありますが、SharePoint サーバーの全体管理の **[診断ログ]** ページから、パスを確認または変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="9b774-234">The Trace Log files are usually found in the folder **c:\Program Files\Common files\Microsoft Shared\Web Server Extensions\14\logs** but you can verify or change the path from the **Diagnostic Logging** page in SharePoint Central Administration.</span></span>

