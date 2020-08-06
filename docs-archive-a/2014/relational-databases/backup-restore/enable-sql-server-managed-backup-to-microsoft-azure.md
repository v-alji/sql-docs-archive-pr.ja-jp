---
title: Azure への SQL Server マネージバックアップの設定 |Microsoft Docs
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b9e3b86fde91028106263310aad8a1952fc041a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644485"
---
# <a name="setting-up-sql-server-managed-backup-to-azure"></a><span data-ttu-id="6254a-102">Azure への SQL Server マネージド バックアップの設定</span><span class="sxs-lookup"><span data-stu-id="6254a-102">Setting up SQL Server Managed Backup to Azure</span></span>
  <span data-ttu-id="6254a-103">このトピックには、次の 2 つのチュートリアルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6254a-103">This topic includes two tutorials:</span></span>  
  
 <span data-ttu-id="6254a-104">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]をデータベース レベルで設定し、電子メール通知を有効にして、バックアップ処理を監視します。</span><span class="sxs-lookup"><span data-stu-id="6254a-104">Set up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the database level, enable email notification, and monitor backup activity.</span></span>  
  
 <span data-ttu-id="6254a-105">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]をインスタンス レベルで設定し、電子メール通知を有効にして、バックアップ処理を監視します。</span><span class="sxs-lookup"><span data-stu-id="6254a-105">Setting up  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the instance level, enable email notification, and monitor backup activity.</span></span>  
  
 <span data-ttu-id="6254a-106">可用性グループの設定に関するチュートリアルについ [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ては、「[可用性グループの Microsoft Azure するための SQL Server マネージバックアップの設定](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-106">For a tutorial on setting up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for Availability Groups, see [Setting up SQL Server Managed Backup to Microsoft Azure for Availability Groups](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
## <a name="setting-up-ss_smartbackup"></a><span data-ttu-id="6254a-107">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の設定</span><span class="sxs-lookup"><span data-stu-id="6254a-107">Setting Up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]</span></span>  
  
### <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><span data-ttu-id="6254a-108">データベースに対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] を有効にして構成する</span><span class="sxs-lookup"><span data-stu-id="6254a-108">Enable and Configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a Database</span></span>  
 <span data-ttu-id="6254a-109">このチュートリアルでは、データベース (TestDB) に対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効にして構成するために必要な手順の後、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の正常性状態の監視を有効にする手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="6254a-109">This tutorial describes the steps necessary to enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a database (TestDB), followed by steps to enable monitoring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
 <span data-ttu-id="6254a-110">**アクセス許可:**</span><span class="sxs-lookup"><span data-stu-id="6254a-110">**Permissions:**</span></span>  
  
-   <span data-ttu-id="6254a-111">**Db_backupoperator**データベースロールのメンバーシップ、 **ALTER ANY CREDENTIAL**権限、および `EXECUTE` **sp_delete_backuphistory**ストアドプロシージャに対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6254a-111">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="6254a-112">**Smart_admin fn_get_current_xevent_settings**関数に対する**SELECT**権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6254a-112">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="6254a-113">`EXECUTE` **Smart_admin sp_get_backup_diagnostics**ストアドプロシージャに対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6254a-113">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="6254a-114">さらに、`VIEW SERVER STATE` 権限も必要です (この権限を必要とする他のシステム オブジェクトを内部的に呼び出すため)。</span><span class="sxs-lookup"><span data-stu-id="6254a-114">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  
  
-   <span data-ttu-id="6254a-115">`EXECUTE` `smart_admin.sp_set_instance_backup` ストアドプロシージャおよびストアドプロシージャに対する権限が必要です `smart_admin.sp_backup_master_switch` 。</span><span class="sxs-lookup"><span data-stu-id="6254a-115">Requires `EXECUTE` permissions on the `smart_admin.sp_set_instance_backup` and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  


1.  <span data-ttu-id="6254a-116">**Microsoft Azure ストレージアカウントを作成します。** バックアップは Microsoft Azure ストレージサービスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-116">**Create a Microsoft Azure storage account:** The backups are stored in the Microsoft Azure storage service.</span></span> <span data-ttu-id="6254a-117">まだアカウントを持っていない場合は、まず Microsoft Azure ストレージアカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-117">You must first create a Microsoft Azure storage account, if you do not already have an account.</span></span>
    - <span data-ttu-id="6254a-118">SQL Server 2014 では、ブロック blob と追加 blob とは異なるページ blob が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-118">SQL Server 2014 uses page blobs, which are different than block and append blobs.</span></span> <span data-ttu-id="6254a-119">そのため、blob アカウントではなく、汎用アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-119">Therefore you must create a general purpose account, and not a blob account.</span></span> <span data-ttu-id="6254a-120">詳細については、「[Azure ストレージ アカウントについて](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-120">For more information, see [About Azure storage accounts](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span>
    - <span data-ttu-id="6254a-121">ストレージ アカウント名およびアクセス キーをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="6254a-121">Make a note of the storage account name, and the access keys.</span></span> <span data-ttu-id="6254a-122">ストレージ アカウント名およびアクセス キー情報は、SQL 資格情報の作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="6254a-122">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="6254a-123">ストレージアカウントに対する認証には、SQL 資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-123">The SQL Credential is used to authenticate to the storage account.</span></span>  
 
2.  <span data-ttu-id="6254a-124">**SQL 資格情報を作成します。** Id としてストレージアカウントの名前を使用し、パスワードとしてストレージアクセスキーを使用して、SQL 資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="6254a-124">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="6254a-125">**SQL Server エージェントサービスが開始され、実行されていることを確認します。** 現在実行されていない場合は SQL Server エージェントを開始します。</span><span class="sxs-lookup"><span data-stu-id="6254a-125">**Ensure SQL Server Agent service is Started and Running:**  Start SQL Server Agent if it is not currently running.</span></span>  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="6254a-126">でバックアップ操作を実行するには、SQL Server エージェントがインスタンスで実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-126">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="6254a-127">バックアップ操作を定期的に実行できるように、SQL Server エージェントの自動的な実行を設定できます。</span><span class="sxs-lookup"><span data-stu-id="6254a-127">You may want to set SQL Server Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="6254a-128">**保有期間を決定する:** バックアップ ファイルに必要な保有期間を決定します。</span><span class="sxs-lookup"><span data-stu-id="6254a-128">**Determine the retention period:** Determine the retention period for the backup files.</span></span> <span data-ttu-id="6254a-129">保有期間は日数で指定し、その範囲は 1 ～ 30 になります。</span><span class="sxs-lookup"><span data-stu-id="6254a-129">The retention period is specified in days and can range from 1 to 30.</span></span>  
  
5.  <span data-ttu-id="6254a-130">**を有効にして構成する [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** SQL Server Management Studio を開始し、データベースがインストールされているインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6254a-130">**Enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Start SQL Server Management Studio and connect to the instance where the database is installed.</span></span> <span data-ttu-id="6254a-131">要件に合わせて、データベース名、SQL 資格情報、保有期間、および暗号化オプションの値を変更した後、クエリ ウィンドウから次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6254a-131">From the query window run the following statement after you modify the values for the database name, SQL Credential, retention period, and encryption options per your requirements:</span></span>  
  
     <span data-ttu-id="6254a-132">暗号化用の証明書の作成の詳細については、「[暗号化されたバックアップを作成](create-an-encrypted-backup.md)する」の「**バックアップ証明書**の作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-132">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="6254a-133">は、指定したデータベースで有効になります。</span><span class="sxs-lookup"><span data-stu-id="6254a-133">is now enabled on the database you specified.</span></span> <span data-ttu-id="6254a-134">データベースでのバックアップ操作の実行が開始されるまで最大 15 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-134">It may take up to 15 minutes for the backup operations on the database to start to run.</span></span>  
  
6.  <span data-ttu-id="6254a-135">**拡張イベントの既定の構成を確認する:** 次の Transact-SQL ステートメントを実行して、拡張イベントの設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="6254a-135">**Review Extended Event Default Configuration:** Review the Extended Event settings by running the following transact-SQL statement.</span></span>  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     <span data-ttu-id="6254a-136">管理、運用、および分析のチャネル イベントは既定で有効になっていて、無効にできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-136">You should see that Admin, Operational, and Analytical channel events are enabled by default and cannot be disabled.</span></span> <span data-ttu-id="6254a-137">手動の介入を必要とするイベントを監視するには、これで十分です。</span><span class="sxs-lookup"><span data-stu-id="6254a-137">This should be sufficient to monitor the events that require manual intervention.</span></span>  <span data-ttu-id="6254a-138">デバッグ イベントを有効にすることはできますが、デバッグ チャネルには、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] が問題の検出および解決に使用する情報イベントとデバッグ イベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6254a-138">You can enable debug events, but the debug channels include informational and debug events that [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] uses to detect issues and solve them.</span></span> <span data-ttu-id="6254a-139">詳細については、「 [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-139">For more information, see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
7.  <span data-ttu-id="6254a-140">**正常性状態の通知を有効化し、構成する:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]Microsoft Azure への SQL Server マネージド バックアップには、注意を要するエラーまたは警告の電子メール通知を送信するためにエージェント ジョブを作成するストアド プロシージャがあります。</span><span class="sxs-lookup"><span data-stu-id="6254a-140">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span> <span data-ttu-id="6254a-141">次の手順では、電子メール通知を有効にして構成するためのプロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="6254a-141">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="6254a-142">データベース メールがインスタンス上でまだ有効になっていない場合は設定します。</span><span class="sxs-lookup"><span data-stu-id="6254a-142">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="6254a-143">詳細については、「 [Configure Database Mail](../database-mail/configure-database-mail.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-143">For more information, see [Configure Database Mail](../database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="6254a-144">データベース メールを使用するように SQL Server エージェント通知を構成します。</span><span class="sxs-lookup"><span data-stu-id="6254a-144">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="6254a-145">詳細については、「 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-145">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="6254a-146">**電子メール通知を有効にして、バックアップ エラーおよび警告を受け取る:** クエリ ウィンドウから、次の Transact-SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6254a-146">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
         <span data-ttu-id="6254a-147">詳細と完全なサンプルスクリプトについては、「 [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-147">For more information, and a full sample script see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
8.  <span data-ttu-id="6254a-148">**Microsoft Azure ストレージ アカウントでバックアップ ファイルを表示する:** SQL Server Management Studio または Azure 管理ポータルから、ストレージ アカウントに接続します。</span><span class="sxs-lookup"><span data-stu-id="6254a-148">**View backup files in the Microsoft Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="6254a-149">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を使用するように構成したデータベースをホストする SQL Server インスタンスのコンテナーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-149">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="6254a-150">また、データベースに対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効にしてから 15 分以内のデータベースとログ バックアップも表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-150">You may also see a database and a log backup within 15 minutes of enabling [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the database.</span></span>  
  
9. <span data-ttu-id="6254a-151">**正常性状態を監視する:** 前の手順で構成した電子メール通知から監視するか、ログに記録されているイベントをアクティブに監視することができます。</span><span class="sxs-lookup"><span data-stu-id="6254a-151">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="6254a-152">イベントを表示するための Transact-SQL ステートメントのいくつかの例を示します。</span><span class="sxs-lookup"><span data-stu-id="6254a-152">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 <span data-ttu-id="6254a-153">このセクションで説明した手順は、データベースで初めて [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] を構成するための特別な手順です。</span><span class="sxs-lookup"><span data-stu-id="6254a-153">The steps described in this section are specifically for configuring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the first time on the database.</span></span> <span data-ttu-id="6254a-154">同じシステムストアドプロシージャ**smart_admin sp_set_db_backup**を使用して既存の構成を変更し、新しい値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="6254a-154">You can modify the existing configurations using the same system stored procedure **smart_admin.sp_set_db_backup** and provide the new values.</span></span> <span data-ttu-id="6254a-155">詳細については、「SQL Server 管理されている[バックアップから Microsoft Azure-保有期間とストレージの設定](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-155">For more information, see [SQL Server Managed Backup to Microsoft Azure - Retention and Storage Settings](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).</span></span>  
  
### <a name="enable-ss_smartbackup-for-the-instance-with-default-settings"></a><span data-ttu-id="6254a-156">既定の設定を使用してインスタンスの [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効にする</span><span class="sxs-lookup"><span data-stu-id="6254a-156">Enable [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the Instance with Default Settings</span></span>  
 <span data-ttu-id="6254a-157">このチュートリアルでは、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] インスタンス ' MyInstance ' に対してを有効にして構成する手順について説明し \\ ます。</span><span class="sxs-lookup"><span data-stu-id="6254a-157">This tutorial describes the steps to enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the instance, 'MyInstance',\\.</span></span> <span data-ttu-id="6254a-158">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] の正常性状態の監視を有効にするための手順も含まれています。</span><span class="sxs-lookup"><span data-stu-id="6254a-158">It includes steps to enable monitoring the [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
 <span data-ttu-id="6254a-159">**アクセス許可:**</span><span class="sxs-lookup"><span data-stu-id="6254a-159">**Permissions:**</span></span>  
  
-   <span data-ttu-id="6254a-160">**Db_backupoperator**データベースロールのメンバーシップ、 **ALTER ANY CREDENTIAL**権限、および `EXECUTE` **sp_delete_backuphistory**ストアドプロシージャに対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6254a-160">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="6254a-161">**Smart_admin fn_get_current_xevent_settings**関数に対する**SELECT**権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6254a-161">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="6254a-162">`EXECUTE` **Smart_admin sp_get_backup_diagnostics**ストアドプロシージャに対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6254a-162">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="6254a-163">さらに、`VIEW SERVER STATE` 権限も必要です (この権限を必要とする他のシステム オブジェクトを内部的に呼び出すため)。</span><span class="sxs-lookup"><span data-stu-id="6254a-163">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  


1.  <span data-ttu-id="6254a-164">**Microsoft Azure ストレージアカウントを作成します。** バックアップは Microsoft Azure ストレージサービスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-164">**Create a Microsoft Azure storage account:** The backups are stored in the Microsoft Azure storage service.</span></span> <span data-ttu-id="6254a-165">まだアカウントを持っていない場合は、まず Microsoft Azure ストレージアカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-165">You must first create a Microsoft Azure storage account, if you do not already have an account.</span></span>
    - <span data-ttu-id="6254a-166">SQL Server 2014 では、ブロック blob と追加 blob とは異なるページ blob が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-166">SQL Server 2014 uses page blobs, which are different than block and append blobs.</span></span> <span data-ttu-id="6254a-167">そのため、blob アカウントではなく、汎用アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-167">Therefore you must create a general purpose account, and not a blob account.</span></span> <span data-ttu-id="6254a-168">詳細については、「[Azure ストレージ アカウントについて](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-168">For more information, see [About Azure storage accounts](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span>
    - <span data-ttu-id="6254a-169">ストレージ アカウント名およびアクセス キーをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="6254a-169">Make a note of the storage account name, and the access keys.</span></span> <span data-ttu-id="6254a-170">ストレージ アカウント名およびアクセス キー情報は、SQL 資格情報の作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="6254a-170">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="6254a-171">ストレージアカウントに対する認証には、SQL 資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-171">The SQL Credential is used to authenticate to the storage account.</span></span>  
  
2.  <span data-ttu-id="6254a-172">**SQL 資格情報を作成します。** Id としてストレージアカウントの名前を使用し、パスワードとしてストレージアクセスキーを使用して、SQL 資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="6254a-172">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="6254a-173">**SQL Server エージェント サービスが開始され、実行されていることを確認する:** SQL Server エージェントを開始します (現在実行されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="6254a-173">**Ensure SQL Server Agent service is Started and Running:** Start SQL Server Agent if it is not currently running.</span></span> [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="6254a-174">でバックアップ操作を実行するには、SQL Server エージェントがインスタンスで実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-174">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="6254a-175">バックアップ操作を定期的に実行できるように、SQL Server エージェントの自動的な実行を設定できます。</span><span class="sxs-lookup"><span data-stu-id="6254a-175">You may want to set SQL Server Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="6254a-176">**保有期間を決定する:** バックアップ ファイルに必要な保有期間を決定します。</span><span class="sxs-lookup"><span data-stu-id="6254a-176">**Determine the retention period:** Determine the retention period for the backup files.</span></span> <span data-ttu-id="6254a-177">保有期間は日数で指定し、その範囲は 1 ～ 30 になります。</span><span class="sxs-lookup"><span data-stu-id="6254a-177">The retention period is specified in days and can range from 1 to 30.</span></span> <span data-ttu-id="6254a-178">インスタンス レベルで既定値を使用して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効にすると、その後作成されたすべての新しいデータベースに、設定が継承されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-178">Once [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] is enabled at the instance level with the defaults all new databases created thereafter will inherit the settings.</span></span> <span data-ttu-id="6254a-179">完全または一括ログ復旧モデルに設定されているデータベースのみがサポートされており、自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-179">Only databases that are set to full or bulk-logged recovery models are supported and will be configured automatically.</span></span> <span data-ttu-id="6254a-180">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を構成する必要がなければ、特定のデータベースの [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]をいつでも無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="6254a-180">You may disable [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a specific database at any time if you  do not want [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configured.</span></span> <span data-ttu-id="6254a-181">また、データベース レベルで [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を構成することで、特定のデータベースの構成を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="6254a-181">You can also change the configuration for a specific database by configuring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the database level.</span></span>  
  
5.  <span data-ttu-id="6254a-182">**を有効にして構成する [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** SQL Server Management Studio を開始し、SQL Server のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6254a-182">**Enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Start SQL Server Management Studio and connect to the instance of SQL Server.</span></span> <span data-ttu-id="6254a-183">要件に応じて、データベース名、SQL 資格情報、保有期間、および暗号化オプションの値を変更した後、クエリウィンドウから次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6254a-183">From the query window run the following statement after you modify the values for the database name, SQL Credential, retention period, and the encryption options per your requirements:</span></span>  
  
     <span data-ttu-id="6254a-184">暗号化用の証明書の作成の詳細については、「[暗号化されたバックアップを作成](create-an-encrypted-backup.md)する」の「**バックアップ証明書**の作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-184">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
    ```  
    Use msdb;  
    Go  
       EXEC smart_admin.sp_set_instance_backup  
                     @enable_backup=1  
                    ,@retention_days=30   
                    ,@credential_name='sqlbackuptoURL'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert';  
    GO  
  
    ```  
  
     <span data-ttu-id="6254a-185">これで、インスタンス上で [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]が有効になります。</span><span class="sxs-lookup"><span data-stu-id="6254a-185">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] is now enabled on the instance.</span></span>  
  
6.  <span data-ttu-id="6254a-186">次の Transact-SQL ステートメントを実行して、構成設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="6254a-186">Verify the configuration settings by running the following Transact-SQL statement:</span></span>  
  
    ```  
    Use msdb;  
    GO  
    SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
    ```  
  
7.  <span data-ttu-id="6254a-187">インスタンス上に新しいデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="6254a-187">Create a new database on the instance.</span></span> <span data-ttu-id="6254a-188">次の Transact-SQL ステートメントを実行して、データベースの [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の構成設定を表示します。</span><span class="sxs-lookup"><span data-stu-id="6254a-188">Run the following Transact-SQL statement to view the [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configuration settings for the database:</span></span>  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('NewDB')  
    ```  
  
     <span data-ttu-id="6254a-189">設定が表示され、データベースでのバックアップ操作の実行が開始されるまで最大 15 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-189">It may take up to 15 minutes for the settings to show and backup operations on the database to start to run.</span></span>  
  
8.  <span data-ttu-id="6254a-190">**正常性状態の通知を有効化し、構成する:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]Microsoft Azure への SQL Server マネージド バックアップには、注意を要するエラーまたは警告の電子メール通知を送信するためにエージェント ジョブを作成するストアド プロシージャがあります。</span><span class="sxs-lookup"><span data-stu-id="6254a-190">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span>  <span data-ttu-id="6254a-191">このような通知を受信するには、SQL Server エージェント ジョブを作成するストアド プロシージャの実行を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-191">To receive such notifications, you must enable run the stored procedure which creates a SQL Server Agent Job.</span></span> <span data-ttu-id="6254a-192">次の手順では、電子メール通知を有効にして構成するためのプロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="6254a-192">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="6254a-193">データベース メールがインスタンス上でまだ有効になっていない場合は設定します。</span><span class="sxs-lookup"><span data-stu-id="6254a-193">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="6254a-194">詳細については、「 [Configure Database Mail](../database-mail/configure-database-mail.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-194">For more information, see [Configure Database Mail](../database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="6254a-195">データベース メールを使用するように SQL Server エージェント通知を構成します。</span><span class="sxs-lookup"><span data-stu-id="6254a-195">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="6254a-196">詳細については、「 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-196">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="6254a-197">**電子メール通知を有効にして、バックアップ エラーおよび警告を受け取る:** クエリ ウィンドウから、次の Transact-SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="6254a-197">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email address>'  
  
        ```  
  
         <span data-ttu-id="6254a-198">監視方法の詳細と完全なサンプルスクリプトについては、「 [monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-198">For more information about how to monitor, and a full sample script see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
9. <span data-ttu-id="6254a-199">**Microsoft Azure ストレージ アカウントでバックアップ ファイルを表示する:** SQL Server Management Studio または Azure 管理ポータルから、ストレージ アカウントに接続します。</span><span class="sxs-lookup"><span data-stu-id="6254a-199">**View backup files in the Microsoft Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="6254a-200">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を使用するように構成したデータベースをホストする SQL Server インスタンスのコンテナーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6254a-200">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="6254a-201">また、新しいデータベースを作成してから 15 分以内のデータベースとログ バックアップも表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="6254a-201">You may also see a database and a log backup within 15 minutes of creating a new database.</span></span>  
  
10. <span data-ttu-id="6254a-202">**正常性状態を監視する:** 前の手順で構成した電子メール通知から監視するか、ログに記録されているイベントをアクティブに監視することができます。</span><span class="sxs-lookup"><span data-stu-id="6254a-202">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="6254a-203">イベントを表示するための Transact-SQL ステートメントのいくつかの例を示します。</span><span class="sxs-lookup"><span data-stu-id="6254a-203">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]<span data-ttu-id="6254a-204">の既定の設定は、明示的にデータベース レベルで設定を構成することで、特定のデータベースに対してオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="6254a-204">default settings can be overridden for a specific database by configuring the settings specifically at the database level.</span></span> <span data-ttu-id="6254a-205">また、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] サービスを一時停止および再開することもできます。</span><span class="sxs-lookup"><span data-stu-id="6254a-205">You can also pause and resume [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] service temporarily.</span></span> <span data-ttu-id="6254a-206">詳細については、「 [Microsoft Azure への管理](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)されたバックアップの SQL Server」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6254a-206">For more information, see [SQL Server Managed Backup to Microsoft Azure - Retention and Storage Settings](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)</span></span>  
  
  
