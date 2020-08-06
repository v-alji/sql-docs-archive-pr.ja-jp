---
title: DQS ログ ファイルの詳細設定の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- log files,advanced settings
- dqs log files,advanced settings
ms.assetid: 1d565748-9759-425c-ae38-4d2032a86868
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad41b0cac95f9bfe5565ccbac16b0fda3e28ddf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712417"
---
# <a name="configure-advanced-settings-for-dqs-log-files"></a><span data-ttu-id="e25d2-102">DQS ログ ファイルの詳細設定の構成</span><span class="sxs-lookup"><span data-stu-id="e25d2-102">Configure Advanced Settings for DQS Log Files</span></span>
  <span data-ttu-id="e25d2-103">このトピックでは、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ログ ファイルと [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ログ ファイルの詳細設定を構成する方法 (ログ ファイルのローリング ファイル サイズの制限の設定、イベントのタイム スタンプ パターンの設定など) について説明します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-103">This topic describes how to configure advanced settings for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log files, such as set the rolling file size limit of the log files, set the time stamp pattern of the events, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e25d2-104">これらのアクティビティは [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]を使用して実行できません。また、これらのアクティビティは上級ユーザーだけが実行できます。</span><span class="sxs-lookup"><span data-stu-id="e25d2-104">These activities cannot be performed using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and is intended for advanced users only.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e25d2-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="e25d2-105">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e25d2-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e25d2-106">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e25d2-107">Permissions</span><span class="sxs-lookup"><span data-stu-id="e25d2-107">Permissions</span></span>  
  
-   <span data-ttu-id="e25d2-108">DQS_MAIN データベースの A_CONFIGURATION テーブルで構成の設定を変更するには、Windows ユーザー アカウントが SQL Server インスタンスの sysadmin 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="e25d2-108">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance to modify configuration settings in the A_CONFIGURATION table in the DQS_MAIN database.</span></span>  
  
-   <span data-ttu-id="e25d2-109">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のログ設定を構成するには、DQLog.Client.xml ファイルを変更するコンピューターの Administrators グループのメンバーとしてログオンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e25d2-109">You must be logged on as a member of the Administrators group on the computer where you are modifying the DQLog.Client.xml file to configure the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] logging settings.</span></span>  
  
##  <a name="configure-data-quality-server-log-settings"></a><a name="DQSServer"></a><span data-ttu-id="e25d2-110">Data Quality Server のログ設定の構成</span><span class="sxs-lookup"><span data-stu-id="e25d2-110">Configure Data Quality Server Log Settings</span></span>  
 <span data-ttu-id="e25d2-111">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] のログ設定は、DQS_MAIN データベースの A_CONFIGURATION テーブル内の **[ServerLogging]** 行の **[VALUE]** 列に XML 形式で示されます。</span><span class="sxs-lookup"><span data-stu-id="e25d2-111">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log settings are present in an XML format in the **VALUE** column of the **ServerLogging** row in the A_CONFIGURATION table in the DQS_MAIN database.</span></span> <span data-ttu-id="e25d2-112">構成情報を表示するには、次の SQL クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-112">You can run the following SQL query to view the configuration information:</span></span>  
  
```sql  
select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'; 
```  
  
 <span data-ttu-id="e25d2-113">**ログ記録の構成設定を変更するには、** [ServerLogging] **行の** [VALUE] [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 列で該当する情報を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e25d2-113">You must update the appropriate information in the **VALUE** column of the **ServerLogging** row to change the configuration settings for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging.</span></span> <span data-ttu-id="e25d2-114">この例では、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ログ設定を更新して、ローリング ファイルのサイズ制限を 25000 KB (既定値は 20000 KB) に設定します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-114">In this example, we will update the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log settings to set the rolling file size limit to 25000 KB (the default is 20000 KB).</span></span>  
  
1.  <span data-ttu-id="e25d2-115">Microsoft SQL Server Management Studio を起動し、適切な SQL Server インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-115">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="e25d2-116">オブジェクト エクスプローラーでサーバーを右クリックし、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e25d2-116">In Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e25d2-117">クエリ エディター ウィンドウで、SQL ステートメントをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e25d2-117">In the Query Editor window, copy the following SQL statements:</span></span>  
  
    ```sql  
    -- Begin the transaction.  
    BEGIN TRAN  
    GO  
    -- set the XML value field for the row with name=ServerLogging  
    update DQS_MAIN.dbo.A_CONFIGURATION   
    set VALUE='<configuration>  
      <configSections>  
        <section name="loggingConfiguration" type="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.LoggingSettings, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" />  
      </configSections>  
      <loggingConfiguration name="Logging Application Block" tracingEnabled="true" defaultCategory="" logWarningsWhenNoCategoriesMatch="true">  
        <listeners>  
          <add fileName="###REPLACE_THIS_WITH_SQL_SERVER_INSTANCE_LOG_FOLDER_NAME###DQServerLog.###REPLACE_THIS_WITH_SQL_CATALOG_NAME###.log" footer="" formatter="Custom Text Formatter" header="" rollFileExistsBehavior="Increment" rollInterval="None" rollSizeKB="25000" timeStampPattern="yyyy-MM-dd" listenerDataType="Microsoft.Practices.EnterpriseLibrary.Logging.Configuration.RollingFlatFileTraceListenerData, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" traceOutputOptions="None" filter="All" type="Microsoft.Practices.EnterpriseLibrary.Logging.TraceListeners.RollingFlatFileTraceListener, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Rolling Flat File Trace Listener" />  
        </listeners>  
        <formatters>  
          <add template="{timestamp(local)}|[{threadName}]|{dictionary({value}|)}{message}" type="Microsoft.Practices.EnterpriseLibrary.Logging.Formatters.TextFormatter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="Custom Text Formatter" />  
        </formatters>  
        <logFilters>  
          <add enabled="true" type="Microsoft.Practices.EnterpriseLibrary.Logging.Filters.LogEnabledFilter, Microsoft.Practices.EnterpriseLibrary.Logging, Version=4.1.0.0, Culture=neutral, PublicKeyToken=e44a2bc38ed2c13c" name="LogEnabled Filter" />  
        </logFilters>  
        <categorySources />  
        <specialSources>  
          <allEvents switchValue="All" name="All Events" />  
          <notProcessed switchValue="All" name="Unprocessed Category" />  
          <errors switchValue="All" name="Logging Errors & Warnings">  
            <listeners>  
              <add name="Rolling Flat File Trace Listener" />  
            </listeners>  
          </errors>  
        </specialSources>  
      </loggingConfiguration>  
    </configuration>'  
    WHERE NAME='ServerLogging'  
    GO  
    -- check the result  
    select * from DQS_MAIN.dbo.A_CONFIGURATION where NAME='ServerLogging'  
  
    -- Commit the transaction.  
    COMMIT TRAN  
  
    ```  
  
4.  <span data-ttu-id="e25d2-118">F5 キーを押してステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-118">Press F5 to execute the statements.</span></span> <span data-ttu-id="e25d2-119">**[結果]** ペインを確認してステートメントが正常に実行されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-119">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
5.  <span data-ttu-id="e25d2-120">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] のログ構成の変更を適用するには、次の Transact-SQL ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e25d2-120">To apply changes done to the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging configuration, you must run the following Transact-SQL statements.</span></span> <span data-ttu-id="e25d2-121">新しいクエリ エディター ウィンドウを開き、次の Transact-SQL ステートメントを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e25d2-121">Open a new Query Editor window, and paste the following Transact-SQL statements:</span></span>  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    DECLARE @return_value int  
    EXEC @return_value = [internal_core].[RefreshLogSettings]  
    SELECT 'Return Value' = @return_value  
    GO  
    ```  
  
6.  <span data-ttu-id="e25d2-122">F5 キーを押してステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-122">Press F5 to execute the statements.</span></span> <span data-ttu-id="e25d2-123">**[結果]** ペインを確認してステートメントが正常に実行されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-123">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e25d2-124">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] のログ設定の構成が動的に生成されて、DQS_MAIN.Log ファイルに保存されます。SQL Server の既定のインスタンスをインストールした場合、このファイルは通常 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log に保存されています。</span><span class="sxs-lookup"><span data-stu-id="e25d2-124">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] logging settings configuration is dynamically generated and stored in the DQS_MAIN.Log file, which is typically available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log if you installed the default instance of SQL Server.</span></span> <span data-ttu-id="e25d2-125">ただし、このファイルで直接変更した内容は保持されず、DQS_MAIN データベースの A_CONFIGURATION テーブルの構成設定で上書きされます。</span><span class="sxs-lookup"><span data-stu-id="e25d2-125">However, changes done directly in this file do not hold, and are overwritten by the configuration settings in the A_CONFIGURATION table in the DQS_MAIN database.</span></span>  
  
##  <a name="configure-data-quality-client-log-settings"></a><a name="DQSClient"></a><span data-ttu-id="e25d2-126">Data Quality Client ログ設定の構成</span><span class="sxs-lookup"><span data-stu-id="e25d2-126">Configure Data Quality Client Log Settings</span></span>  
 <span data-ttu-id="e25d2-127">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]ログ設定の構成ファイルである DQLog.Client.xml は、通常、C:\Program モジュールで使用できます (& d)。XML ファイルの内容は、前にログ構成設定で変更した XML ファイルに似てい [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e25d2-127">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log setting configuration file, DQLog.Client.xml, is typically available at C:\Program Files\Microsoft SQL Server\120\Tools\Binn\DQ\config. The contents of the XML file is similar to the XML file that you modified earlier for the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log configuration settings.</span></span> <span data-ttu-id="e25d2-128">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のログ設定を構成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-128">To configure the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log settings:</span></span>  
  
1.  <span data-ttu-id="e25d2-129">管理者として、任意の XML 編集ツールやメモ帳を実行します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-129">Run any XML editing tool or notepad as an administrator.</span></span>  
  
2.  <span data-ttu-id="e25d2-130">DQLog.Client.xml ファイルをツールやメモ帳で開きます。</span><span class="sxs-lookup"><span data-stu-id="e25d2-130">Open the DQLog.Client.xml file in the tool or notepad.</span></span>  
  
3.  <span data-ttu-id="e25d2-131">必要な変更を行い、ファイルを保存して、新しいログの変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="e25d2-131">Make the required changes, and save the file to apply the new logging changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25d2-132">参照</span><span class="sxs-lookup"><span data-stu-id="e25d2-132">See Also</span></span>  
 [<span data-ttu-id="e25d2-133">DQS ログ ファイルの重大度レベルの構成</span><span class="sxs-lookup"><span data-stu-id="e25d2-133">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)  
  
  
