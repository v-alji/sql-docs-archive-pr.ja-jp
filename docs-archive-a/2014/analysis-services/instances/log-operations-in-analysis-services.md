---
title: Analysis Services のログ操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa1db060-95dc-4198-8aeb-cffdda44b140
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95d0e41576e449ab10b243ef49cbe283940afe0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643004"
---
# <a name="log-operations-in-analysis-services"></a><span data-ttu-id="d8aaa-102">Analysis Services でのログ操作</span><span class="sxs-lookup"><span data-stu-id="d8aaa-102">Log operations in Analysis Services</span></span>
  <span data-ttu-id="d8aaa-103">Analysis Services インスタンスは、サーバーの通知、エラー、および警告を msmdsrv.exe ファイルに記録します。インストールするインスタンスごとに1つです。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-103">An Analysis Services instance will log server notifications, errors, and warnings to the msmdsrv.log file - one for each instance you install.</span></span> <span data-ttu-id="d8aaa-104">管理者は、ルーチンのイベントと異常なイベントのどちらの情報を得る場合でも、このログを参照します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-104">Administrators refer to this log for insights into routine and extraordinary events alike.</span></span> <span data-ttu-id="d8aaa-105">最近のリリースにおいては、ログ記録が機能拡張され、さらに多くの情報が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-105">In recent releases, logging has been enhanced to include more information.</span></span> <span data-ttu-id="d8aaa-106">ログ レコードには、製品のバージョンおよびエディション情報だけでなく、プロセッサ、メモリ、接続、およびブロック イベントも含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-106">Log records now include product version and edition information, as well as processor, memory, connectivity, and blocking events.</span></span> <span data-ttu-id="d8aaa-107">[ログ記録の機能強化](https://support.microsoft.com/kb/2965035)に関するページで、全体的な変更の一覧を確認できます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-107">You can review the entire change list at [Logging improvements](https://support.microsoft.com/kb/2965035).</span></span>  
  
 <span data-ttu-id="d8aaa-108">組み込みのログ記録機能以外にも、多くの管理者および開発者が、Analysis Services コミュニティが提供する **ASTrace**などのツールを使用して、サーバー操作に関するデータを収集しています。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-108">Besides the built-in logging feature, many administrators and developers also use tools provided by the Analysis Services community to collect data about server operations, such as **ASTrace**.</span></span> <span data-ttu-id="d8aaa-109">ダウンロードのリンクについては、「 [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/) 」 (Microsoft SQL Server コミュニティ サンプル: Analysis Services) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-109">See [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/) for the download links.</span></span>  
  
 <span data-ttu-id="d8aaa-110">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-110">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="d8aaa-111">ログの場所と種類</span><span class="sxs-lookup"><span data-stu-id="d8aaa-111">Location and types of logs</span></span>](#bkmk_location)  
  
-   [<span data-ttu-id="d8aaa-112">ログファイルの構成設定に関する一般的な情報</span><span class="sxs-lookup"><span data-stu-id="d8aaa-112">General information on log file configuration settings</span></span>](#bkmk_general)  
  
-   [<span data-ttu-id="d8aaa-113">MSMDSRV サービス ログ ファイル</span><span class="sxs-lookup"><span data-stu-id="d8aaa-113">MSMDSRV service log file</span></span>](#bkmk_msmdsrv)  
  
-   [<span data-ttu-id="d8aaa-114">クエリログ</span><span class="sxs-lookup"><span data-stu-id="d8aaa-114">Query logs</span></span>](#bkmk_querylog)  
  
-   [<span data-ttu-id="d8aaa-115">ミニダンプ (mdmp) ファイル</span><span class="sxs-lookup"><span data-stu-id="d8aaa-115">Mini dump (.mdmp) files</span></span>](#bkmk_mdmp)  
  
-   [<span data-ttu-id="d8aaa-116">ヒントとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="d8aaa-116">Tips and best practices</span></span>](#bkmk_tips)  
  
> [!NOTE]  
>  <span data-ttu-id="d8aaa-117">ログ記録の情報をお探しの場合、処理およびクエリの実行パスを示す操作のトレースに関心を持たれるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-117">If you're looking for information about logging, you might also be interested in tracing operations that show processing and query execution paths.</span></span> <span data-ttu-id="d8aaa-118">アドホックかつ持続的なトレース(キューブ アクセスの監査など) のためのトレース オブジェクト、および Flight Recorder、SQL Server Profiler、および xEvents を最適に使用する方法に関する推奨事項は、このページ (「 [Analysis Services インスタンスの監視](monitor-an-analysis-services-instance.md)」) のリンクから確認できます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-118">Trace objects for ad hoc and sustained tracing (such as auditing cube access) ─ as well as recommendations on how to best use Flight Recorder, SQL Server Profiler, and xEvents ─ can be found through the links on this page: [Monitor an Analysis Services Instance](monitor-an-analysis-services-instance.md).</span></span>  
  
##  <a name="location-and-types-of-logs"></a><a name="bkmk_location"></a><span data-ttu-id="d8aaa-119">ログの場所と種類</span><span class="sxs-lookup"><span data-stu-id="d8aaa-119">Location and types of logs</span></span>  
 <span data-ttu-id="d8aaa-120">Analysis Services では、次に示すログが提供されています。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-120">Analysis Services provides the logs described below.</span></span>  
  
|<span data-ttu-id="d8aaa-121">ファイルの名前または場所</span><span class="sxs-lookup"><span data-stu-id="d8aaa-121">File name or Location</span></span>|<span data-ttu-id="d8aaa-122">Type</span><span class="sxs-lookup"><span data-stu-id="d8aaa-122">Type</span></span>|<span data-ttu-id="d8aaa-123">使用目的</span><span class="sxs-lookup"><span data-stu-id="d8aaa-123">Used for</span></span>|<span data-ttu-id="d8aaa-124">既定でオン</span><span class="sxs-lookup"><span data-stu-id="d8aaa-124">On by default</span></span>|  
|---------------------------|----------|--------------|-------------------|  
|<span data-ttu-id="d8aaa-125">Msmdsrv.log</span><span class="sxs-lookup"><span data-stu-id="d8aaa-125">Msmdsrv.log</span></span>|<span data-ttu-id="d8aaa-126">エラー ログ</span><span class="sxs-lookup"><span data-stu-id="d8aaa-126">Error log</span></span>|<span data-ttu-id="d8aaa-127">ルーチン監視と基本的なトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d8aaa-127">Routine monitoring and basic troubleshooting</span></span>|<span data-ttu-id="d8aaa-128">はい</span><span class="sxs-lookup"><span data-stu-id="d8aaa-128">Yes</span></span>|  
|<span data-ttu-id="d8aaa-129">リレーショナル データベースの OlapQueryLog テーブル</span><span class="sxs-lookup"><span data-stu-id="d8aaa-129">OlapQueryLog table in a relational database</span></span>|<span data-ttu-id="d8aaa-130">クエリ ログ</span><span class="sxs-lookup"><span data-stu-id="d8aaa-130">Query log</span></span>|<span data-ttu-id="d8aaa-131">[使用法の最適化] ウィザードでの入力の収集</span><span class="sxs-lookup"><span data-stu-id="d8aaa-131">Collect inputs for the Usage Optimization Wizard</span></span>|<span data-ttu-id="d8aaa-132">いいえ</span><span class="sxs-lookup"><span data-stu-id="d8aaa-132">No</span></span>|  
|<span data-ttu-id="d8aaa-133">SQLDmp \<guid> ファイル</span><span class="sxs-lookup"><span data-stu-id="d8aaa-133">SQLDmp\<guid>.mdmp files</span></span>|<span data-ttu-id="d8aaa-134">クラッシュと例外</span><span class="sxs-lookup"><span data-stu-id="d8aaa-134">Crashes and exceptions</span></span>|<span data-ttu-id="d8aaa-135">高度なトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d8aaa-135">Deep troubleshooting</span></span>|<span data-ttu-id="d8aaa-136">いいえ</span><span class="sxs-lookup"><span data-stu-id="d8aaa-136">No</span></span>|  
  
 <span data-ttu-id="d8aaa-137">このトピックで説明されていない追加の情報リソースについては、 [マイクロソフト サポートからの初期データ コレクションに関するヒントのページ](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)を参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-137">We highly recommend the following link for additional information resources not covered in this topic: [Initial data collection tips from Microsoft Support](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx).</span></span>  
  
##  <a name="general-information-on-log-file-configuration-settings"></a><a name="bkmk_general"></a> <span data-ttu-id="d8aaa-138">ログ ファイルの構成設定に関する一般情報</span><span class="sxs-lookup"><span data-stu-id="d8aaa-138">General information on log file configuration settings</span></span>  
 <span data-ttu-id="d8aaa-139">各ログのセクションは msmdsrv.ini サーバー構成ファイル内にあります。このファイルは \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-139">You can find sections for each log in the msmdsrv.ini server configuration file, located in the \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config folder.</span></span> <span data-ttu-id="d8aaa-140">ファイルを編集する手順については、「 [Analysis Services でのサーバープロパティの構成](../server-properties/server-properties-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-140">See [Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md) for instructions on editing the file.</span></span>  
  
 <span data-ttu-id="d8aaa-141">可能であれば、Management Studio の [サーバーのプロパティ] ページにあるログ記録のプロパティを設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-141">Where possible, we suggest that you set logging properties in the server properties page of Management Studio.</span></span> <span data-ttu-id="d8aaa-142">ただし、場合によっては、管理ツールに表示されていない設定を構成するため、msmdsrv.ini ファイルを直接編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-142">Although in some cases, you must edit the msmdsrv.ini file directly to configure settings that are not visible in the administrative tools.</span></span>  
  
 <span data-ttu-id="d8aaa-143">![ログ設定を示した構成ファイルのセクション](../media/ssas-logfilesettings.png "ログ設定を示した構成ファイルのセクション")</span><span class="sxs-lookup"><span data-stu-id="d8aaa-143">![Section of the config file showing log settings](../media/ssas-logfilesettings.png "Section of the config file showing log settings")</span></span>  
  
##  <a name="msmdsrv-service-log-file"></a><a name="bkmk_msmdsrv"></a><span data-ttu-id="d8aaa-144">MSMDSRV.EXE サービスログファイル</span><span class="sxs-lookup"><span data-stu-id="d8aaa-144">MSMDSRV service log file</span></span>  
 <span data-ttu-id="d8aaa-145">Analysis Services は、サーバーの操作のログを msmdsrv.log ファイルにインスタンスごとに記録します。このログ ファイルの場所は \program files\Microsoft SQL Server\\<instance\>\Olap\Log です。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-145">Analysis Services logs server operations to the msmdsrv.log file, one per instance, located at \program files\Microsoft SQL Server\\<instance\>\Olap\Log.</span></span>  
  
 <span data-ttu-id="d8aaa-146">このログ ファイルは、サービスを再起動するたびに空になります。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-146">This log file is emptied at each service restart.</span></span> <span data-ttu-id="d8aaa-147">以前のリリースでは、ログ ファイルが使用できなくなるほど肥大化する事態を避けるためだけに、管理者がサービスを再起動してログ ファイルをフラッシュするということも行われていました。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-147">In previous releases, administrators would sometimes restart the service for the sole purpose of flushing the log file before it could grow so large as to become unusable.</span></span> <span data-ttu-id="d8aaa-148">これはもう不要です。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-148">This is no longer necessary.</span></span> <span data-ttu-id="d8aaa-149">SQL Server 2012 SP2 以降で導入された構成設定では、ログ ファイルとその履歴のサイズを制御できます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-149">Configuration settings, introduced in SQL Server 2012 SP2 and later, give you control over the size of the log file and its history:</span></span>  
  
-   <span data-ttu-id="d8aaa-150">`MaxFileSizeMB` は、ログ ファイルの最大サイズを MB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-150">`MaxFileSizeMB` specifies a maximum log file size in megabytes.</span></span> <span data-ttu-id="d8aaa-151">既定値は 256 です。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-151">The default is 256.</span></span> <span data-ttu-id="d8aaa-152">置き換える有効な値は正の整数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-152">A valid replacement value must be a positive integer.</span></span> <span data-ttu-id="d8aaa-153">Analysis Services は、`MaxFileSizeMB` に達すると、現在のファイルの名前を msmdsrv{現在のタイムスタンプ}.log ファイルに変更し、新しい msmdsrv.log ファイルの使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-153">When `MaxFileSizeMB` is reached, Analysis Services renames the current file as msmdsrv{current timestamp}.log file, and starts a new msmdsrv.log file.</span></span>  
  
-   <span data-ttu-id="d8aaa-154">`MaxNumberFiles` は、古いログ ファイルの保有期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-154">`MaxNumberFiles` specifies retention of older log files.</span></span> <span data-ttu-id="d8aaa-155">既定値は 0 (無効) です。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-155">The default is 0 (disabled).</span></span> <span data-ttu-id="d8aaa-156">ログ ファイルのバージョンを維持するには、正の整数に変更します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-156">You can change it to a positive integer to keep versions of the log file.</span></span> <span data-ttu-id="d8aaa-157">Analysis Services は、`MaxNumberFiles` に達すると、名前のタイムスタンプが最も古いものからファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-157">When `MaxNumberFiles` is reached, Analysis Services deletes the file with the oldest timestamp in its name.</span></span>  
  
 <span data-ttu-id="d8aaa-158">これらの設定を使用するには、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-158">To use these settings, do the following:</span></span>  
  
1.  <span data-ttu-id="d8aaa-159">msmdsrv.ini をメモ帳で開きます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-159">Open msmdsrv.ini in NotePad.</span></span>  
  
2.  <span data-ttu-id="d8aaa-160">次の 2 行をコピーします。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-160">Copy the following two lines:</span></span>  
  
    ```  
    <MaxFileSizeMB>256</MaxFileSizeMB>  
    <MaxNumberOfLogFiles>5</MaxNumberOfLogFiles>  
    ```  
  
3.  <span data-ttu-id="d8aaa-161">この 2 行を、msmdsrv.ini の Log セクション (msmdsrv.log のファイル名の下にある) に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-161">Paste the two lines into the Log section of msmdsrv.ini, below the filename for msmdsrv.log.</span></span> <span data-ttu-id="d8aaa-162">両方の設定を手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-162">Both settings must be added manually.</span></span> <span data-ttu-id="d8aaa-163">msmdsrv.ini ファイル内にプレースホルダーはありません。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-163">There are no placeholders for them in the msmdsrv.ini file.</span></span>  
  
     <span data-ttu-id="d8aaa-164">変更された構成ファイルは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-164">The changed configuration file should look like the following:</span></span>  
  
    ```  
    <Log>  
    <File>msmdsrv.log</File>  
    <MaxFileSizeMB>256</MaxFileSizeMB>  
    <MaxNumberOfLogFiles>5</MaxNumberOfLogFiles>  
    <FileBufferSize>0</FileBufferSize>  
  
    ```  
  
4.  <span data-ttu-id="d8aaa-165">与えられた値が希望と異なる場合は、値を編集します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-165">Edit the values if those provided differ from what you want.</span></span>  
  
5.  <span data-ttu-id="d8aaa-166">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-166">Save the file.</span></span>  
  
6.  <span data-ttu-id="d8aaa-167">サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-167">Restart the service.</span></span>  
  
##  <a name="query-logs"></a><a name="bkmk_querylog"></a> <span data-ttu-id="d8aaa-168">クエリ ログ</span><span class="sxs-lookup"><span data-stu-id="d8aaa-168">Query logs</span></span>  
 <span data-ttu-id="d8aaa-169">クエリ ログの名称には若干誤りがあります。というのは、クエリ ログではユーザーの MDX クエリや DAX クエリの操作をログに記録しないためです。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-169">The query log is a bit of a misnomer in that it does not log the MDX or DAX query activity of your users.</span></span> <span data-ttu-id="d8aaa-170">代わりに、クエリ ログでは、Analysis Services によって生成されるクエリに関するデータを収集します。その後、このデータが [使用法に基づく最適化] ウィザードのデータ入力として使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-170">Instead, it collects data about queries generated by Analysis Services, which is subsequently used as data input in the Usage Based Optimization Wizard.</span></span> <span data-ttu-id="d8aaa-171">クエリ ログに収集されたデータは直接分析するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-171">The data collected in the query log is not intended for direct analysis.</span></span> <span data-ttu-id="d8aaa-172">具体的には、データセットは、データセットのパスがクエリに含まれることを示す 0 または 1 のビット配列で記述されます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-172">Specifically, the datasets are described in bit arrays, with a zero or a one indicating the parts of dataset is included in the query.</span></span> <span data-ttu-id="d8aaa-173">ここでも、このデータはウィザード向けのものです。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-173">Again, this data is meant for the wizard.</span></span>  
  
 <span data-ttu-id="d8aaa-174">クエリの監視とトラブルシューティングのため、多くの開発者および管理者は、クエリを監視するためにコミュニティ ツール **ASTrace**を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-174">For query monitoring and troubleshooting, many developers and administrators use a community tool, **ASTrace**, to monitor queries.</span></span> <span data-ttu-id="d8aaa-175">また、SQL Server Profiler、xEvents、または Analysis Services トレースも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-175">You can also use SQL Server Profiler, xEvents, or an Analysis Services trace.</span></span> <span data-ttu-id="d8aaa-176">トレース関連のリンクについては、「 [Analysis Services インスタンスの監視](monitor-an-analysis-services-instance.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-176">See [Monitor an Analysis Services Instance](monitor-an-analysis-services-instance.md) for tracing-related links.</span></span>  
  
 <span data-ttu-id="d8aaa-177">クエリ ログを使用する場合</span><span class="sxs-lookup"><span data-stu-id="d8aaa-177">When should you use the query log?</span></span> <span data-ttu-id="d8aaa-178">[使用法に基づく最適化] ウィザードを含むクエリ パフォーマンス チューニングの練習の一部として、クエリ ログを有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-178">We recommend enabling the query log as part of a query performance tuning exercise that includes the Usage Based Optimization Wizard.</span></span> <span data-ttu-id="d8aaa-179">機能を有効にして、機能をサポートするデータ構造を作成し、Analysis Services がログの検索と作成に使用するプロパティを設定するまでは、クエリ ログは存在しません。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-179">The query log does not exist until you enable the feature, create the data structures to support it, and set properties used by Analysis Services to locate and populate the log.</span></span>  
  
 <span data-ttu-id="d8aaa-180">クエリ ログを有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-180">To enable the query log, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d8aaa-181">クエリ ログを格納する SQL Server リレーショナル データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-181">Create a SQL Server relational database to store the query log.</span></span>  
  
2.  <span data-ttu-id="d8aaa-182">Analysis Services のサービス アカウントに、データベースに対する十分なアクセス許可を付与します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-182">Grant the Analysis Services service account sufficient permissions on the database.</span></span> <span data-ttu-id="d8aaa-183">アカウントには、テーブルの作成、テーブルへの書き込み、テーブルからの読み取りの権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-183">The account needs permission to create a table, write to the table, and read from the table.</span></span>  
  
3.  <span data-ttu-id="d8aaa-184">SQL Server Management Studio で**Analysis Services**プロパティの全般] を右クリックし  |  **Properties**  |  **General**、[ **createquerylogtable** ] を [true] に設定します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-184">In SQL Server Management Studio, right-click **Analysis Services** | **Properties** | **General**, set **CreateQueryLogTable** to true.</span></span>  
  
4.  <span data-ttu-id="d8aaa-185">(省略可能) クエリを異なるレートでサンプリングする場合、またはテーブルに異なる名前を使用する場合は、 **QueryLogSampling** または **QueryLogTableName** を変更します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-185">Optionally, change **QueryLogSampling** or **QueryLogTableName** if you want to sample queries at a different rate, or use a different name for the table.</span></span>  
  
 <span data-ttu-id="d8aaa-186">サンプリングの要件を満たすだけの十分な MDX クエリを実行するまでクエリ ログ テーブルは作成されません。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-186">The query log table will not be created until you have run enough MDX queries to meet the sampling requirements.</span></span> <span data-ttu-id="d8aaa-187">たとえば、10 の既定値を維持する場合は、テーブルが作成されるまでに少なくとも 10 個のクエリを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-187">For example, if you keep the default value of 10, you must run at least 10 queries before the table will be created.</span></span>  
  
 <span data-ttu-id="d8aaa-188">クエリ ログの設定は、サーバー全体に適用します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-188">Query log settings are server wide.</span></span> <span data-ttu-id="d8aaa-189">指定した設定は、このサーバーで実行されているすべてのデータベースで使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-189">The settings you specify will be used by all databases running on this server.</span></span>  
  
 <span data-ttu-id="d8aaa-190">![Management Studio でのクエリ ログの設定](../media/ssas-querylogsettings.png "Management Studio でのクエリ ログの設定")</span><span class="sxs-lookup"><span data-stu-id="d8aaa-190">![Query log settings in Management Studio](../media/ssas-querylogsettings.png "Query log settings in Management Studio")</span></span>  
  
 <span data-ttu-id="d8aaa-191">構成設定を指定したら、MDX クエリを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-191">After the configuration settings are specified, run an MDX query multiple times.</span></span> <span data-ttu-id="d8aaa-192">サンプリングを 10 に設定している場合は、クエリを 11 回実行します。テーブルが作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-192">If sampling is set to 10, run the query 11 times.Verify the table is created.</span></span> <span data-ttu-id="d8aaa-193">Management Studio で、リレーショナル データベース エンジンに接続し、データベース フォルダーを開きます。 **Tables** フォルダーを開き、 **OlapQueryLog** が存在していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-193">In Management Studio, connect to the relational database engine, open the database folder, open the **Tables** folder, and verify that **OlapQueryLog** exists.</span></span> <span data-ttu-id="d8aaa-194">テーブルがすぐに表示されない場合は、フォルダーの情報を更新して内容への変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-194">If you do not immediately see the table, refresh the folder to pick up any changes to its contents.</span></span>  
  
 <span data-ttu-id="d8aaa-195">クエリ ログが [使用法に基づく最適化] ウィザードに十分なデータを蓄積できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-195">Allow the query log to accumulate sufficient data for the Usage Based Optimization Wizard.</span></span> <span data-ttu-id="d8aaa-196">クエリのボリュームが循環的である場合は、代表的なデータのセットを得るのに十分なトラフィック量をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-196">If query volumes are cyclical, capture enough traffic to have a representative set of data.</span></span> <span data-ttu-id="d8aaa-197">ウィザードの実行方法の説明については、「 [使用法に基づく最適化ウィザード](https://msdn.microsoft.com/library/ms189706.aspx) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-197">See [Usage Based Optimization Wizard](https://msdn.microsoft.com/library/ms189706.aspx) for instructions on how to run the wizard.</span></span>  
  
 <span data-ttu-id="d8aaa-198">クエリ ログの構成については、「 [Analysis Services クエリ ログの構成](https://technet.microsoft.com/library/Cc917676) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-198">See [Configuring the Analysis Services Query Log](https://technet.microsoft.com/library/Cc917676) to learn more about query log configuration.</span></span> <span data-ttu-id="d8aaa-199">記事は非常に古いものですが、クエリ ログの構成は最近のリリースでは変更されておらず、含まれている情報は引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-199">Although the paper is quite old, query log configuration has not changed in recent releases and the information it contains still applies.</span></span>  
  
##  <a name="mini-dump-mdmp-files"></a><a name="bkmk_mdmp"></a> <span data-ttu-id="d8aaa-200">ミニ ダンプ (.mdmp) ファイル</span><span class="sxs-lookup"><span data-stu-id="d8aaa-200">Mini dump (.mdmp) files</span></span>  
 <span data-ttu-id="d8aaa-201">ダンプ ファイルでは、異例なイベントを分析するために使用されるデータをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-201">Dump files capture data used for analyzing extraordinary events.</span></span> <span data-ttu-id="d8aaa-202">Analysis Services は、サーバーのクラッシュ、例外、およびいくつかの構成エラーに対応してミニ ダンプ (.mdmp) を自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-202">Analysis Services automatically generates mini dumps (.mdmp) in response to a server crash, exception, and some configuration errors.</span></span> <span data-ttu-id="d8aaa-203">機能が有効であっても、クラッシュ レポートは自動的に送信されません。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-203">The feature is enabled, but does not send crash reports automatically.</span></span>  
  
 <span data-ttu-id="d8aaa-204">クラッシュ レポートは、Msmdsrv.ini ファイルの「Exception (例外)」セクションで構成します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-204">Crash reports are configured through the Exception section in the Msmdsrv.ini file.</span></span> <span data-ttu-id="d8aaa-205">これらの設定は、メモリ ダンプ ファイルの生成を制御します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-205">These settings control memory dump file generation.</span></span> <span data-ttu-id="d8aaa-206">次のスニペットは、既定値を示しています。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-206">The following snippet shows the default values:</span></span>  
  
```  
<Exception>  
<CreateAndSendCrashReports>1</CreateAndSendCrashReports>  
<CrashReportsFolder/>  
<SQLDumperFlagsOn>0x0</SQLDumperFlagsOn>  
<SQLDumperFlagsOff>0x0</SQLDumperFlagsOff>  
<MiniDumpFlagsOn>0x0</MiniDumpFlagsOn>  
<MiniDumpFlagsOff>0x0</MiniDumpFlagsOff>  
<MinidumpErrorList>0xC1000000, 0xC1000001, 0xC102003F, 0xC1360054, 0xC1360055</MinidumpErrorList>  
<ExceptionHandlingMode>0</ExceptionHandlingMode>  
<CriticalErrorHandling>1</CriticalErrorHandling>  
<MaxExceptions>500</MaxExceptions>  
<MaxDuplicateDumps>1</MaxDuplicateDumps>  
</Exception>  
```  
  
 <span data-ttu-id="d8aaa-207">**クラッシュ レポートの構成**</span><span class="sxs-lookup"><span data-stu-id="d8aaa-207">**Configure Crash Reports**</span></span>  
  
 <span data-ttu-id="d8aaa-208">特に Microsoft サポートから指示がない限り、ほとんどの管理者は既定の設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-208">Unless otherwise directed by Microsoft Support, most administrators use the default settings.</span></span> <span data-ttu-id="d8aaa-209">このサポート技術情報「 [メモリ ダンプ ファイルを生成するように Analysis Services を構成する方法](https://support.microsoft.com/kb/919711)」は古いものですが、ダンプ ファイルの構成手順として今も使用されています。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-209">This older KB article is still used to provide instruction on how to configure dump files: [How to configure Analysis Services to generate memory dump files](https://support.microsoft.com/kb/919711).</span></span>  
  
 <span data-ttu-id="d8aaa-210">最も変更される可能性が高い構成設定は、メモリ ダンプ ファイルを生成するかどうかの指定に使用する `CreateAndSendCrashReports` の設定です。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-210">The configuration setting most likely to be modified is the `CreateAndSendCrashReports` setting used to determine whether a memory dump file will be generated.</span></span>  
  
|<span data-ttu-id="d8aaa-211">値</span><span class="sxs-lookup"><span data-stu-id="d8aaa-211">Value</span></span>|<span data-ttu-id="d8aaa-212">説明</span><span class="sxs-lookup"><span data-stu-id="d8aaa-212">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d8aaa-213">0</span><span class="sxs-lookup"><span data-stu-id="d8aaa-213">0</span></span>|<span data-ttu-id="d8aaa-214">メモリ ダンプ ファイルをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-214">Turns off the memory dump file.</span></span> <span data-ttu-id="d8aaa-215">「Exception (例外)」セクションの他のすべての設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-215">All other settings under the Exception section are ignored.</span></span>|  
|<span data-ttu-id="d8aaa-216">1</span><span class="sxs-lookup"><span data-stu-id="d8aaa-216">1</span></span>|<span data-ttu-id="d8aaa-217">(既定) メモリ ダンプ ファイルを有効にしますが送信しません。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-217">(Default) Enables, but does not send, the memory dump file.</span></span>|  
|<span data-ttu-id="d8aaa-218">2</span><span class="sxs-lookup"><span data-stu-id="d8aaa-218">2</span></span>|<span data-ttu-id="d8aaa-219">有効にするとともに、エラー レポートを Microsoft に自動的に送信します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-219">Enables and automatically sends an error report to Microsoft.</span></span>|  
  
 <span data-ttu-id="d8aaa-220">`CrashReportsFolder` はダンプ ファイルの場所です。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-220">`CrashReportsFolder` is the location of the dump files.</span></span> <span data-ttu-id="d8aaa-221">既定では、.mdmp ファイルと関連付けられているログ レコードは \Olap\Log フォルダー内にあります。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-221">By default, an .mdmp file and associated log records can be found in the \Olap\Log folder.</span></span>  
  
 <span data-ttu-id="d8aaa-222">`SQLDumperFlagsOn` は完全ダンプの生成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-222">`SQLDumperFlagsOn` is used to generate a full dump.</span></span> <span data-ttu-id="d8aaa-223">既定では、完全ダンプは無効です。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-223">By default, full dumps are not enabled.</span></span> <span data-ttu-id="d8aaa-224">このプロパティは `0x34` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-224">You can set this property to `0x34`.</span></span>  
  
 <span data-ttu-id="d8aaa-225">次のリンクに詳しい背景情報があります。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-225">The following links provide more background:</span></span>  
  
-   [<span data-ttu-id="d8aaa-226">ミニダンプを使用する SQL Server について詳しく知る</span><span class="sxs-lookup"><span data-stu-id="d8aaa-226">Looking Deeper into SQL Server using Minidumps</span></span>](https://blogs.msdn.com/b/sqlcat/archive/2009/09/11/looking-deeper-into-sql-server-using-minidumps.aspx)  
  
-   [<span data-ttu-id="d8aaa-227">ユーザー モードのダンプ ファイルを作成する方法</span><span class="sxs-lookup"><span data-stu-id="d8aaa-227">How to create a user mode dump file</span></span>](https://support.microsoft.com/kb/931673)  
  
-   [<span data-ttu-id="d8aaa-228">Sqldumper.exe ユーティリティを使用して SQL Server にダンプ ファイルを生成する方法</span><span class="sxs-lookup"><span data-stu-id="d8aaa-228">How to use the Sqldumper.exe utility to generate a dump file in SQL Server</span></span>](https://support.microsoft.com/kb/917825)  
  
##  <a name="tips-and-best-practices"></a><a name="bkmk_tips"></a><span data-ttu-id="d8aaa-229">ヒントとベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="d8aaa-229">Tips and best practices</span></span>  
 <span data-ttu-id="d8aaa-230">このセクションは、この記事全体で説明したヒントの要約です。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-230">This section is a recap of the tips mentioned throughout this article.</span></span>  
  
-   <span data-ttu-id="d8aaa-231">msmdsrv log ファイルのサイズと数を制御するには、msmdsrv.log ファイルを構成します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-231">Configure the msmdsrv.log file to control the size and number of msmdsrv log file.</span></span> <span data-ttu-id="d8aaa-232">既定では設定が無効になっているため、必ずインストール後の手順として設定を追加してください。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-232">The settings are not enabled by default, so be sure to add them as post-installation step.</span></span> <span data-ttu-id="d8aaa-233">このトピックの [MSMDSRV サービス ログ ファイル](#bkmk_msmdsrv) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-233">See [MSMDSRV service log file](#bkmk_msmdsrv) in this topic.</span></span>  
  
-   <span data-ttu-id="d8aaa-234">サーバーの操作に関する情報の取得に使用するリソースについて知るには、マイクロソフト カスタマー サポートから [最初のデータの収集に関するブログの投稿](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)を確認します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-234">Review this blog post from Microsoft Customer Support to learn what resources they use to get information about server operations: [Initial Data Collection](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)</span></span>  
  
-   <span data-ttu-id="d8aaa-235">キューブのクエリを実行している人を確認するには、クエリ ログではなく ASTrace2012 を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-235">Use ASTrace2012, rather than a query log, to find out who is querying cubes.</span></span> <span data-ttu-id="d8aaa-236">通常、クエリ ログは、[使用法に基づく最適化] ウィザードへの入力に使用され、クエリ ログでキャプチャしたデータは読み取りや解釈が簡単ではありません。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-236">The query log is typically used to provide input into the Usage Based Optimization Wizard, and the data it captures is not easy to read or interpret.</span></span> <span data-ttu-id="d8aaa-237">ASTrace2012 は、クエリ操作のキャプチャに広く使われているコミュニティ ツールです。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-237">ASTrace2012 is a community tool, widely used, that captures query operations.</span></span> <span data-ttu-id="d8aaa-238">「 [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/)」 (Microsoft SQL Server コミュニティ サンプル: Analysis Services) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8aaa-238">See [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8aaa-239">参照</span><span class="sxs-lookup"><span data-stu-id="d8aaa-239">See Also</span></span>  
 <span data-ttu-id="d8aaa-240">[Analysis Services インスタンス管理](analysis-services-instance-management.md) </span><span class="sxs-lookup"><span data-stu-id="d8aaa-240">[Analysis Services Instance Management](analysis-services-instance-management.md) </span></span>  
 <span data-ttu-id="d8aaa-241">[SQL Server プロファイラーを使用した Analysis Services の監視の概要](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="d8aaa-241">[Introduction to Monitoring Analysis Services with SQL Server Profiler](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="d8aaa-242">Analysis Services のサーバーのプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="d8aaa-242">Configure Server Properties in Analysis Services</span></span>](../server-properties/server-properties-in-analysis-services.md)  
  
  
