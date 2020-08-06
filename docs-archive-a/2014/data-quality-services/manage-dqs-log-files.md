---
title: DQS ログ ファイルの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- logging
- log files
- dqs log files
ms.assetid: 4fccfd24-aede-4882-be69-ec1e82682e16
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ca85772b8cc8aca41b75ad05d028bc444f280378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644645"
---
# <a name="manage-dqs-log-files"></a><span data-ttu-id="6ab6b-102">DQS ログ ファイルの管理</span><span class="sxs-lookup"><span data-stu-id="6ab6b-102">Manage DQS Log Files</span></span>
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] <span data-ttu-id="6ab6b-103">(DQS) のログ ファイルは、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]、および [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]の問題を診断およびトラブルシューティングする際に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-103">(DQS) log files help you in diagnosing and troubleshooting issue with [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and the [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)].</span></span> <span data-ttu-id="6ab6b-104">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]、および [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]ごとに異なるログ ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-104">Separate log files are generated for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and the [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].</span></span>  
  
 <span data-ttu-id="6ab6b-105">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] を使用して、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] の機能とモジュールのログの重大度設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-105">You can use [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] to configure the log severity setting for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] features and modules.</span></span> <span data-ttu-id="6ab6b-106">また、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] コンピューターで DQS_MAIN データベースと XML ファイルの DQS ログ構成設定を手動で変更して、DQS ログ ファイルのその他の (詳細) 設定の一部を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-106">Additionally, you can also configure some other (advanced) settings for the DQS log files by manually changing the DQS log configuration settings in the DQS_MAIN database and an XML file on the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] computer.</span></span>  
  
##  <a name="data-quality-server-log-file"></a><a name="DQSServer"></a><span data-ttu-id="6ab6b-107">Data Quality Server のログファイル</span><span class="sxs-lookup"><span data-stu-id="6ab6b-107">Data Quality Server Log File</span></span>  
 <span data-ttu-id="6ab6b-108">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] のログ ファイルである DQServerLog.DQS_MAIN.log には、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]で実行されるアクティビティのログが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-108">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file, DQServerLog.DQS_MAIN.log, includes logs of activities that are run on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="6ab6b-109">SQL Server の既定のインスタンスをインストールした場合、DQServerLog.DQS_MAIN.log ファイルは C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log に格納されます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-109">If you installed the default instance of SQL Server, the DQServerLog.DQS_MAIN.log file is available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log.</span></span> <span data-ttu-id="6ab6b-110">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] のログ ファイルには、それぞれパイプ (|) で区切られた次の種類の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-110">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file contains the following pieces of information, each delimited by a pipe (|):</span></span>  
  
-   <span data-ttu-id="6ab6b-111">日付と時刻</span><span class="sxs-lookup"><span data-stu-id="6ab6b-111">Date and time</span></span>  
  
-   <span data-ttu-id="6ab6b-112">スレッド名</span><span class="sxs-lookup"><span data-stu-id="6ab6b-112">Thread name</span></span>  
  
-   <span data-ttu-id="6ab6b-113">スレッド ID</span><span class="sxs-lookup"><span data-stu-id="6ab6b-113">Thread ID</span></span>  
  
-   <span data-ttu-id="6ab6b-114">ログの重大度 (FATAL、ERROR、WARN、INFO、および DEBUG)</span><span class="sxs-lookup"><span data-stu-id="6ab6b-114">Log severity (FATAL, ERROR, WARN, INFO, and DEBUG)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6ab6b-115">DEBUG ログ重大度は、[詳細] と同じです。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-115">The DEBUG logging severity is same as Verbose.</span></span>  
  
-   <span data-ttu-id="6ab6b-116">UID (内部 DQS インフラストラクチャ ID)</span><span class="sxs-lookup"><span data-stu-id="6ab6b-116">UID (internal DQS infrastructure ID)</span></span>  
  
-   <span data-ttu-id="6ab6b-117">名前空間</span><span class="sxs-lookup"><span data-stu-id="6ab6b-117">Namespace</span></span>  
  
-   <span data-ttu-id="6ab6b-118">クラスとメソッド</span><span class="sxs-lookup"><span data-stu-id="6ab6b-118">Class and method</span></span>  
  
-   <span data-ttu-id="6ab6b-119">Message</span><span class="sxs-lookup"><span data-stu-id="6ab6b-119">Message</span></span>  
  
 <span data-ttu-id="6ab6b-120">これらに加えて、ログ ファイルには、アプリケーションのバージョン、コンピューター名、ユーザー名、およびオペレーティング システムに関する情報も表示されます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-120">Along with these, the log file also displays information about the application version, computer name, user name, and operating system.</span></span>  
  
 <span data-ttu-id="6ab6b-121">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ログ ファイルのサンプル エントリは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-121">A sample entry in the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file looks like the following:</span></span>  
  
```  
23-08-2013 01:45:29|[]|4|INFO|PUID|InfInfoModuleStarting|Microsoft.Ssdqs.Core.Startup.ServerInit|Starting DQS ServerInit: version [12.0.0.0], machine name [DQS-TEST], user name [NT Service\MSSQLSERVER], operating system [Microsoft Windows NT 6.1.7600.0]...  
```  
  
 <span data-ttu-id="6ab6b-122">DQServerLog.DQS_MAIN.log ファイルはローリング ファイルです。既存のログ ファイルが、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ログ構成設定で指定されたローリング ファイルのサイズを超えると、新しいログ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-122">The DQServerLog.DQS_MAIN.log file is a rolling file, and a new log file is created once the existing log file exceeds the rolling file size limit specified in the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log configuration settings.</span></span> <span data-ttu-id="6ab6b-123">詳細については、「 [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-123">For more information, see [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).</span></span>  
  
##  <a name="data-quality-client-log-file"></a><a name="DQSClient"></a><span data-ttu-id="6ab6b-124">ログファイルの Data Quality Client</span><span class="sxs-lookup"><span data-stu-id="6ab6b-124">Data Quality Client Log File</span></span>  
 <span data-ttu-id="6ab6b-125">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のログ ファイルである DQClientLog.log には、クライアント側のログが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-125">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file, DQClientLog.log, includes the client side logs.</span></span> <span data-ttu-id="6ab6b-126">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のログ ファイルは %APPDATA%\SSDQS\Log に格納されます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-126">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file is available at %APPDATA%\SSDQS\Log.</span></span> <span data-ttu-id="6ab6b-127">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ログ ファイルには、サーバー ログ ファイルと同様の情報が含まれますが、内容はクライアント側に関するものになります。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-127">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file contains similar set of information as in the server log file, but for the client side.</span></span>  
  
 <span data-ttu-id="6ab6b-128">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ログ ファイルと同様に、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ログ ファイルもローリング ファイルです。既存のログ ファイルが、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ログ構成設定で指定されたローリング ファイルのサイズを超えると、新しいログ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-128">As with the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file, the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file is also a rolling file, and a new log file is created once the existing log file exceeds the rolling file size limit specified in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log configuration settings.</span></span> <span data-ttu-id="6ab6b-129">詳細については、「 [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-129">For more information, see [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).</span></span>  
  
##  <a name="dqs-cleansing-component-log-file"></a><a name="DQSCleansing"></a><span data-ttu-id="6ab6b-130">DQS クレンジングコンポーネントのログファイル</span><span class="sxs-lookup"><span data-stu-id="6ab6b-130">DQS Cleansing Component Log File</span></span>  
 <span data-ttu-id="6ab6b-131">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] のログ ファイルである DQSSSISLog.log には、 [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]を使用して実行されたアクティビティのログが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-131">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] log file, DQSSSISLog.log, includes logs of activities performed using the [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)].</span></span> <span data-ttu-id="6ab6b-132">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] コンポーネントのログ ファイルは %APPDATA%\SSDQS\Log に格納されます。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-132">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] component log file is available at %APPDATA%\SSDQS\Log.</span></span> <span data-ttu-id="6ab6b-133">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] ログ ファイルには、サーバー ログ ファイルと同様の情報が含まれますが、内容は [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]に関するものになります。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-133">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] log file contains similar set of information as in the server log file, but for the [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].</span></span>  
  
##  <a name="related-tasks"></a><a name="RT"></a> <span data-ttu-id="6ab6b-134">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6ab6b-134">Related Tasks</span></span>  
  
|<span data-ttu-id="6ab6b-135">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="6ab6b-135">Task Description</span></span>|<span data-ttu-id="6ab6b-136">トピック</span><span class="sxs-lookup"><span data-stu-id="6ab6b-136">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="6ab6b-137">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]を使用して DQS ログ ファイルのログの重大度設定を構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-137">Describes how to configure log severity settings for DQS log files using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>|[<span data-ttu-id="6ab6b-138">DQS ログ ファイルの重大度レベルの構成</span><span class="sxs-lookup"><span data-stu-id="6ab6b-138">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|<span data-ttu-id="6ab6b-139">DQS ログ ファイルの詳細設定を手動で構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6ab6b-139">Describes how to manually configure advanced settings for DQS log files.</span></span>|[<span data-ttu-id="6ab6b-140">DQS ログ ファイルの詳細設定の構成</span><span class="sxs-lookup"><span data-stu-id="6ab6b-140">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
  
## <a name="see-also"></a><span data-ttu-id="6ab6b-141">参照</span><span class="sxs-lookup"><span data-stu-id="6ab6b-141">See Also</span></span>  
 [<span data-ttu-id="6ab6b-142">DQS 管理</span><span class="sxs-lookup"><span data-stu-id="6ab6b-142">DQS Administration</span></span>](../../2014/data-quality-services/dqs-administration.md)  
  
  
