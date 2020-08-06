---
title: SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06127b5e4b422750554c30fae23b6190107cb643
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642135"
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a><span data-ttu-id="5f967-102">SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5f967-102">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>
  <span data-ttu-id="5f967-103">このトピックでは、Azure Blob service との間の SQL Server のバックアップと復元に関するベスト プラクティスとトラブルシューティングのヒントを示します。</span><span class="sxs-lookup"><span data-stu-id="5f967-103">This topic includes best practices and troubleshooting tips for SQL Server backup and restores to the Azure Blob service.</span></span>  
  
 <span data-ttu-id="5f967-104">SQL Server のバックアップ操作または復元操作に Azure Blob Storage サービスを使用する方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f967-104">For more information about using Azure Blob storage service for SQL Server backup or restore operations, see:</span></span>  
  
-   [<span data-ttu-id="5f967-105">Azure Blob Storage サービスを使った SQL Server のバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="5f967-105">SQL Server Backup and Restore with Azure Blob Storage Service</span></span>](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [<span data-ttu-id="5f967-106">チュートリアル:Azure Blob Storage サービスへの SQL Server のバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="5f967-106">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a><span data-ttu-id="5f967-107">バックアップの管理</span><span class="sxs-lookup"><span data-stu-id="5f967-107">Managing Backups</span></span>  
 <span data-ttu-id="5f967-108">バックアップを管理するための一般的な推奨事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5f967-108">The following list includes general recommendations to manage backups:</span></span>  
  
-   <span data-ttu-id="5f967-109">BLOB を誤って上書きしないように、各バックアップに一意なファイル名を付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5f967-109">Unique file name for every backup is recommended to prevent accidentally overwriting the blobs.</span></span>  
  
-   <span data-ttu-id="5f967-110">コンテナーを作成する際は、アクセス レベルを **private**に設定し、必要な認証情報を指定できるユーザーまたはアカウントだけがコンテナー内の BLOB の読み取りや書き込みを実行できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5f967-110">When creating a container, it is recommended that you set the access level to **private**, so only users or accounts that can provide the required authentication information can read or write the blobs in the container.</span></span>  
  
-   <span data-ttu-id="5f967-111">Azure 仮想マシンで実行されている SQL Server のインスタンス上のデータベースの SQL Server については、リージョン間のデータ転送コストを回避するために、仮想マシンと同じリージョンのストレージアカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f967-111">For SQL Server databases on an instance of SQL Server running in an Azure Virtual Machine, use a storage account in the same region as the virtual machine to avoid data transfer costs between regions.</span></span> <span data-ttu-id="5f967-112">また、同じ地域を使用すると、バックアップ操作と復元操作で最適なパフォーマンスを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="5f967-112">Using the same region also ensures optimal performance for backup and restore operations.</span></span>  
  
-   <span data-ttu-id="5f967-113">バックアップ処理に失敗すると、無効なバックアップ ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5f967-113">Failed backup activity can result in an invalid backup file.</span></span> <span data-ttu-id="5f967-114">失敗したバックアップを定期的に確認し、BLOB ファイルを削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5f967-114">We recommend periodic identification of failed backups and deleting the blob files.</span></span> <span data-ttu-id="5f967-115">詳細については、「 [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5f967-115">For more information, see [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)</span></span>  
  
-   <span data-ttu-id="5f967-116">バックアップ中に `WITH COMPRESSION` オプションを使用すると、ストレージ コストとストレージのトランザクション コストを最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="5f967-116">Using the `WITH COMPRESSION` option during backup can minimize your storage costs and storage transaction costs.</span></span> <span data-ttu-id="5f967-117">また、バックアップ プロセスが完了するまでにかかる時間を短縮することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f967-117">It can also decrease the time taken to complete the backup process.</span></span>  
  
## <a name="handling-large-files"></a><span data-ttu-id="5f967-118">大きなファイルの処理</span><span class="sxs-lookup"><span data-stu-id="5f967-118">Handling Large Files</span></span>  
  
-   <span data-ttu-id="5f967-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップ操作では、複数のスレッドを使用して、Azure Blob Storage サービスへのデータ転送が最適化されます。</span><span class="sxs-lookup"><span data-stu-id="5f967-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup operation uses multiple threads to optimize data transfer to Azure Blob storage services.</span></span>  <span data-ttu-id="5f967-120">ただし、パフォーマンスは ISV の帯域幅やデータベースのサイズなどのさまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="5f967-120">However the performance depends on various factors, such as ISV bandwidth and size of the database.</span></span> <span data-ttu-id="5f967-121">内部設置型の SQL Server データベースから大きなデータベースまたはファイル グループをバックアップする場合は、最初にスループットのテストを行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5f967-121">If you plan to back up large databases or filegroups from an on-premise SQL Server database, it is recommended that you do some throughput testing first.</span></span> <span data-ttu-id="5f967-122">[Azure storage の SLA](https://go.microsoft.com/fwlink/?LinkId=271619)には、考慮する必要がある blob の最大処理時間があります。</span><span class="sxs-lookup"><span data-stu-id="5f967-122">[Azure storage SLA's](https://go.microsoft.com/fwlink/?LinkId=271619) have maximum processing times for blobs that you can take into consideration.</span></span>  
  
-   <span data-ttu-id="5f967-123">「**バックアップの管理**」セクションで推奨されているように `WITH COMPRESSION` オプションを使用することは、大きなファイルをバックアップするときに非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="5f967-123">Using the `WITH COMPRESSION` option as recommended in the **Managing Backup** section, it is very important when backing up large files.</span></span>  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a><span data-ttu-id="5f967-124">BACKUP TO URL または RESTORE FROM URL のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5f967-124">Troubleshooting Backup To or Restore from URL</span></span>  
 <span data-ttu-id="5f967-125">ここでは、Azure Blob Storage サービスへのバックアップまたは Azure Blob Storage サービスからの復元を実行するときに発生するエラーを簡単にトラブルシューティングする方法をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="5f967-125">Following are some quick ways to troubleshoot errors when backing up to or restoring from the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="5f967-126">サポートされていないオプションまたは制限事項によるエラーを回避するには、「 [Azure Blob Storage サービスを使用したバックアップと復元 SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) 」の記事に記載されている制限事項の一覧および backup コマンドと restore コマンドのサポートに関する情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f967-126">To avoid errors due to unsupported options or limitations, review the list of limitations, and support for BACKUP and RESTORE commands information in the [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) article.</span></span>  
  
 <span data-ttu-id="5f967-127">**認証エラー:**</span><span class="sxs-lookup"><span data-stu-id="5f967-127">**Authentication Errors:**</span></span>  
  
-   <span data-ttu-id="5f967-128">WITH CREDENTIAL は新しいオプションで、Azure Blob ストレージサービスとの間でバックアップまたは復元を行うために必要です。</span><span class="sxs-lookup"><span data-stu-id="5f967-128">WITH CREDENTIAL is a new option and required to back up to or restore from the Azure Blob storage service.</span></span> <span data-ttu-id="5f967-129">資格情報に関連するエラーには、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="5f967-129">Failures related to credential could be the following:</span></span>  
  
     <span data-ttu-id="5f967-130">`BACKUP` コマンドまたは `RESTORE` コマンドで指定された資格情報が存在しません。</span><span class="sxs-lookup"><span data-stu-id="5f967-130">The credential specified in the `BACKUP` or `RESTORE` command does not exist.</span></span> <span data-ttu-id="5f967-131">この問題を回避するには、資格情報が BACKUP ステートメントに存在しない場合に資格情報を作成する T-SQL ステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5f967-131">To avoid this issue, you can include T-SQL statements to create the credential if one does not exist in the backup statement.</span></span> <span data-ttu-id="5f967-132">使用可能な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5f967-132">The following is an example you can use:</span></span>  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   <span data-ttu-id="5f967-133">資格情報は存在しますが、BACKUP コマンドの実行に使用されるログイン アカウントに資格情報へのアクセス権限がありません。</span><span class="sxs-lookup"><span data-stu-id="5f967-133">The credential exists but the login account that is used to run the backup command does not have permissions to access the credentials.</span></span> <span data-ttu-id="5f967-134">**Alter any credential** 権限がある **db_backupoperator** ロールのログイン アカウントを使用してください。</span><span class="sxs-lookup"><span data-stu-id="5f967-134">Use a login account in the **db_backupoperator** role with **Alter any credential** permissions.</span></span>  
  
-   <span data-ttu-id="5f967-135">ストレージ アカウントの名前とキーの値を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5f967-135">Verify the storage account name and key values.</span></span> <span data-ttu-id="5f967-136">資格情報に格納されている情報は、バックアップ操作と復元操作で使用する Azure ストレージ アカウントのプロパティの値と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f967-136">The information stored in the credential must match the property values of the Azure storage account you are using in the backup and restore operations.</span></span>  
  
 <span data-ttu-id="5f967-137">**バックアップ エラー/障害:**</span><span class="sxs-lookup"><span data-stu-id="5f967-137">**Backup Errors/Failures:**</span></span>  
  
-   <span data-ttu-id="5f967-138">同じ BLOB への並列バックアップを実行すると、バックアップの 1 つが " **初期化に失敗しました** " エラーで失敗します。</span><span class="sxs-lookup"><span data-stu-id="5f967-138">Parallel backups to the same blob cause one of the backups to fail with an **Initialization failed** error.</span></span>  
  
-   <span data-ttu-id="5f967-139">次のエラー ログを使用して、バックアップ エラーのトラブルシューティングに役立ててください。</span><span class="sxs-lookup"><span data-stu-id="5f967-139">Use the following error logs to help with troubleshooting backup errors:</span></span>  
  
    -   <span data-ttu-id="5f967-140">トレース フラグ 3051 を設定して、次の形式の特定のエラー ログへの記録を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5f967-140">Set trace flag 3051 to turn on logging to a specific error log with the following format in:</span></span>  
  
         <span data-ttu-id="5f967-141">BackupToUrl- \<instname> - \<dbname> -action- \<PID> .log \<action> は次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="5f967-141">BackupToUrl-\<instname>-\<dbname>-action-\<PID>.log Where \<action> is one of:</span></span>  
  
        -   `DB`  
  
        -   `FILELISTONLY`  
  
        -   `LABELONLY`  
  
        -   `HEADERONLY`  
  
        -   `VERIFYONLY`  
  
    -   <span data-ttu-id="5f967-142">"SQLBackupToUrl" という名前の [アプリケーションログ] の下にある Windows イベントログを確認して、情報を検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f967-142">You can also find information by reviewing the Windows Event Log - Under Application logs with the name 'SQLBackupToUrl'.</span></span>  
  
-   <span data-ttu-id="5f967-143">圧縮されたバックアップから復元するときに、次のエラーが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f967-143">When restoring from a compressed backup, you might see the following error:</span></span>  
  
    -   <span data-ttu-id="5f967-144">**SqlException 3284 が発生しました。重大度:16、状態: 5**</span><span class="sxs-lookup"><span data-stu-id="5f967-144">**SqlException 3284 occurred. Severity: 16 State: 5**</span></span>  
        <span data-ttu-id="5f967-145">**デバイス ' ' のメッセージマーク https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak は、アラインされていません。Backupset の作成に使用したのと同じブロックサイズを使用して Restore ステートメントを再実行してください: ' 65536 ' は、可能な値のように見えます。**</span><span class="sxs-lookup"><span data-stu-id="5f967-145">**Message Filemark on device 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak' is not aligned. Reissue the Restore statement with the same block size used to create the backupset: '65536' looks like a possible value.**</span></span>  
  
         <span data-ttu-id="5f967-146">このエラーを解決するには、`BACKUP` を指定した `BLOCKSIZE = 65536` ステートメントを再実行してください。</span><span class="sxs-lookup"><span data-stu-id="5f967-146">To solve this error, reissue the `BACKUP` statement with `BLOCKSIZE = 65536` specified.</span></span>  
  
-   <span data-ttu-id="5f967-147">アクティブなリースを保持している BLOB が原因でバックアップ中に発生するエラー:バックアップ処理に失敗すると、アクティブなリースを保持する BLOB が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5f967-147">Error during backup due to blobs that have active lease on them: Failed backup activity can result in blobs with active leases.</span></span>  
  
     <span data-ttu-id="5f967-148">BACKUP ステートメントが再実行されると、バックアップ操作が次のようなエラーで失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="5f967-148">If a backup statement is reattempted, backup operation might fail with an error similar to the following:</span></span>  
  
     <span data-ttu-id="5f967-149">**Backup to URL はリモート エンドポイントから例外を受け取りました。例外メッセージ: リモート サーバーからエラーが返されました: (412) 現在 BLOB にリースがありますが、要求にリース ID が指定されていません**。</span><span class="sxs-lookup"><span data-stu-id="5f967-149">**Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (412) There is currently a lease on the blob and no lease ID was specified in the request**.</span></span>  
  
     <span data-ttu-id="5f967-150">アクティブなリースを保持しているバックアップ BLOB ファイルに対して RESTORE ステートメントが実行されると、復元操作は次のようなエラーで失敗します。</span><span class="sxs-lookup"><span data-stu-id="5f967-150">If a restore statement is attempted on a backup blob file that has an active lease, the restore operation fails with an error similar to the following:</span></span>  
  
     <span data-ttu-id="5f967-151">**例外メッセージ: リモート サーバーからエラーが返されました: (409) 競合。**</span><span class="sxs-lookup"><span data-stu-id="5f967-151">**Exception Message: The remote server returned an error: (409) Conflict..**</span></span>  
  
     <span data-ttu-id="5f967-152">このようなエラーが発生した場合は、BLOB ファイルを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f967-152">When such error occurs, the blob files need to be deleted.</span></span> <span data-ttu-id="5f967-153">このシナリオの詳細とこの問題の解決方法については、「 [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f967-153">For more information on this scenario and how to correct this problem, see [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)</span></span>  
  
## <a name="proxy-errors"></a><span data-ttu-id="5f967-154">プロキシ エラー</span><span class="sxs-lookup"><span data-stu-id="5f967-154">Proxy Errors</span></span>  
 <span data-ttu-id="5f967-155">インターネットへのアクセスにプロキシ サーバーを使用している場合、以下の問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="5f967-155">If you are using Proxy Servers to access the internet, you may see the following issues:</span></span>  
  
 <span data-ttu-id="5f967-156">**プロキシ サーバーによる接続数の設定:**</span><span class="sxs-lookup"><span data-stu-id="5f967-156">**Connection throttling by Proxy Servers:**</span></span>  
  
 <span data-ttu-id="5f967-157">プロキシ サーバーで、1 分あたりの接続数を制限する設定が使用されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f967-157">Proxy Servers can have settings that limit the number of connections per minute.</span></span> <span data-ttu-id="5f967-158">Backup to URL プロセスはマルチスレッド プロセスであるため、この制限を超える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5f967-158">The Backup to URL process is a multi-threaded process and hence can go over this limit.</span></span> <span data-ttu-id="5f967-159">制限を超えた場合、プロキシ サーバーは接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="5f967-159">If this happens, the proxy server kills the connection.</span></span> <span data-ttu-id="5f967-160">この問題を解決するには、プロキシ設定を変更し、SQL Server がプロキシを使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="5f967-160">To resolve this issue, change the proxy settings so SQL Server is not using the proxy.</span></span>   <span data-ttu-id="5f967-161">エラー ログに表示される可能性のある種類またはエラー メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5f967-161">Following are some examples of the types or error messages you may see in the error log:</span></span>  
  
-   <span data-ttu-id="5f967-162">"" への書き込みに http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak 失敗しました: Backup TO URL がリモートエンドポイントから例外を受け取りました。</span><span class="sxs-lookup"><span data-stu-id="5f967-162">Write on "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak" failed: Backup to URL received an exception from the remote endpoint.</span></span> <span data-ttu-id="5f967-163">例外メッセージ: 転送接続からデータを読み取ることができません: 接続は閉じられました。</span><span class="sxs-lookup"><span data-stu-id="5f967-163">Exception Message: Unable to read data from the transport connection: The connection was closed.</span></span>  
  
-   <span data-ttu-id="5f967-164">ファイル "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" で回復できない I/O エラーが発生しました。リモート エンドポイントからエラーを収集できませんでした。</span><span class="sxs-lookup"><span data-stu-id="5f967-164">A nonrecoverable I/O error occurred on file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Error could not be gathered from Remote Endpoint.</span></span>  
  
     <span data-ttu-id="5f967-165">メッセージ 3013、レベル 16、状態 1、行 2</span><span class="sxs-lookup"><span data-stu-id="5f967-165">Msg 3013, Level 16, State 1, Line 2</span></span>  
  
     <span data-ttu-id="5f967-166">バックアップ データベースが異常終了しています。</span><span class="sxs-lookup"><span data-stu-id="5f967-166">BACKUP DATABASE is terminating abnormally.</span></span>  
  
-   <span data-ttu-id="5f967-167">BackupIoRequest:: ReportIoError: バックアップデバイス ' ' で書き込みエラーが発生 http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak しています。</span><span class="sxs-lookup"><span data-stu-id="5f967-167">BackupIoRequest::ReportIoError: write failure on backup device 'http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak'.</span></span> <span data-ttu-id="5f967-168">Backup to URL がリモート エンドポイントから例外を受け取ったオペレーティング システム エラーです。</span><span class="sxs-lookup"><span data-stu-id="5f967-168">Operating system error Backup to URL received an exception from the remote endpoint.</span></span> <span data-ttu-id="5f967-169">例外メッセージ: 転送接続からデータを読み取ることができません: 接続は閉じられました。</span><span class="sxs-lookup"><span data-stu-id="5f967-169">Exception Message: Unable to read data from the transport connection: The connection was closed.</span></span>  
  
 <span data-ttu-id="5f967-170">トレース フラグ 3051 を使用して詳細ログを有効にすると、ログに次のメッセージが表示される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5f967-170">If you turn on the verbose logging using the trace flag 3051 you may also see the following message in the logs:</span></span>  
  
 <span data-ttu-id="5f967-171">HTTP ステータス コード 502、HTTP ステータス メッセージ プロキシ エラー (1 分あたりの HTTP 要求数が構成済みの上限を超えました。</span><span class="sxs-lookup"><span data-stu-id="5f967-171">HTTP status code 502, HTTP Status Message Proxy Error ( The number of HTTP requests per minute exceeded the configured limit.</span></span> <span data-ttu-id="5f967-172">ISA Server 管理者に連絡してください。)</span><span class="sxs-lookup"><span data-stu-id="5f967-172">Contact your ISA Server administrator.</span></span>  <span data-ttu-id="5f967-173">)</span><span class="sxs-lookup"><span data-stu-id="5f967-173">)</span></span>  
  
 <span data-ttu-id="5f967-174">**選択されていない既定のプロキシ設定:**</span><span class="sxs-lookup"><span data-stu-id="5f967-174">**Default Proxy Settings not picked up:**</span></span>  
  
 <span data-ttu-id="5f967-175">既定の設定が選択されていないことが原因で、次に示すようなプロキシ認証エラーが発生することがあります。 "" という*ファイルで回復不可能な i/o エラーが発生しました。 http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: BACKUP to URL がリモートエンドポイントから例外を受け取りました。例外メッセージ: リモートサーバーからエラーが返されました: (407)* **プロキシ認証が必要**です。</span><span class="sxs-lookup"><span data-stu-id="5f967-175">Sometimes the default settings are not picked up causing proxy authentication errors such as the one shown below:*A nonrecoverable I/O error occurred on file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (407)* **Proxy Authentication Required**.</span></span>  
  
 <span data-ttu-id="5f967-176">この問題を解決するには、次の手順に従って、Backup to URL プロセスで既定のプロキシ設定を使用できるようにするための構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="5f967-176">To resolve this issue, create a configuration file that allows the Backup to URL process to use the default proxy settings using the following steps:</span></span>  
  
1.  <span data-ttu-id="5f967-177">次の xml を使用して、BackuptoURL.exe.config という名前の構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="5f967-177">Create a configuration file named BackuptoURL.exe.config  with the following xml:</span></span>  
  
    ```  
    <?xml version ="1.0"?>  
    <configuration>   
                    <system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    </system.net>  
    </configuration>  
  
    ```  
  
2.  <span data-ttu-id="5f967-178">SQL Server インスタンスの Binn フォルダーに構成ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="5f967-178">Place the configuration file in the Binn folder of the SQL Server Instance.</span></span> <span data-ttu-id="5f967-179">たとえば、SQL Server がコンピューターの C ドライブにインストールされている場合は、構成ファイルを*C:\Program SERVER\MSSQL12. \<InstanceName> SQL に配置します。\MSSQL\Binn*。</span><span class="sxs-lookup"><span data-stu-id="5f967-179">For example, if my SQL Server is installed on the C drive of the machine, place the configuration file here: *C:\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\Binn*.</span></span>  
  
## <a name="troubleshooting-sql-server-managed-backup-to-azure"></a><span data-ttu-id="5f967-180">Azure への SQL Server マネージド バックアップのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5f967-180">Troubleshooting SQL Server Managed Backup to Azure</span></span>  
 <span data-ttu-id="5f967-181">SQL Server マネージド バックアップは Backup to URL の上に構築されるので、前のセクションで説明したトラブルシューティングのヒントは、SQL Server マネージド バックアップを使用するデータベースまたはインスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="5f967-181">Since SQL Server Managed Backup is built on top of Backup to URL, the troubleshooting tips described in the earlier sections apply to databases or instances using SQL Server Managed Backup.</span></span>  <span data-ttu-id="5f967-182">Azure への管理されたバックアップ SQL Server のトラブルシューティングの詳細については、「 [azure へのマネージバックアップのトラブルシューティング SQL Server](sql-server-managed-backup-to-microsoft-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f967-182">Information about troubleshooting SQL Server Managed Backup to Azure is described in detail in [Troubleshooting SQL Server Managed  Backup to Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f967-183">参照</span><span class="sxs-lookup"><span data-stu-id="5f967-183">See Also</span></span>  
 [<span data-ttu-id="5f967-184">Azure に格納されたバックアップからの復元</span><span class="sxs-lookup"><span data-stu-id="5f967-184">Restoring From Backups Stored in Azure</span></span>](restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
