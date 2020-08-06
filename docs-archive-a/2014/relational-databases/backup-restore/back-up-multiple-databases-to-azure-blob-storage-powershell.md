---
title: PowerShell を使用して複数のデータベースを Azure Blob Storage サービスにバックアップする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: f7008339-e69d-4e20-9265-d649da670460
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95da5d0009f88943029e62960e7429b292242bbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641701"
---
# <a name="use-powershell-to-backup-multiple-databases-to-azure-blob-storage-service"></a><span data-ttu-id="eb670-102">PowerShell を使った Azure Blob Storage サービスへの複数データベースのバックアップ</span><span class="sxs-lookup"><span data-stu-id="eb670-102">Use PowerShell to Backup Multiple Databases to Azure Blob Storage Service</span></span>
  <span data-ttu-id="eb670-103">このトピックでは、PowerShell コマンドレットを使用して Azure Blob Storage サービスへのバックアップを自動化するために使用できるサンプル スクリプトを提供します。</span><span class="sxs-lookup"><span data-stu-id="eb670-103">This topic provides sample scripts that can be used to automate backups to Azure Blob storage service using PowerShell cmdlets.</span></span>  
  
## <a name="overview-of-powershell-cmdlets-for-backup-and-restore"></a><span data-ttu-id="eb670-104">バックアップと復元用の PowerShell コマンドレットの概要</span><span class="sxs-lookup"><span data-stu-id="eb670-104">Overview of PowerShell cmdlets for Backup and Restore</span></span>  
 <span data-ttu-id="eb670-105">バックアップ操作と復元操作を行うために使用できる 2 つの主要なコマンドレットは、`Backup-SqlDatabase` と `Restore-SqlDatabase` です。</span><span class="sxs-lookup"><span data-stu-id="eb670-105">The `Backup-SqlDatabase` and `Restore-SqlDatabase` are the two main cmdlets available to do backup and restore operations.</span></span> <span data-ttu-id="eb670-106">さらに、一連の **SqlCredential** コマンドレットのように、Azure Blob Storage へのバックアップを自動化するために必要な他のコマンドレットもあります。バックアップおよび復元操作用として [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に用意されている PowerShell コマンドレットを次に示します。</span><span class="sxs-lookup"><span data-stu-id="eb670-106">In addition, there are other cmdlets that may be required to automate backups to Azure Blob storage like the set of **SqlCredential** cmdlets  Following is a list of PowerShell cmdlets available in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that are used in backup and restore operations:</span></span>  
  
 <span data-ttu-id="eb670-107">Backup-SqlDatabase</span><span class="sxs-lookup"><span data-stu-id="eb670-107">Backup-SqlDatabase</span></span>  
 <span data-ttu-id="eb670-108">このコマンドレットは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="eb670-108">This cmdlet is used to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Backup.</span></span>  
  
 <span data-ttu-id="eb670-109">Restore-SqlDatabase</span><span class="sxs-lookup"><span data-stu-id="eb670-109">Restore-SqlDatabase</span></span>  
 <span data-ttu-id="eb670-110">データベースを復元するために使用します。</span><span class="sxs-lookup"><span data-stu-id="eb670-110">Used to restore a database.</span></span>  
  
 <span data-ttu-id="eb670-111">New-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="eb670-111">New-SqlCredential</span></span>  
 <span data-ttu-id="eb670-112">このコマンドレットは、Azure Storage の SQL Server バックアップに使用する SQL 資格情報を作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="eb670-112">This cmdlet is used to create a SQL Credential to use for SQL Server Backup to Azure Storage.</span></span> <span data-ttu-id="eb670-113">SQL Server のバックアップと復元における資格情報とその使用方法の詳細については、「 [Azure Blob Storage サービスを使用したバックアップと復元の SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb670-113">For more information on credentials and their use in SQL Server Backup and Restore, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="eb670-114">Get-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="eb670-114">Get-SqlCredential</span></span>  
 <span data-ttu-id="eb670-115">このコマンドレットは、資格情報オブジェクトとそのプロパティを取得するために使用します。</span><span class="sxs-lookup"><span data-stu-id="eb670-115">This cmdlet is used to retrieve the Credential object and its properties.</span></span>  
  
 <span data-ttu-id="eb670-116">Remove-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="eb670-116">Remove-SqlCredential</span></span>  
 <span data-ttu-id="eb670-117">SQL 資格情報オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="eb670-117">Delete a SQL Credential object</span></span>  
  
 <span data-ttu-id="eb670-118">Set-SqlCredential</span><span class="sxs-lookup"><span data-stu-id="eb670-118">Set-SqlCredential</span></span>  
 <span data-ttu-id="eb670-119">このコマンドレットは、SQL 資格情報オブジェクトのプロパティを変更または設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="eb670-119">This cmdlet is used to change or set the properties of the SQL Credential Object.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="eb670-120">Credential コマンドレットは、Azure Blob Storage へのバックアップと復元のシナリオで使用します。</span><span class="sxs-lookup"><span data-stu-id="eb670-120">The Credential cmdlets are used in Backup and Restore to Azure Blob storage scenarios.</span></span>  
  
### <a name="powershell-for-multi-database-multi-instance-backup-operations"></a><span data-ttu-id="eb670-121">複数データベース/複数インスタンス バックアップ操作用の PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb670-121">PowerShell for Multi-Database, Multi-Instance Backup Operations</span></span>  
 <span data-ttu-id="eb670-122">以下のセクションでは、SQL Server の複数インスタンスでの SQL 資格情報の作成、特定の SQL Server インスタンスにあるすべてのユーザー データベースのバックアップなど、さまざまな操作用のスクリプトを掲載します。</span><span class="sxs-lookup"><span data-stu-id="eb670-122">The following sections include scripts for various operations like creating a SQL Credential on multiple instance of SQL Server, backing up all user databases in an instance of SQL Server, and such.</span></span> <span data-ttu-id="eb670-123">これらのスクリプトでは、使用している環境の要件に従ってバックアップ操作を自動化またはスケジュールすることができます。</span><span class="sxs-lookup"><span data-stu-id="eb670-123">You can use these scripts to automate or schedule backup operations according to the requirements of your environment.</span></span> <span data-ttu-id="eb670-124">ここに示すスクリプトは例であり、環境に合わせて変更または拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="eb670-124">The scripts provided here are examples, and may be modified or extended for your environment.</span></span>  
  
 <span data-ttu-id="eb670-125">サンプル スクリプトに関する注意点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="eb670-125">The following are considerations for the sample scripts:</span></span>  
  
1.  <span data-ttu-id="eb670-126">**SQL Server PowerShell パスの移動:** Windows PowerShell では、コマンドレットを実装して、PowerShell プロバイダーによりサポートされるオブジェクトの階層を表すパス構造を移動できます。</span><span class="sxs-lookup"><span data-stu-id="eb670-126">**Navigating SQL Server PowerShell paths:** Windows PowerShell implements cmdlets to navigate the path structure that represents the hierarchy of objects supported by a PowerShell provider.</span></span> <span data-ttu-id="eb670-127">そのパス内のノードへ移動したときに、他のコマンドレットを使用して、現在のオブジェクトの基本的な操作を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="eb670-127">When you have navigated to a node in the path, you can use other cmdlets to perform basic operations on the current object.</span></span>  
  
2.  <span data-ttu-id="eb670-128">`Get-ChildItem` コマンドレット: `Get-ChildItem` から返される情報は、SQL Server PowerShell パス内の場所によって異なります。</span><span class="sxs-lookup"><span data-stu-id="eb670-128">`Get-ChildItem` cmdlet: The information returned by the `Get-ChildItem` depends on the location in a SQL Server PowerShell path.</span></span> <span data-ttu-id="eb670-129">たとえば、場所がコンピューター レベルである場合、このコマンドレットはコンピューターにインストールされているすべての SQL Server データベース エンジン インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="eb670-129">For example, if the location is at the computer level, this cmdlet returns all the SQL Server database engine instances installed on the computer.</span></span> <span data-ttu-id="eb670-130">もう 1 つの例として、場所がデータベースなどのオブジェクト レベルである場合、このコマンドレットはデータベース オブジェクトのリストを返します。</span><span class="sxs-lookup"><span data-stu-id="eb670-130">As another example, if the location is at the object level such as databases, then this cmdlet returns a list of database objects.</span></span>  <span data-ttu-id="eb670-131">既定では、`Get-ChildItem` コマンドレットはシステム オブジェクトを返しません。</span><span class="sxs-lookup"><span data-stu-id="eb670-131">By default the `Get-ChildItem` cmdlet does not return system objects.</span></span>  <span data-ttu-id="eb670-132">-Force パラメーターを使用すると、システム オブジェクトを表示できます。</span><span class="sxs-lookup"><span data-stu-id="eb670-132">Using the -Force parameter you can see the system objects.</span></span>  
  
     <span data-ttu-id="eb670-133">詳細については、「 [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="eb670-133">For more information, see [Navigate SQL Server PowerShell Paths](../../powershell/navigate-sql-server-powershell-paths.md).</span></span>  
  
3.  <span data-ttu-id="eb670-134">各コード サンプルは変数値を変更して個別に試すことができますが、Azure ストレージ アカウントおよび SQL 資格情報の作成が前提条件であり、Azure Blob Storage サービスへのすべてのバックアップ操作と復元操作に必要です。</span><span class="sxs-lookup"><span data-stu-id="eb670-134">Although each code sample can be tried independently by changing the variable values, creating an Azure Storage Account and a SQL Credential are prerequisites and required for all backup and restore operations to Azure Blob storage service.</span></span>  
  
### <a name="create-a-sql-credential-on-all-the-instances-of-sql-server"></a><span data-ttu-id="eb670-135">SQL Server のすべてのインスタンスで SQL 資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="eb670-135">Create a SQL Credential on All the Instances of SQL Server</span></span>  
 <span data-ttu-id="eb670-136">2 種類のサンプル スクリプトがあり、いずれもコンピューター上のすべての SQL Server インスタンスで SQL 資格情報 "mybackupToURL" を作成します。</span><span class="sxs-lookup"><span data-stu-id="eb670-136">There are two sample scripts, and both create a SQL Credential "mybackupToURL" on all the instances of SQL Server on a computer.</span></span> <span data-ttu-id="eb670-137">最初の例では単純に資格情報を作成し、例外をトラップしません。</span><span class="sxs-lookup"><span data-stu-id="eb670-137">The first example creates is simple and creates the credential and does not trap exceptions.</span></span>  <span data-ttu-id="eb670-138">たとえば、コンピューター上のいずれかのインスタンスに同じ名前の資格情報が既に存在する場合、このスクリプトは失敗します。</span><span class="sxs-lookup"><span data-stu-id="eb670-138">For example, if there was already an existing credential with the same name on one of the instances of the computer, the script would fail.</span></span> <span data-ttu-id="eb670-139">2 番目の例ではエラーをトラップし、スクリプトを続行できます。</span><span class="sxs-lookup"><span data-stu-id="eb670-139">The second example traps errors and allows the script to continue.</span></span>  
  
```powershell
import-module sqlps  
  
# create variables  
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-ChildItem  
#pipe the instances to new-sqlcredentail cmdlet to create SQL credential  
$instances | New-SqlCredential -Name $credentialName -Identity $storageAccount -Secret $secureString  
```  
  
```powershell
import-module sqlps  
  
# set the parameter values
$storageAccount = "mystorageaccount"  
$storageKey = "<storageaccesskeyvalue>"  
$secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
$credentialName = "mybackuptoURL"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
# get the list of instances  
$instances = Get-ChildItem  
#loop through instances and create a SQL credential, output any errors  
ForEach ($instance In $instances)  
{  
    Try  
{  
     New-SqlCredential -Name $credentialName -path "SQLServer:\SQL\$($instance.name)" -Identity $storageAccount -Secret $secureString -ea Stop
}  
Catch [Exception]  
    {
            Write-Host "instance - $($instance.name): "$_.Exception.Message
    }
 }
```  
  
### <a name="remove-a-sql-credential-from-all-the-instances-of-sql-server"></a><span data-ttu-id="eb670-140">SQL Server のすべてのインスタンスから SQL 資格情報を削除する</span><span class="sxs-lookup"><span data-stu-id="eb670-140">Remove A SQL Credential from All the Instances of SQL Server</span></span>  
 <span data-ttu-id="eb670-141">このスクリプトは、コンピューターにインストールされているすべての SQL Server インスタンスから特定の資格情報を削除する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb670-141">This script can be used to remove a specific credential from all the instances of SQL Server installed on the computer.</span></span> <span data-ttu-id="eb670-142">特定のインスタンスに資格情報オブジェクトが存在しない場合は、エラー メッセージが表示され、すべてのインスタンスが確認されるまでスクリプトが続行されます。</span><span class="sxs-lookup"><span data-stu-id="eb670-142">If the Credential object does not exist on a specific instance, an error message is displayed, and the script continues until all instances are checked.</span></span>  
  
```powershell
import-module sqlps  
  
cd SQLServer:\SQL\COMPUTERNAME  
$credentialName = "mybackuptoURL"  
  
$instances = Get-ChildItem  
  
ForEach ($instance In $instances)  
   {
    Try  
        {  
            $path = "SQLServer:\SQL\$($instance.name)\credentials\$credentialName"   
            Remove-SqlCredential -Path $path -ea stop   
         }  
         Catch [Exception]  
         {  
            Write-Host $_.Exception.Message
        }
    }  
```  
  
### <a name="full-database-backup-for-all-databases-including-system-databases"></a><span data-ttu-id="eb670-143">すべてのデータベース (システム データベースを含む) の完全バックアップ</span><span class="sxs-lookup"><span data-stu-id="eb670-143">Full Database Backup for all Databases (INCLUDING SYSTEM DATABASES)</span></span>  
 <span data-ttu-id="eb670-144">次のスクリプトでは、コンピューター上のすべてのデータベースのバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb670-144">The following script creates backups of all databases on the computer.</span></span> <span data-ttu-id="eb670-145">これには、ユーザー データベースと **msdb** システム データベースの両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="eb670-145">This includes both user databases and **msdb** system database.</span></span> <span data-ttu-id="eb670-146">スクリプトでは、 **tempdb** システム データベースと **model** システム データベースを除外します。</span><span class="sxs-lookup"><span data-stu-id="eb670-146">The script filters out **tempdb** and **model** system databases.</span></span>  
  
```powershell
import-module sqlps  
# set the parameter values  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-ChildItem
# loop through each instances and backup up all the  databases -filter out tempdb and model databases  
  
 ForEach ($instance In $instances)  
 {  
   $path = "sqlserver:\sql\$($instance.name)\databases"  
   $alldatabases = Get-ChildItem -Force -path $path | Where-Object {$_.name -ne "tempdb" -and $_.name -ne "model"}   
   $alldatabases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On -script   
 }
```  
  
### <a name="full-database-backup-for-all-user-databases"></a><span data-ttu-id="eb670-147">すべてのユーザー データベースの完全バックアップ</span><span class="sxs-lookup"><span data-stu-id="eb670-147">Full Database Backup for ALL User Databases</span></span>  
 <span data-ttu-id="eb670-148">次のスクリプトは、コンピューター上にあるすべての SQL Server インスタンスのユーザー データベースをすべてバックアップするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb670-148">The following script can be used to back up all the user databases on all the instances of SQL Server on the computer.</span></span>  
  
```powershell
import-module sqlps
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackuptoURL"  
  
# cd to computer level
cd SQLServer:\SQL\COMPUTERNAME  
$instances = Get-ChildItem
# loop through each instances and backup up all the user databases  
 ForEach ($instance In $instances)  
 {  
    $databases = dir "sqlserver:\sql\$($instance.name)\databases"  
    $databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On
 }  
```  
  
### <a name="full-database-backup-for-master-and-msdb-system-databases-on-all-the-instances-of-sql-server"></a><span data-ttu-id="eb670-149">すべての SQL Server インスタンスの master と msdb (システム データベース) の完全バックアップ</span><span class="sxs-lookup"><span data-stu-id="eb670-149">Full Database Backup for MASTER and MSDB (SYSTEM DATABASES) On All the Instances of SQL Server</span></span>  
 <span data-ttu-id="eb670-150">次のスクリプトは、コンピューター上にインストールされているすべての SQL Server インスタンスの **master** データベースと **msdb** データベースをバックアップするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb670-150">The following script can be used to back up **master** and **msdb** databases on all the instances of SQL Server installed on the computer.</span></span>  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$credentialName = "mybackupToUrl"  
$sysDbs = "master", "msdb"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
$instances = Get-ChildItem
ForEach ($instance In $instances)  
 {  
      ForEach ($s In $sysdbs)  
     {  
        Backup-SqlDatabase -Database $s -path "sqlserver:\sql\$($instance.name)" -BackupContainer  $backupUrlContainer -SqlCredential $credentialName -Compression On   
}
 } 
```  
  
### <a name="full-database-backup-for-all-user-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="eb670-151">SQL Server インスタンスのすべてのユーザー データベースの完全バックアップ</span><span class="sxs-lookup"><span data-stu-id="eb670-151">Full Database Backup for All User Databases on an Instance of SQL Server</span></span>  
 <span data-ttu-id="eb670-152">次のスクリプトは、SQL Server の名前付きインスタンスで使用可能なユーザー データベースのみをバックアップするために使用します。</span><span class="sxs-lookup"><span data-stu-id="eb670-152">The following script is used to back up only the user databases available on a named instance of SQL Server.</span></span> <span data-ttu-id="eb670-153">$srvPath パラメーターの値を変更することで、同じスクリプトをコンピューター上の既定インスタンスに使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="eb670-153">The same script can be used for the default instance on the computer by changing the $srvPath parameter value.</span></span>  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME"  # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#cd to computer level  
cd sqlserver:\sql\COMPUTERNAME  
  
#retrieves the database objects for a specific instance  
$databases = dir $srvPath\databases  
  
#backup all the user databases  
$databases | Backup-SqlDatabase -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
```  
  
### <a name="full-database-backup-for-only-system-databases-master-and-msdb-on-an-instance-of-sql-server"></a><span data-ttu-id="eb670-154">SQL Server インスタンスのシステム データベース (master と msdb) のみの完全バックアップ</span><span class="sxs-lookup"><span data-stu-id="eb670-154">Full Database Backup for Only System Databases (MASTER AND MSDB) On an Instance of SQL Server</span></span>  
 <span data-ttu-id="eb670-155">次のスクリプトは、SQL Server の名前付きインスタンスの **master** データベースと **msdb** データベースをバックアップするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="eb670-155">The full script can be used to back up the **master** and the **msdb** databases on a named instance of SQL Server.</span></span> <span data-ttu-id="eb670-156">$srvPath パラメーターの値を変更することで、同じスクリプトをコンピューター上の既定インスタンスに使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="eb670-156">The same script can be used for the default instance on the computer by changing the $srvpath parameter value.</span></span>  
  
```powershell
import-module sqlps  
  
$storageAccount = "mystorageaccount"  
$blobContainer = "privatecontainertest"  
$backupUrlContainer = "https://$storageAccount.blob.core.windows.net/$blobContainer/"  
$srvPath = "SQLServer:\SQL\COMPUTERNAME\INSTANCENAME" # for default instance, the $srvpath variable is "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
$credentialName = "mybackupToUrl"  
  
#navigate to instance level  
cd $srvPath  
  
$sysDbs = "master", "msdb"  
ForEach ($s In $sysDbs)
{  
Backup-SqlDatabase -Database $s -BackupContainer $backupUrlContainer -SqlCredential $credentialName -Compression On  
}
```  
  
## <a name="see-also"></a><span data-ttu-id="eb670-157">参照</span><span class="sxs-lookup"><span data-stu-id="eb670-157">See Also</span></span>
 <span data-ttu-id="eb670-158">[Azure Blob Storage サービスを使用したバックアップと復元の SQL Server SQL Server の](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) [URL に関するベストプラクティスとトラブルシューティング](sql-server-backup-to-url-best-practices-and-troubleshooting.md)</span><span class="sxs-lookup"><span data-stu-id="eb670-158">[SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) [SQL Server Backup to URL Best Practices and Troubleshooting](sql-server-backup-to-url-best-practices-and-troubleshooting.md)</span></span>  
