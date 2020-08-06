---
title: レポートサーバーの実行ログと ExecutionLog3 View |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- logs [Reporting Services], execution
- execution logs [Reporting Services]
ms.assetid: a7ead67d-1404-4e67-97e7-4c7b0d942070
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 868f8497e61c17662cb621850cdb8aee74c82706
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633760"
---
# <a name="report-server-execution-log-and-the-executionlog3-view"></a><span data-ttu-id="36406-102">レポート サーバー実行ログと ExecutionLog3 ビュー</span><span class="sxs-lookup"><span data-stu-id="36406-102">Report Server Execution Log and the ExecutionLog3 View</span></span>
  <span data-ttu-id="36406-103">レポート サーバー実行ログには、サーバー上で実行するレポート、またはネイティブ モードのスケールアウト配置や SharePoint ファーム内の複数のサーバー上で実行するレポートに関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="36406-103">The report server execution log contains information about the reports that execute on the server or on multiple servers in a native mode scale-out deployment or a SharePoint farm.</span></span> <span data-ttu-id="36406-104">レポート実行ログを使用して、レポートを要求する頻度、最も多く使用される出力形式、および各処理フェーズでかかる処理時間 (単位はミリ秒) を調査できます。</span><span class="sxs-lookup"><span data-stu-id="36406-104">You can use the report execution log to find out how often a report is requested, what output formats are used the most, and how many milliseconds of processing time is spent on each processing phase.</span></span> <span data-ttu-id="36406-105">このログには、レポートのデータセット クエリの実行にかかった時間とデータの処理にかかった時間に関する情報が記録されます。</span><span class="sxs-lookup"><span data-stu-id="36406-105">The log contains information on the length of time spent executing a report's dataset query and the time spent processing the data.</span></span> <span data-ttu-id="36406-106">レポート サーバー管理者は、ログの情報を確認して実行時間が長いタスクを特定し、レポート作成者に対して改善の余地があるレポートの領域 (データセットや処理) について提案することができます。</span><span class="sxs-lookup"><span data-stu-id="36406-106">If you are a report server administrator, you can review the log information and identify long running tasks and make suggestions to the report authors on the areas of the report (dataset or processing) they may be able to improve.</span></span>  
  
 <span data-ttu-id="36406-107">SharePoint モード用に構成されたレポート サーバーでは、SharePoint ULS ログも利用できます。</span><span class="sxs-lookup"><span data-stu-id="36406-107">Report servers configured for SharePoint mode, can also utilize the SharePoint ULS logs.</span></span> <span data-ttu-id="36406-108">詳細については、「 [SharePoint トレース ログの Reporting Services イベントをオンにする (ULS)](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)</span><span class="sxs-lookup"><span data-stu-id="36406-108">For more information, see [Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)</span></span>  
  
##  <a name="viewing-log-information"></a><a name="bkmk_top"></a> <span data-ttu-id="36406-109">ログ情報の表示</span><span class="sxs-lookup"><span data-stu-id="36406-109">Viewing Log Information</span></span>  
 <span data-ttu-id="36406-110">レポート サーバーは、レポート実行に関するデータのログを内部データベース テーブルに記録します。</span><span class="sxs-lookup"><span data-stu-id="36406-110">The report server execution logs data about report execution into an internal database table.</span></span> <span data-ttu-id="36406-111">このテーブルの情報は SQL Server ビューで参照できます。</span><span class="sxs-lookup"><span data-stu-id="36406-111">The information from the table is available from SQL Server views.</span></span>  
  
 <span data-ttu-id="36406-112">レポート サーバー実行ログはレポート サーバー データベースに格納されます。このデータベースの既定の名前は **ReportServer**です。</span><span class="sxs-lookup"><span data-stu-id="36406-112">The report execution log is stored in the report server database that by default is named **ReportServer**.</span></span> <span data-ttu-id="36406-113">実行ログの情報は、SQL ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="36406-113">The SQL views provide the execution log information.</span></span> <span data-ttu-id="36406-114">より新しいリリースで追加された "2" および "3" のビューには、新しいフィールドが追加されています。また、以前のリリースよりもわかりやすい名前に変更されたフィールドもあります。</span><span class="sxs-lookup"><span data-stu-id="36406-114">The "2" and "3" views were added in more recent releases and contain new fields or they contain fields with friendlier names than the previous releases.</span></span> <span data-ttu-id="36406-115">古いビューも引き続き利用できるため、それらに依存するカスタム アプリケーションへの影響はありません。</span><span class="sxs-lookup"><span data-stu-id="36406-115">The older views remain in the product so custom applications that depend on them are not impacted.</span></span> <span data-ttu-id="36406-116">ExecutionLog などの古いビューに依存していない場合は、最新のビューである ExecutionLog**3**を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="36406-116">If you do not have a dependence on an older view, for example ExecutionLog, it is recommended you use the most recent view, ExecutionLog**3**.</span></span>  
  
 <span data-ttu-id="36406-117">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="36406-117">In this topic:</span></span>  
  
-   [<span data-ttu-id="36406-118">SharePoint モードのレポート サーバーの構成設定</span><span class="sxs-lookup"><span data-stu-id="36406-118">Configuration Settings for a SharePoint mode Report Server</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="36406-119">ネイティブ モードのレポート サーバーの構成設定</span><span class="sxs-lookup"><span data-stu-id="36406-119">Configuration Settings for a Native Mode Report Server</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="36406-120">ログのフィールド (ExecutionLog3)</span><span class="sxs-lookup"><span data-stu-id="36406-120">Log Fields (ExecutionLog3)</span></span>](#bkmk_executionlog3)  
  
-   [<span data-ttu-id="36406-121">AdditionalInfo フィールド</span><span class="sxs-lookup"><span data-stu-id="36406-121">The AdditionalInfo Field</span></span>](#bkmk_additionalinfo)  
  
-   [<span data-ttu-id="36406-122">ログのフィールド (ExecutionLog2)</span><span class="sxs-lookup"><span data-stu-id="36406-122">Log Fields (ExecutionLog2)</span></span>](#bkmk_executionlog2)  
  
-   [<span data-ttu-id="36406-123">ログのフィールド (ExecutionLog)</span><span class="sxs-lookup"><span data-stu-id="36406-123">Log Fields (ExecutionLog)</span></span>](#bkmk_executionlog)  
  
##  <a name="configuration-settings-for-a-sharepoint-mode-report-server"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="36406-124">SharePoint モードのレポート サーバーの構成設定</span><span class="sxs-lookup"><span data-stu-id="36406-124">Configuration Settings for a SharePoint mode Report Server</span></span>  
 <span data-ttu-id="36406-125">レポート実行のログ記録の有効と無効の切り替えは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションのシステム設定で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="36406-125">You can turn report execution logging on or off from the system settings of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
 <span data-ttu-id="36406-126">既定では、ログ エントリが 60 日間保持されます。</span><span class="sxs-lookup"><span data-stu-id="36406-126">By default, log entries are kept 60 days.</span></span> <span data-ttu-id="36406-127">この期間を超えるエントリは、毎日午前 2 時に</span><span class="sxs-lookup"><span data-stu-id="36406-127">Entries that exceed this date are removed at 2:00 A.M.</span></span> <span data-ttu-id="36406-128">削除されます。</span><span class="sxs-lookup"><span data-stu-id="36406-128">every day.</span></span> <span data-ttu-id="36406-129">長期間使用しているインストールでは、使用可能な情報は常に 60 日分のみになります。</span><span class="sxs-lookup"><span data-stu-id="36406-129">On a mature installation, only 60 days of information will be available at any given time.</span></span>  
  
 <span data-ttu-id="36406-130">記録される行数またはエントリの種類に制限を設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="36406-130">You cannot set limits on the number of rows or on the type of entries that are logged.</span></span>  
  
 <span data-ttu-id="36406-131">**実行のログ記録を有効にするには**</span><span class="sxs-lookup"><span data-stu-id="36406-131">**To enable execution logging:**</span></span>  
  
1.  <span data-ttu-id="36406-132">SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36406-132">From SharePoint Central Administration, click **Manage service applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="36406-133">構成する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36406-133">Click the name of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application you want to configure.</span></span>  
  
3.  <span data-ttu-id="36406-134">**[システム設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36406-134">Click **System Settings**.</span></span>  
  
4.  <span data-ttu-id="36406-135">**[ログ記録]** セクションで **[実行のログ記録を有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="36406-135">Select **Enable Execution Logging** in the **Logging** section.</span></span>  
  
5.  <span data-ttu-id="36406-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36406-136">Click **OK**.</span></span>  
  
 <span data-ttu-id="36406-137">**詳細ログを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="36406-137">**To enable verbose logging:**</span></span>  
  
 <span data-ttu-id="36406-138">前の手順の説明に従ってログ記録を有効にしてから、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36406-138">You need to enable logging as described in the previous steps and then complete the following:</span></span>  
  
1.  <span data-ttu-id="36406-139">**サービス アプリケーションの** [システム設定] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ページで、 **[ユーザー定義]** セクションを探します。</span><span class="sxs-lookup"><span data-stu-id="36406-139">From the **System Settings** page of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] services application, find the **User-defined** section.</span></span>  
  
2.  <span data-ttu-id="36406-140">**ExecutionLogLevel** を **verbose**に変更します。</span><span class="sxs-lookup"><span data-stu-id="36406-140">Change the **ExecutionLogLevel** to **verbose**.</span></span> <span data-ttu-id="36406-141">このフィールドはテキスト入力フィールドで、有効な値は **verbose** と **normal**の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="36406-141">This field is a text entry field and the two possible values are **verbose** and **normal**.</span></span>  
  
##  <a name="configuration-settings-for-a-native-mode-report-server"></a><a name="bkmk_native"></a> <span data-ttu-id="36406-142">ネイティブ モードのレポート サーバーの構成設定</span><span class="sxs-lookup"><span data-stu-id="36406-142">Configuration Settings for a Native Mode Report Server</span></span>  
 <span data-ttu-id="36406-143">レポート実行のログ記録の有効と無効の切り替えは、SQL Server Management Studio の [サーバーのプロパティ] ページで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="36406-143">You can turn report execution logging on or off from the Server Properties page in SQL Server Management Studio.</span></span> <span data-ttu-id="36406-144">詳細プロパティの **EnableExecutionLogging** を使用します。</span><span class="sxs-lookup"><span data-stu-id="36406-144">The **EnableExecutionLogging** is and Advanced property.</span></span>  
  
 <span data-ttu-id="36406-145">既定では、ログ エントリが 60 日間保持されます。</span><span class="sxs-lookup"><span data-stu-id="36406-145">By default, log entries are kept 60 days.</span></span> <span data-ttu-id="36406-146">この期間を超えるエントリは、毎日午前 2 時に</span><span class="sxs-lookup"><span data-stu-id="36406-146">Entries that exceed this date are removed at 2:00 A.M.</span></span> <span data-ttu-id="36406-147">削除されます。</span><span class="sxs-lookup"><span data-stu-id="36406-147">every day.</span></span> <span data-ttu-id="36406-148">長期間使用しているインストールでは、使用可能な情報は常に 60 日分のみになります。</span><span class="sxs-lookup"><span data-stu-id="36406-148">On a mature installation, only 60 days of information will be available at any given time.</span></span>  
  
 <span data-ttu-id="36406-149">記録される行数またはエントリの種類に制限を設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="36406-149">You cannot set limits on the number of rows or on the type of entries that are logged.</span></span>  
  
 <span data-ttu-id="36406-150">**実行のログ記録を有効にするには**</span><span class="sxs-lookup"><span data-stu-id="36406-150">**To enable execution logging:**</span></span>  
  
1.  <span data-ttu-id="36406-151">SQL Server Management Studio を管理者特権で起動します。</span><span class="sxs-lookup"><span data-stu-id="36406-151">Start SQL Server Management Studio with administrative privileges.</span></span> <span data-ttu-id="36406-152">たとえば、Management Studio のアイコンを右クリックし、[管理者として実行] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36406-152">For example right-click the Management Studio icon and click 'Run as administrator'.</span></span>  
  
2.  <span data-ttu-id="36406-153">目的のレポート サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="36406-153">Connect to the desired report server.</span></span>  
  
3.  <span data-ttu-id="36406-154">サーバー名を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36406-154">Right-click the server name and click **Properties**.</span></span> <span data-ttu-id="36406-155">[プロパティ] オプションが無効になっている場合は、SQL Server Management Studio を管理者特権で実行したことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="36406-155">If the Properties option is disabled, verify you ran SQL Server Management Studio with administrative privileges.</span></span>  
  
4.  <span data-ttu-id="36406-156">**[ログ記録]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36406-156">Click the **Logging** page.</span></span>  
  
5.  <span data-ttu-id="36406-157">**[レポート実行のログ記録を有効にする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="36406-157">Select **Enable report execution Logging**.</span></span>  
  
 <span data-ttu-id="36406-158">**詳細ログを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="36406-158">**To enable verbose logging:**</span></span>  
  
 <span data-ttu-id="36406-159">前の手順の説明に従ってログ記録を有効にしてから、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36406-159">You need to enable logging as described in the previous steps and then complete the following:</span></span>  
  
1.  <span data-ttu-id="36406-160">**[サーバーのプロパティ]** ダイアログ ボックスで、 **[詳細設定]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36406-160">From the **Server Properties** dialog, click the **Advanced** page.</span></span>  
  
2.  <span data-ttu-id="36406-161">**[ユーザー定義]** セクションで、 **ExecutionLogLevel** を **verbose**に変更します。</span><span class="sxs-lookup"><span data-stu-id="36406-161">In the **User-defined** section, change the **ExecutionLogLevel** to **verbose**.</span></span> <span data-ttu-id="36406-162">このフィールドはテキスト入力フィールドで、有効な値は **verbose** と **normal**の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="36406-162">This field is a text entry field and the two possible values are **verbose** and **normal**.</span></span>  
  
##  <a name="log-fields-executionlog3"></a><a name="bkmk_executionlog3"></a> <span data-ttu-id="36406-163">ログのフィールド (ExecutionLog3)</span><span class="sxs-lookup"><span data-stu-id="36406-163">Log Fields (ExecutionLog3)</span></span>  
 <span data-ttu-id="36406-164">このビューの XML ベースの **AdditionalInfo** 列内に追加のパフォーマンス診断ノードが追加されました。</span><span class="sxs-lookup"><span data-stu-id="36406-164">This view added additional performance diagnostics node inside the XML based **AdditionalInfo** column.</span></span> <span data-ttu-id="36406-165">AdditionalInfo 列には、他の 1 つ以上の情報のフィールドから成る XML 構造が格納されています。</span><span class="sxs-lookup"><span data-stu-id="36406-165">The AdditionalInfo column contains an XML structure of 1 to many additional fields of information.</span></span> <span data-ttu-id="36406-166">ExecutionLog3 ビューから行を取得する Transact-SQL ステートメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="36406-166">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog3.</span></span> <span data-ttu-id="36406-167">この例では、レポート サーバー データベースの名前が **ReportServer**であることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="36406-167">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog3 order by TimeStart DESC  
```  
  
 <span data-ttu-id="36406-168">次の表に、レポート実行ログに取得されるデータを示します。</span><span class="sxs-lookup"><span data-stu-id="36406-168">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="36406-169">列</span><span class="sxs-lookup"><span data-stu-id="36406-169">Column</span></span>|<span data-ttu-id="36406-170">説明</span><span class="sxs-lookup"><span data-stu-id="36406-170">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="36406-171">InstanceName</span><span class="sxs-lookup"><span data-stu-id="36406-171">InstanceName</span></span>|<span data-ttu-id="36406-172">要求を処理したレポート サーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="36406-172">Name of the report server instance that handled the request.</span></span> <span data-ttu-id="36406-173">レポート サーバーが複数ある環境では、InstanceName のディストリビューションを分析することで、ネットワーク負荷分散を監視し、要求がレポート サーバー間で想定どおりに分散されているかどうかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="36406-173">If your environment has more than one report server, you can analyze the InstanceName distribution to monitor and determine if your network-load balancer distributes requests across report servers as expected.</span></span>|  
|<span data-ttu-id="36406-174">ItemPath</span><span class="sxs-lookup"><span data-stu-id="36406-174">ItemPath</span></span>|<span data-ttu-id="36406-175">レポートまたはレポート アイテムの格納場所のパス。</span><span class="sxs-lookup"><span data-stu-id="36406-175">Path of where a report or report item is stored.</span></span>|  
|<span data-ttu-id="36406-176">UserName</span><span class="sxs-lookup"><span data-stu-id="36406-176">UserName</span></span>|<span data-ttu-id="36406-177">ユーザー識別子。</span><span class="sxs-lookup"><span data-stu-id="36406-177">User identifier.</span></span>|  
|<span data-ttu-id="36406-178">[ExecutionID]</span><span class="sxs-lookup"><span data-stu-id="36406-178">ExecutionID</span></span>|<span data-ttu-id="36406-179">要求に関連付けられた内部識別子。</span><span class="sxs-lookup"><span data-stu-id="36406-179">The internal identifier associated with a request.</span></span> <span data-ttu-id="36406-180">同じユーザー セッションの要求は、同じ実行 ID を共有します。</span><span class="sxs-lookup"><span data-stu-id="36406-180">Requests on the same user sessions share the same execution id.</span></span>|  
|<span data-ttu-id="36406-181">RequestType</span><span class="sxs-lookup"><span data-stu-id="36406-181">RequestType</span></span>|<span data-ttu-id="36406-182">有効値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="36406-182">Possible Values:</span></span><br /><span data-ttu-id="36406-183">**対話**</span><span class="sxs-lookup"><span data-stu-id="36406-183">**Interactive**</span></span><br /><span data-ttu-id="36406-184">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="36406-184">**Subscription**</span></span><br /><br /> <br /><br /> <span data-ttu-id="36406-185">RequestType=Subscription でフィルター処理したログ データを TimeStart で並べ替えて分析すると、サブスクリプションが集中している時間が見つかることがあります。この情報を基に、レポートのサブスクリプションの一部を別の時間に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="36406-185">Analyzing log data filtered by RequestType=Subscription and sorted by TimeStart may reveal periods of heavy subscription usage and you may want to modify some of the report subscriptions to a different time.</span></span>|  
|<span data-ttu-id="36406-186">Format</span><span class="sxs-lookup"><span data-stu-id="36406-186">Format</span></span>|<span data-ttu-id="36406-187">表示形式。</span><span class="sxs-lookup"><span data-stu-id="36406-187">Rendering format.</span></span>|  
|<span data-ttu-id="36406-188">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36406-188">Parameters</span></span>|<span data-ttu-id="36406-189">レポート実行に使用するパラメーター値。</span><span class="sxs-lookup"><span data-stu-id="36406-189">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="36406-190">ItemAction</span><span class="sxs-lookup"><span data-stu-id="36406-190">ItemAction</span></span>|<span data-ttu-id="36406-191">指定できる値</span><span class="sxs-lookup"><span data-stu-id="36406-191">Possible values:</span></span><br /><br /> <span data-ttu-id="36406-192">**レンダリング**</span><span class="sxs-lookup"><span data-stu-id="36406-192">**Render**</span></span><br /><br /> <span data-ttu-id="36406-193">**Sort**</span><span class="sxs-lookup"><span data-stu-id="36406-193">**Sort**</span></span><br /><br /> <span data-ttu-id="36406-194">**BookMarkNavigation**</span><span class="sxs-lookup"><span data-stu-id="36406-194">**BookMarkNavigation**</span></span><br /><br /> <span data-ttu-id="36406-195">**DocumentNavigation**</span><span class="sxs-lookup"><span data-stu-id="36406-195">**DocumentNavigation**</span></span><br /><br /> <span data-ttu-id="36406-196">**GetDocumentMap**</span><span class="sxs-lookup"><span data-stu-id="36406-196">**GetDocumentMap**</span></span><br /><br /> <span data-ttu-id="36406-197">**Findstring**</span><span class="sxs-lookup"><span data-stu-id="36406-197">**Findstring**</span></span><br /><br /> <span data-ttu-id="36406-198">**おい**</span><span class="sxs-lookup"><span data-stu-id="36406-198">**Execute**</span></span><br /><br /> <span data-ttu-id="36406-199">**RenderEdit**</span><span class="sxs-lookup"><span data-stu-id="36406-199">**RenderEdit**</span></span>|  
|<span data-ttu-id="36406-200">TimeStart</span><span class="sxs-lookup"><span data-stu-id="36406-200">TimeStart</span></span>|<span data-ttu-id="36406-201">レポート処理の期間を示す開始時刻と終了時刻。</span><span class="sxs-lookup"><span data-stu-id="36406-201">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="36406-202">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="36406-202">TimeEnd</span></span>||  
|<span data-ttu-id="36406-203">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="36406-203">TimeDataRetrieval</span></span>|<span data-ttu-id="36406-204">データの取得にかかった時間 (単位はミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="36406-204">Number of milliseconds spent retrieving the data.</span></span>|  
|<span data-ttu-id="36406-205">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="36406-205">TimeProcessing</span></span>|<span data-ttu-id="36406-206">レポートの処理にかかった時間 (単位はミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="36406-206">Number of milliseconds spent processing the report.</span></span>|  
|<span data-ttu-id="36406-207">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="36406-207">TimeRendering</span></span>|<span data-ttu-id="36406-208">レポートの表示にかかった時間 (単位はミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="36406-208">Number of milliseconds spent rendering the report.</span></span>|  
|<span data-ttu-id="36406-209">source</span><span class="sxs-lookup"><span data-stu-id="36406-209">Source</span></span>|<span data-ttu-id="36406-210">レポート実行のソース。</span><span class="sxs-lookup"><span data-stu-id="36406-210">Source of the report execution.</span></span> <span data-ttu-id="36406-211">指定できる値</span><span class="sxs-lookup"><span data-stu-id="36406-211">Possible values:</span></span><br /><br /> <span data-ttu-id="36406-212">**ライブ**</span><span class="sxs-lookup"><span data-stu-id="36406-212">**Live**</span></span><br /><br /> <span data-ttu-id="36406-213">**Cache**: キャッシュされた実行を示します。たとえば、データセットクエリはライブでは実行されません。</span><span class="sxs-lookup"><span data-stu-id="36406-213">**Cache**: Indicates a cached execution, for example, dataset queries are not executed live.</span></span><br /><br /> <span data-ttu-id="36406-214">**スナップショット**</span><span class="sxs-lookup"><span data-stu-id="36406-214">**Snapshot**</span></span><br /><br /> <span data-ttu-id="36406-215">**HISTORY**</span><span class="sxs-lookup"><span data-stu-id="36406-215">**History**</span></span><br /><br /> <span data-ttu-id="36406-216">**アドホック**: ドリルスルーレポートに基づいて動的に生成されたレポートモデル、または処理と表示のためにレポートサーバーを使用しているクライアントでプレビューされているレポートビルダーレポートのいずれかを示します。</span><span class="sxs-lookup"><span data-stu-id="36406-216">**AdHoc** : Indicates either a dynamically generated report model based drill through report, or a Report Builder report that is previewed on a client utilizing the report server for processing and rendering.</span></span><br /><br /> <span data-ttu-id="36406-217">**Session**: 既に確立されたセッション内のフォローアップ要求を示します。</span><span class="sxs-lookup"><span data-stu-id="36406-217">**Session**: Indicates a follow up request within an already established session.</span></span>  <span data-ttu-id="36406-218">たとえば、最初の要求がページ 1 の表示であり、フォローアップ要求は現在のセッション状態での Excel へのエクスポートである場合などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="36406-218">For example the initial request is to view page 1, and the follow up request is to export to Excel with the current session state.</span></span><br /><br /> <span data-ttu-id="36406-219">**Rdce**: レポート定義のカスタマイズ拡張機能を示します。</span><span class="sxs-lookup"><span data-stu-id="36406-219">**Rdce**:  Indicates a Report Definition Customization Extension.</span></span> <span data-ttu-id="36406-220">RDCE カスタム拡張機能では、レポート実行時にレポート定義を処理エンジンに渡す前に動的にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="36406-220">An RDCE custom extension can dynamically customize a report definition before it is passed to the processing engine upon report execution.</span></span>|  
|<span data-ttu-id="36406-221">Status</span><span class="sxs-lookup"><span data-stu-id="36406-221">Status</span></span>|<span data-ttu-id="36406-222">状態 (rsSuccess またはエラー コード。複数のエラーが発生する場合は、最初のエラーのみ記録)。</span><span class="sxs-lookup"><span data-stu-id="36406-222">Status (either rsSuccess or an error code; if multiple errors occur, only the first error is recorded).</span></span>|  
|<span data-ttu-id="36406-223">ByteCount</span><span class="sxs-lookup"><span data-stu-id="36406-223">ByteCount</span></span>|<span data-ttu-id="36406-224">表示されるレポートのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="36406-224">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="36406-225">RowCount</span><span class="sxs-lookup"><span data-stu-id="36406-225">RowCount</span></span>|<span data-ttu-id="36406-226">クエリから返される行数。</span><span class="sxs-lookup"><span data-stu-id="36406-226">Number of rows returned from queries.</span></span>|  
|<span data-ttu-id="36406-227">AdditionalInfo:</span><span class="sxs-lookup"><span data-stu-id="36406-227">AdditionalInfo</span></span>|<span data-ttu-id="36406-228">実行に関する追加情報を格納する XML プロパティ バッグ。</span><span class="sxs-lookup"><span data-stu-id="36406-228">An XML property bag containing additional information about the execution.</span></span> <span data-ttu-id="36406-229">内容は行ごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="36406-229">The contents can be different for each row.</span></span>|  
  
##  <a name="the-additionalinfo-field"></a><a name="bkmk_additionalinfo"></a> <span data-ttu-id="36406-230">AdditionalInfo フィールド</span><span class="sxs-lookup"><span data-stu-id="36406-230">The AdditionalInfo Field</span></span>  
 <span data-ttu-id="36406-231">AdditionalInfo フィールドは、実行に関する追加情報を格納する XML プロパティ バッグ (構造) です。</span><span class="sxs-lookup"><span data-stu-id="36406-231">The AdditionalInfo field is an XML property bag or structure containing additional information about the execution.</span></span> <span data-ttu-id="36406-232">内容はログの行ごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="36406-232">The contents can be different for each row in the log.</span></span>  
  
 <span data-ttu-id="36406-233">次の表は、標準と詳細の両方のログの AddtionalInfo フィールドの内容の例です。</span><span class="sxs-lookup"><span data-stu-id="36406-233">The following tables are examples  of the contents of the AddtionalInfo field for both standard and verbose logging:</span></span>  
  
 <span data-ttu-id="36406-234">**AddtionalInfo の標準ログの例**</span><span class="sxs-lookup"><span data-stu-id="36406-234">**Standard logging example of AddtionalInfo**</span></span>  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>147</ConnectionOpenTime>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>642</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>63</ExecuteReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>157</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>60</ExecuteReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 <span data-ttu-id="36406-235">**AdditionalInfo の詳細ログの例**</span><span class="sxs-lookup"><span data-stu-id="36406-235">**Verbose logging example of AdditionalInfo**</span></span>  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>127</ConnectionOpenTime>  
      <DataSource>  
        <Name>DataSource1</Name>  
        <DataExtension>SQL</DataExtension>  
      </DataSource>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>33</ExecuteReaderTime>  
          <DataReaderMappingTime>30</DataReaderMappingTime>  
          <DisposeDataReaderTime>1</DisposeDataReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>1</ExecuteReaderTime>  
          <DataReaderMappingTime>0</DataReaderMappingTime>  
          <DisposeDataReaderTime>0</DisposeDataReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 <span data-ttu-id="36406-236">次に、AdditionalInfo フィールドに表示されるいくつかのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="36406-236">The following describes some of the properties you will see in the AdditionalInfo field:</span></span>  
  
-   <span data-ttu-id="36406-237">**Processingengine**: 1 = SQL Server 2005、2 = 新しいオンデマンド処理エンジン。</span><span class="sxs-lookup"><span data-stu-id="36406-237">**ProcessingEngine**: 1=SQL Server 2005, 2=The new On-demand Processing Engine.</span></span> <span data-ttu-id="36406-238">ほとんどのレポートでこの値が 1 になっている場合は、レポートを設計し直す方法を調べて、効率が向上した新しいオンデマンド処理エンジンを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="36406-238">If a majority of your reports are still showing the value of 1, you may investigate how to redesign them so they utilize the newer and more efficient on-demand processing engine.</span></span>  
  
     `<ProcessingEngine>2</ProcessingEngine>`  
  
-   <span data-ttu-id="36406-239">スケーリング可能な**時間**: 処理エンジンでスケール関連の操作を実行するために費やされた時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="36406-239">**ScalabilityTime**: The number of milliseconds spent performing scale related operations in the processing engine.</span></span> <span data-ttu-id="36406-240">値が 0 の場合は、スケール操作に特に時間はかからず、要求時にメモリ不足にならなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="36406-240">A value of 0 indicates that no additional time was spent on scale operations and a 0 also indicates the request was not under memory pressure.</span></span>  
  
    ```  
    <ScalabilityTime>  
        <Processing>0</Processing>  
    </ScalabilityTime>  
    ```  
  
-   <span data-ttu-id="36406-241">**EstimatedMemoryUsageKB**: 特定の要求中に各コンポーネントによって消費されるメモリのピーク量の推定値。</span><span class="sxs-lookup"><span data-stu-id="36406-241">**EstimatedMemoryUsageKB**: An estimate of the peak amount of memory, in kilobytes, consumed by each component during a particular request.</span></span>  
  
    ```  
    <EstimatedMemoryUsageKB>  
        <Processing>38</Processing>  
    </EstimatedMemoryUsageKB>  
    ```  
  
-   <span data-ttu-id="36406-242">**Dataextension**: レポートで使用されるデータ拡張機能またはデータソースの種類。</span><span class="sxs-lookup"><span data-stu-id="36406-242">**DataExtension**: The types of data extensions or data sources used in the report.</span></span> <span data-ttu-id="36406-243">数値は、そのデータ ソースが使用されている回数を示します。</span><span class="sxs-lookup"><span data-stu-id="36406-243">The number is a count of the number of occurrences of the particular data source.</span></span>  
  
    ```  
    <DataExtension>  
       <DAX>2</DAX>  
    </DataExtension>  
    ```  
  
-   <span data-ttu-id="36406-244">**Externalimages**値はミリ秒にあります。</span><span class="sxs-lookup"><span data-stu-id="36406-244">**ExternalImages**The value is in miliseconds.</span></span> <span data-ttu-id="36406-245">このデータはパフォーマンスに関する問題の診断に使用できます。</span><span class="sxs-lookup"><span data-stu-id="36406-245">This data can be used to diagnose performance issues.</span></span> <span data-ttu-id="36406-246">外部 Web サーバーからイメージを取得するのに時間がかかり、レポートの実行全体が遅くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="36406-246">The time needed to retrieve images from an external webserver may slow the overall report execution.</span></span> <span data-ttu-id="36406-247">で追加されました [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="36406-247">Added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
    ```  
    <ExternalImages>  
        <Count>3</Count>  
        <ByteCount>9268</ByteCount>  
        <ResourceFetchTime>9</ResourceFetchTime>  
    </ExternalImages>  
    ```  
  
-   <span data-ttu-id="36406-248">**Connections**: 複数の平準化構造。</span><span class="sxs-lookup"><span data-stu-id="36406-248">**Connections**: A multi-leveled structure.</span></span> <span data-ttu-id="36406-249">で追加されました [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="36406-249">Added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
    ```  
    <Connections>  
        <Connection>  
          <ConnectionOpenTime>127</ConnectionOpenTime>  
          <DataSource>  
            <Name>DataSource1</Name>  
            <DataExtension>SQL</DataExtension>  
          </DataSource>  
          <DataSets>  
            <DataSet>  
              <Name>DataSet1</Name>  
              <RowsRead>16</RowsRead>  
              <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>33</ExecuteReaderTime>  
              <DataReaderMappingTime>30</DataReaderMappingTime>  
              <DisposeDataReaderTime>1</DisposeDataReaderTime>  
            </DataSet>  
            <DataSet>  
              <Name>DataSet2</Name>  
              <RowsRead>3</RowsRead>  
              <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>1</ExecuteReaderTime>  
              <DataReaderMappingTime>0</DataReaderMappingTime>  
              <DisposeDataReaderTime>0</DisposeDataReaderTime>  
            </DataSet>  
          </DataSets>  
        </Connection>  
    </Connections>  
  
    ```  
  
##  <a name="log-fields-executionlog2"></a><a name="bkmk_executionlog2"></a> <span data-ttu-id="36406-250">ログのフィールド (ExecutionLog2)</span><span class="sxs-lookup"><span data-stu-id="36406-250">Log Fields (ExecutionLog2)</span></span>  
 <span data-ttu-id="36406-251">このビューにはフィールドがいくつか追加されたほか、一部のフィールドの名前が変更されています。</span><span class="sxs-lookup"><span data-stu-id="36406-251">This view added a few new fields and renamed a few others.</span></span> <span data-ttu-id="36406-252">ExecutionLog2 ビューから行を取得する Transact-SQL ステートメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="36406-252">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog2.</span></span> <span data-ttu-id="36406-253">この例では、レポート サーバー データベースの名前が **ReportServer**であることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="36406-253">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog2 order by TimeStart DESC  
```  
  
 <span data-ttu-id="36406-254">次の表に、レポート実行ログに取得されるデータを示します。</span><span class="sxs-lookup"><span data-stu-id="36406-254">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="36406-255">列</span><span class="sxs-lookup"><span data-stu-id="36406-255">Column</span></span>|<span data-ttu-id="36406-256">説明</span><span class="sxs-lookup"><span data-stu-id="36406-256">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="36406-257">InstanceName</span><span class="sxs-lookup"><span data-stu-id="36406-257">InstanceName</span></span>|<span data-ttu-id="36406-258">要求を処理したレポート サーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="36406-258">Name of the report server instance that handled the request.</span></span>|  
|<span data-ttu-id="36406-259">ReportPath</span><span class="sxs-lookup"><span data-stu-id="36406-259">ReportPath</span></span>|<span data-ttu-id="36406-260">レポートのパス構造。</span><span class="sxs-lookup"><span data-stu-id="36406-260">The path structure to the report.</span></span>  <span data-ttu-id="36406-261">たとえば、"test" というレポートがレポート マネージャーのルート フォルダーにある場合、ReportPath は "/test" となります。</span><span class="sxs-lookup"><span data-stu-id="36406-261">For example a report named "test" which is the in root folder in Report Manager, would have a ReportPath of "/test".</span></span><br /><br /> <span data-ttu-id="36406-262">"test" という名前のレポートがレポート マネージャー "samples" フォルダーに保存されている場合は、ReportPath は "/Samples/test/" となります。</span><span class="sxs-lookup"><span data-stu-id="36406-262">A report named "test" that is saved in the folder "samples" on Report Manager , will have a ReportPath of "/Samples/test/"</span></span>|  
|<span data-ttu-id="36406-263">UserName</span><span class="sxs-lookup"><span data-stu-id="36406-263">UserName</span></span>|<span data-ttu-id="36406-264">ユーザー識別子。</span><span class="sxs-lookup"><span data-stu-id="36406-264">User identifier.</span></span>|  
|<span data-ttu-id="36406-265">[ExecutionID]</span><span class="sxs-lookup"><span data-stu-id="36406-265">ExecutionID</span></span>||  
|<span data-ttu-id="36406-266">RequestType</span><span class="sxs-lookup"><span data-stu-id="36406-266">RequestType</span></span>|<span data-ttu-id="36406-267">要求の種類 (ユーザーまたはシステム)。</span><span class="sxs-lookup"><span data-stu-id="36406-267">Request type (either user or system).</span></span>|  
|<span data-ttu-id="36406-268">書式</span><span class="sxs-lookup"><span data-stu-id="36406-268">Format</span></span>|<span data-ttu-id="36406-269">表示形式。</span><span class="sxs-lookup"><span data-stu-id="36406-269">Rendering format.</span></span>|  
|<span data-ttu-id="36406-270">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36406-270">Parameters</span></span>|<span data-ttu-id="36406-271">レポート実行に使用するパラメーター値。</span><span class="sxs-lookup"><span data-stu-id="36406-271">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="36406-272">ReportAction</span><span class="sxs-lookup"><span data-stu-id="36406-272">ReportAction</span></span>|<span data-ttu-id="36406-273">有効値: Render、Sort、BookMarkNavigation、DocumentNavigation、GetDocumentMap、Findstring。</span><span class="sxs-lookup"><span data-stu-id="36406-273">Possible values: Render, Sort, BookMarkNavigation, DocumentNavigation, GetDocumentMap, Findstring</span></span>|  
|<span data-ttu-id="36406-274">TimeStart</span><span class="sxs-lookup"><span data-stu-id="36406-274">TimeStart</span></span>|<span data-ttu-id="36406-275">レポート処理の期間を示す開始時刻と終了時刻。</span><span class="sxs-lookup"><span data-stu-id="36406-275">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="36406-276">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="36406-276">TimeEnd</span></span>||  
|<span data-ttu-id="36406-277">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="36406-277">TimeDataRetrieval</span></span>|<span data-ttu-id="36406-278">データの取得、レポートの処理、レポートの表示にかかった時間 (単位はミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="36406-278">Number of milliseconds spent retrieving the data, processing the report, and rendering the report.</span></span>|  
|<span data-ttu-id="36406-279">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="36406-279">TimeProcessing</span></span>||  
|<span data-ttu-id="36406-280">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="36406-280">TimeRendering</span></span>||  
|<span data-ttu-id="36406-281">source</span><span class="sxs-lookup"><span data-stu-id="36406-281">Source</span></span>|<span data-ttu-id="36406-282">レポート実行のソース (1 = 実行中、2 = キャッシュ、3 = スナップショット、4 = 履歴)。</span><span class="sxs-lookup"><span data-stu-id="36406-282">Source of the report execution (1=Live, 2=Cache, 3=Snapshot, 4=History).</span></span>|  
|<span data-ttu-id="36406-283">Status</span><span class="sxs-lookup"><span data-stu-id="36406-283">Status</span></span>|<span data-ttu-id="36406-284">状態 (rsSuccess またはエラー コード。複数のエラーが発生する場合は、最初のエラーのみ記録)。</span><span class="sxs-lookup"><span data-stu-id="36406-284">Status (either rsSuccess or an error code; if multiple errors occur, only the first error is recorded).</span></span>|  
|<span data-ttu-id="36406-285">ByteCount</span><span class="sxs-lookup"><span data-stu-id="36406-285">ByteCount</span></span>|<span data-ttu-id="36406-286">表示されるレポートのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="36406-286">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="36406-287">RowCount</span><span class="sxs-lookup"><span data-stu-id="36406-287">RowCount</span></span>|<span data-ttu-id="36406-288">クエリから返される行数。</span><span class="sxs-lookup"><span data-stu-id="36406-288">Number of rows returned from queries.</span></span>|  
|<span data-ttu-id="36406-289">AdditionalInfo</span><span class="sxs-lookup"><span data-stu-id="36406-289">AdditionalInfo</span></span>|<span data-ttu-id="36406-290">実行に関する追加情報を格納する XML プロパティ バッグ。</span><span class="sxs-lookup"><span data-stu-id="36406-290">An XML property bag containing additional information about the execution.</span></span>|  
  
##  <a name="log-fields-executionlog"></a><a name="bkmk_executionlog"></a> <span data-ttu-id="36406-291">ログのフィールド (ExecutionLog)</span><span class="sxs-lookup"><span data-stu-id="36406-291">Log Fields (ExecutionLog)</span></span>  
 <span data-ttu-id="36406-292">ExecutionLog ビューから行を取得する Transact-SQL ステートメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="36406-292">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog.</span></span> <span data-ttu-id="36406-293">この例では、レポート サーバー データベースの名前が **ReportServer**であることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="36406-293">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog order by TimeStart DESC  
  
```  
  
 <span data-ttu-id="36406-294">次の表に、レポート実行ログに取得されるデータを示します。</span><span class="sxs-lookup"><span data-stu-id="36406-294">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="36406-295">列</span><span class="sxs-lookup"><span data-stu-id="36406-295">Column</span></span>|<span data-ttu-id="36406-296">説明</span><span class="sxs-lookup"><span data-stu-id="36406-296">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="36406-297">InstanceName</span><span class="sxs-lookup"><span data-stu-id="36406-297">InstanceName</span></span>|<span data-ttu-id="36406-298">要求を処理したレポート サーバー インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="36406-298">Name of the report server instance that handled the request.</span></span>|  
|<span data-ttu-id="36406-299">ReportID</span><span class="sxs-lookup"><span data-stu-id="36406-299">ReportID</span></span>|<span data-ttu-id="36406-300">レポート識別子。</span><span class="sxs-lookup"><span data-stu-id="36406-300">Report identifier.</span></span>|  
|<span data-ttu-id="36406-301">UserName</span><span class="sxs-lookup"><span data-stu-id="36406-301">UserName</span></span>|<span data-ttu-id="36406-302">ユーザー識別子。</span><span class="sxs-lookup"><span data-stu-id="36406-302">User identifier.</span></span>|  
|<span data-ttu-id="36406-303">RequestType</span><span class="sxs-lookup"><span data-stu-id="36406-303">RequestType</span></span>|<span data-ttu-id="36406-304">指定できる値</span><span class="sxs-lookup"><span data-stu-id="36406-304">Possible values:</span></span><br /><br /> <span data-ttu-id="36406-305">True = サブスクリプション要求</span><span class="sxs-lookup"><span data-stu-id="36406-305">True = A Subscription request</span></span><br /><br /> <span data-ttu-id="36406-306">False = 対話型の要求</span><span class="sxs-lookup"><span data-stu-id="36406-306">False= An Interactive request</span></span>|  
|<span data-ttu-id="36406-307">書式</span><span class="sxs-lookup"><span data-stu-id="36406-307">Format</span></span>|<span data-ttu-id="36406-308">表示形式。</span><span class="sxs-lookup"><span data-stu-id="36406-308">Rendering format.</span></span>|  
|<span data-ttu-id="36406-309">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36406-309">Parameters</span></span>|<span data-ttu-id="36406-310">レポート実行に使用するパラメーター値。</span><span class="sxs-lookup"><span data-stu-id="36406-310">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="36406-311">TimeStart</span><span class="sxs-lookup"><span data-stu-id="36406-311">TimeStart</span></span>|<span data-ttu-id="36406-312">レポート処理の期間を示す開始時刻と終了時刻。</span><span class="sxs-lookup"><span data-stu-id="36406-312">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="36406-313">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="36406-313">TimeEnd</span></span>||  
|<span data-ttu-id="36406-314">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="36406-314">TimeDataRetrieval</span></span>|<span data-ttu-id="36406-315">データの取得、レポートの処理、レポートの表示にかかった時間 (単位はミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="36406-315">Number of milliseconds spent retrieving the data, processing the report, and rendering the report.</span></span>|  
|<span data-ttu-id="36406-316">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="36406-316">TimeProcessing</span></span>||  
|<span data-ttu-id="36406-317">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="36406-317">TimeRendering</span></span>||  
|<span data-ttu-id="36406-318">source</span><span class="sxs-lookup"><span data-stu-id="36406-318">Source</span></span>|<span data-ttu-id="36406-319">レポート実行のソース。</span><span class="sxs-lookup"><span data-stu-id="36406-319">Source of the report execution.</span></span> <span data-ttu-id="36406-320">有効値: 1 = 実行中、2 = キャッシュ、3 = スナップショット、4 = 履歴、5 = アドホック、6 = セッション、7 = RDCE。</span><span class="sxs-lookup"><span data-stu-id="36406-320">Possible values: (1=Live, 2=Cache, 3=Snapshot, 4=History, 5=Adhoc, 6=Session, 7=RDCE).</span></span>|  
|<span data-ttu-id="36406-321">Status</span><span class="sxs-lookup"><span data-stu-id="36406-321">Status</span></span>|<span data-ttu-id="36406-322">有効値: rsSuccess、rsProcessingAborted、またはエラー コード。</span><span class="sxs-lookup"><span data-stu-id="36406-322">Possible values: rsSuccess, rsProcessingAborted, or an error code.</span></span> <span data-ttu-id="36406-323">複数のエラーが発生した場合は、最初のエラーだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="36406-323">If multiple errors occur, only the first error is recorded.</span></span>|  
|<span data-ttu-id="36406-324">ByteCount</span><span class="sxs-lookup"><span data-stu-id="36406-324">ByteCount</span></span>|<span data-ttu-id="36406-325">表示されるレポートのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="36406-325">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="36406-326">RowCount</span><span class="sxs-lookup"><span data-stu-id="36406-326">RowCount</span></span>|<span data-ttu-id="36406-327">クエリから返される行数。</span><span class="sxs-lookup"><span data-stu-id="36406-327">Number of rows returned from queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36406-328">参照</span><span class="sxs-lookup"><span data-stu-id="36406-328">See Also</span></span>  
 <span data-ttu-id="36406-329">[SharePoint トレースログの Reporting Services イベントをオンにする &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md) </span><span class="sxs-lookup"><span data-stu-id="36406-329">[Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md) </span></span>  
 <span data-ttu-id="36406-330">[Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="36406-330">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 [<span data-ttu-id="36406-331">エラーとイベントのリファレンス (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="36406-331">Errors and Events Reference &#40;Reporting Services&#41;</span></span>](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
