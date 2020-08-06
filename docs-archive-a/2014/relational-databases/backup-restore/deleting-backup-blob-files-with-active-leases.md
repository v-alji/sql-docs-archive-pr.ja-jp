---
title: アクティブなリースを保持しているバックアップ BLOB ファイルの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 02aea910589633a5c3ec79e283c757727b4d92cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640099"
---
# <a name="deleting-backup-blob-files-with-active-leases"></a><span data-ttu-id="4f35f-102">アクティブなリースを保持しているバックアップ BLOB ファイルの削除</span><span class="sxs-lookup"><span data-stu-id="4f35f-102">Deleting Backup Blob Files with Active Leases</span></span>
  <span data-ttu-id="4f35f-103">Azure storage との間でバックアップまたは復元を行う場合、SQL Server は blob への排他アクセスをロックするために無限リースを取得します。</span><span class="sxs-lookup"><span data-stu-id="4f35f-103">When backing up to or restoring from Azure storage, SQL Server acquires an infinite lease in order to lock exclusive access to the blob.</span></span> <span data-ttu-id="4f35f-104">バックアップまたは復元プロセスが正常に完了すると、リースは解放されます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-104">When the backup or restore process is successfully completed, the lease is released.</span></span> <span data-ttu-id="4f35f-105">バックアップまたは復元に失敗すると、バックアップ プロセスは無効な BLOB のクリーンアップを試みます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-105">If a backup or restore fails, the backup process attempts to clean up any invalid blob.</span></span> <span data-ttu-id="4f35f-106">ただし、バックアップの失敗の原因が長期的または持続的なネットワーク接続エラーの場合は、バックアップ プロセスは BLOB にアクセスできず、BLOB は孤立したままになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f35f-106">However, if the backup fails due to prolonged or sustained network connectivity failure, the backup  process may not be able gain access to the blob and the blob may remain orphaned.</span></span> <span data-ttu-id="4f35f-107">つまり、リースが解放されるまで、BLOB を書き込むことも削除することもできません。</span><span class="sxs-lookup"><span data-stu-id="4f35f-107">This means that the blob cannot be written to or deleted until the lease is released.</span></span> <span data-ttu-id="4f35f-108">このトピックでは、リースを解放する方法と BLOB の削除について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f35f-108">This topic describes how to release the lease and deleting the blob..</span></span>  
  
 <span data-ttu-id="4f35f-109">リースの種類の詳細については、こちらの [記事](https://go.microsoft.com/fwlink/?LinkId=275664)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4f35f-109">For more information on the types of leases, read this [article](https://go.microsoft.com/fwlink/?LinkId=275664).</span></span>  
  
 <span data-ttu-id="4f35f-110">バックアップ操作が失敗すると、無効なバックアップ ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-110">If the backup operation fails, it can result in a backup file that is not valid.</span></span>  <span data-ttu-id="4f35f-111">また、バックアップ BLOB ファイルでは、削除や上書きを防ぐためにアクティブなリースを保持する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4f35f-111">The backup blob file might also have an active lease, preventing it from being deleted or overwritten.</span></span>  <span data-ttu-id="4f35f-112">BLOB を削除または上書きするには、最初にリースを終了する必要があります。バックアップ障害が発生した場合は、リースをクリーンアップして BLOB を削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4f35f-112">In order to delete or overwrite such blobs, the lease should first be broken.If there are backup failures, we recommend that you clean up leases and delete blobs.</span></span> <span data-ttu-id="4f35f-113">また、ストレージ管理タスクの一部としてクリーンアップを定期的に選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-113">You can also choose cleanup periodically as part of storage management tasks.</span></span>  
  
 <span data-ttu-id="4f35f-114">復元エラーが発生した場合、後続の復元はブロックされないため、アクティブなリースは問題にならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="4f35f-114">If there is a restore failure, subsequent restores are not blocked, and therefore the active lease may not be an issue.</span></span> <span data-ttu-id="4f35f-115">リースを終了する必要があるのは、BLOB を上書きまたは削除する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="4f35f-115">Breaking the lease is only necessary when you have to overwrite or delete the blob.</span></span>  
  
## <a name="managing-orphaned-blobs"></a><span data-ttu-id="4f35f-116">孤立した BLOB の管理</span><span class="sxs-lookup"><span data-stu-id="4f35f-116">Managing Orphaned Blobs</span></span>  
 <span data-ttu-id="4f35f-117">次の手順では、バックアップ動作または復元動作の失敗後にクリーンアップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f35f-117">The follow steps describe how to clean up after failed backup or restore activity.</span></span> <span data-ttu-id="4f35f-118">すべての手順は、PowerShell スクリプトを使用して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-118">All the steps can be done using PowerShell scripts.</span></span> <span data-ttu-id="4f35f-119">コード例については、次のセクションに示します。</span><span class="sxs-lookup"><span data-stu-id="4f35f-119">A code example is provided in the following section:</span></span>  
  
1.  <span data-ttu-id="4f35f-120">**リースを保持している BLOB の識別:** バックアップ プロセスを実行するスクリプトまたはプロセスがあると、スクリプトまたはプロセス内のエラーをキャプチャし、それを使用して BLOB をクリーンアップできる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4f35f-120">**Identifying blobs that have leases:** If you have a script or a process that runs the backup processes, you might be able to capture the failure within the script or process and use that to clean up the blobs.</span></span>   <span data-ttu-id="4f35f-121">また、LeaseStats プロパティと LeastState プロパティを使用して、それらのプロパティに対してリースを保持している BLOB を識別することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-121">You can also use the LeaseStats and LeastState properties to identify the blobs that have leases on them.</span></span> <span data-ttu-id="4f35f-122">BLOB を識別したら、一覧を確認し、BLOB を削除する前にバックアップ ファイルが有効かどうかを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4f35f-122">Once you have identified the blobs, we recommend that you review the list, verify the validity of the backup file before deleting the blob.</span></span>  
  
2.  <span data-ttu-id="4f35f-123">**リースの終了:** 承認された要求では、リース ID を指定せずにリースを終了できます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-123">**Breaking the lease:** An authorized request can break the lease without supplying a lease ID.</span></span> <span data-ttu-id="4f35f-124">詳細については、 [こちら](https://go.microsoft.com/fwlink/?LinkID=275664) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4f35f-124">See [here](https://go.microsoft.com/fwlink/?LinkID=275664) for more information.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="4f35f-125">SQL Server は、復元操作中にリース ID を発行して排他アクセスを確立します。</span><span class="sxs-lookup"><span data-stu-id="4f35f-125">SQL Server issues a lease ID to establish exclusive access during the restore operation.</span></span> <span data-ttu-id="4f35f-126">復元のリース ID は BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2 です。</span><span class="sxs-lookup"><span data-stu-id="4f35f-126">The restore lease ID is BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.</span></span>  
  
3.  <span data-ttu-id="4f35f-127">**BLOB の削除:** アクティブなリースを保持している BLOB を削除するには、最初にリースを終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f35f-127">**Deleting the Blob:** To delete a blob that has an active lease, you must first break the lease.</span></span>  
  
###  <a name="powershell-script-example"></a><a name="Code_Example"></a><span data-ttu-id="4f35f-128">PowerShell スクリプトの例</span><span class="sxs-lookup"><span data-stu-id="4f35f-128">PowerShell Script Example</span></span>  
 <span data-ttu-id="4f35f-129">\*\* \* \* 重要 \* : \* \*\* PowerShell 2.0 を実行している場合は、Microsoft WindowsAzure.Storage.dll アセンブリの読み込みで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f35f-129">**\*\* Important \*\*** If you are running PowerShell 2.0, you may have problems loading the Microsoft WindowsAzure.Storage.dll assembly.</span></span> <span data-ttu-id="4f35f-130">この問題を解決するには、PowerShell 3.0 にアップグレードすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4f35f-130">We recommend that you upgrade to Powershell 3.0 to solve the issue.</span></span> <span data-ttu-id="4f35f-131">また、PowerShell 2.0 では次の回避策を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-131">You may also use the following workaround for PowerShell 2.0:</span></span>  
  
-   <span data-ttu-id="4f35f-132">次のスクリプトを使用して実行時に .NET 2.0 アセンブリと .NET 4.0 アセンブリを読み込むように powershell.exe.config ファイルを作成または変更する:</span><span class="sxs-lookup"><span data-stu-id="4f35f-132">Create or modify the powershell.exe.config file to load .NET 2.0 and .NET 4.0 assemblies at runtime with the following:</span></span>  
  
    ```xml
    <?xml version="1.0"?>
    <configuration>
        <startup useLegacyV2RuntimeActivationPolicy="true">
            <supportedRuntime version="v4.0.30319"/>
            <supportedRuntime version="v2.0.50727"/>
        </startup>
    </configuration>
    ```  
  
 <span data-ttu-id="4f35f-133">次の例は、アクティブなリースを保持している BLOB を識別してから、アクティブなリースを終了する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4f35f-133">The following example illustrates identifying blobs that have active leases and then breaking them.</span></span> <span data-ttu-id="4f35f-134">この例は、リリースのリース ID をフィルター選択する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="4f35f-134">The example also demonstrates how filter for release lease IDs.</span></span>  
  
 <span data-ttu-id="4f35f-135">このスクリプトの実行に関するヒント</span><span class="sxs-lookup"><span data-stu-id="4f35f-135">Tips on running this script</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="4f35f-136">Azure Blob ストレージサービスへのバックアップがこのスクリプトと同時に実行されている場合、バックアップは失敗する可能性があります。これは、このスクリプトによって、バックアップが同時に取得しようとしているリースが解除されるためです。</span><span class="sxs-lookup"><span data-stu-id="4f35f-136">If a backup to Azure Blob storage service is running at the same time as this script, the backup can fail since this script will break the lease that the backup is trying to acquire at the same time.</span></span> <span data-ttu-id="4f35f-137">このスクリプトは、保守期間中またはバックアップの実行が予期されていないときに実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4f35f-137">We recommend running this script during a maintenance windows or when no backups are expected to run.</span></span>  
  
1.  <span data-ttu-id="4f35f-138">このスクリプトを実行すると、ストレージアカウント、ストレージキー、コンテナー、Azure ストレージアセンブリのパスと名前のパラメーターの値を入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-138">When you run this script, you will be prompted to provide values for the storage account, storage key, container, and the Azure storage assembly path and name parameters.</span></span> <span data-ttu-id="4f35f-139">ストレージ アセンブリのパスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスのインストール ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="4f35f-139">The path of the storage is assembly is the installation directory of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4f35f-140">ストレージ アセンブリのファイル名は Microsoft.WindowsAzure.Storage.dll です。</span><span class="sxs-lookup"><span data-stu-id="4f35f-140">The file name for the storage assembly is Microsoft.WindowsAzure.Storage.dll.</span></span> <span data-ttu-id="4f35f-141">次に、入力するプロンプトと値の例を示します。</span><span class="sxs-lookup"><span data-stu-id="4f35f-141">Following is an example of the prompts and values entered:</span></span>  
  
    ```  
    cmdlet  at command pipeline position 1  
    Supply values for the following parameters:  
    storageAccount: mycloudstorageaccount  
    storageKey: 0BopKY7eEha3gBnistYk+904nf  
    blobContainer: mycontainer   
    storageAssemblyPath: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Microsoft.WindowsAzure.Storage.dll  
    ```  
  
2.  <span data-ttu-id="4f35f-142">リースがロックされている BLOB がない場合は、次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-142">If there are no blobs that have locked leases you should see the following message:</span></span>  
  
     <span data-ttu-id="4f35f-143">**ロックされたリースの状態の BLOB はありません**</span><span class="sxs-lookup"><span data-stu-id="4f35f-143">**There are no blobs with locked lease status**</span></span>  
  
     <span data-ttu-id="4f35f-144">リースがロックされている BLOB がある場合は、次のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f35f-144">If there are blobs with locked leases, you should see the following messages:</span></span>  
  
     <span data-ttu-id="4f35f-145">**リースを終了しています**</span><span class="sxs-lookup"><span data-stu-id="4f35f-145">**Breaking Leases**</span></span>  
  
     <span data-ttu-id="4f35f-146">**リースは \<URL of the Blob> 復元リースです。このメッセージは、まだアクティブになっている復元リースを持つ blob がある場合にのみ表示されます。**</span><span class="sxs-lookup"><span data-stu-id="4f35f-146">**The lease on \<URL of the Blob> is a restore lease: You will see this message only if you have a blob with a restore lease that is still active.**</span></span>  
  
     <span data-ttu-id="4f35f-147">**のリース \<URL of the Blob> は、の復元リースリースではありません \<URL of the Bob> 。**</span><span class="sxs-lookup"><span data-stu-id="4f35f-147">**The lease on \<URL of the Blob> is not a restore lease Breaking lease on \<URL of the Bob>.**</span></span>  
  
```powershell
param(  
       [Parameter(Mandatory=$true)]  
       [string]$storageAccount,  
       [Parameter(Mandatory=$true)]  
       [string]$storageKey,  
       [Parameter(Mandatory=$true)]  
       [string]$blobContainer,  
       [Parameter(Mandatory=$true)]  
       [string]$storageAssemblyPath  
)  
  
# Well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# Load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
$container = $client.GetContainerReference($blobContainer)  
  
#list all the blobs  
$allBlobs = $container.ListBlobs()
  
$lockedBlobs = @()  
# filter blobs that are have Lease Status as "locked"  
foreach($blob in $allBlobs)  
{  
    $blobProperties = $blob.Properties
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
    }  
}  
  
if ($lockedBlobs.Count -eq 0)  
{
    Write-Host " There are no blobs with locked lease status"  
}

if($lockedBlobs.Count -gt 0)  
{  
    Write-Host "Breaking leases"  
    foreach($blob in $lockedBlobs )
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease"  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease"  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)"  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
}
```  
  
## <a name="see-also"></a><span data-ttu-id="4f35f-148">参照</span><span class="sxs-lookup"><span data-stu-id="4f35f-148">See Also</span></span>  
 [<span data-ttu-id="4f35f-149">SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="4f35f-149">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>](sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
