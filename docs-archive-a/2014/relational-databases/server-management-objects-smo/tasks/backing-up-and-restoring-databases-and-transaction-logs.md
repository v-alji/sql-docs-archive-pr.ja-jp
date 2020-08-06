---
title: データベースとトランザクションログのバックアップと復元 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- restoring databases [SMO]
- transaction log backups [SMO]
- backing up transaction logs [SMO]
- database backups [SMO]
- restoring transaction logs [SMO]
- transaction log restores [SMO]
- backing up databases [SMO]
- database restores [SMO]
ms.assetid: 1d7bd180-fd6c-4b38-a87b-351496040542
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e88534e04435001dc4c93b58ff9ed36c4bb14fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739678"
---
# <a name="backing-up-and-restoring-databases-and-transaction-logs"></a><span data-ttu-id="c2d85-102">データベースおよびトランザクション ログのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="c2d85-102">Backing Up and Restoring Databases and Transaction Logs</span></span>
  <span data-ttu-id="c2d85-103">SMO の <xref:Microsoft.SqlServer.Management.Smo.Backup> クラスおよび <xref:Microsoft.SqlServer.Management.Smo.Restore> クラスは、バックアップおよび復元の特定のタスクを実行するツールを提供するユーティリティ クラスです。</span><span class="sxs-lookup"><span data-stu-id="c2d85-103">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Backup> class and the <xref:Microsoft.SqlServer.Management.Smo.Restore> class are utility classes that provide the tools to accomplish the specific tasks of backing up and restoring.</span></span> <span data-ttu-id="c2d85-104">オブジェクトは、 <xref:Microsoft.SqlServer.Management.Smo.Backup> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] サーバーインスタンス上のオブジェクトの代わりに必要な特定のバックアップタスクを表し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c2d85-104">A <xref:Microsoft.SqlServer.Management.Smo.Backup> object represents a specific backup task that is required instead of a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] object on the server instance.</span></span>  
  
 <span data-ttu-id="c2d85-105">データの損失や破損が発生した場合、バックアップを完全に、または部分的に復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2d85-105">If data loss or corruption occurs, the backup must be restored, either fully or partially.</span></span> <span data-ttu-id="c2d85-106">部分的な復元では、復元するデータを分割するために <xref:Microsoft.SqlServer.Management.Smo.FileGroupCollection> コレクションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c2d85-106">Partial restoration uses the <xref:Microsoft.SqlServer.Management.Smo.FileGroupCollection> collection to segment the data to be restored.</span></span> <span data-ttu-id="c2d85-107">トランザクション ログのバックアップの場合、<xref:Microsoft.SqlServer.Management.Smo.Restore.ToPointInTime%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Restore> プロパティを使用して、データが特定の時点まで復元されます。</span><span class="sxs-lookup"><span data-stu-id="c2d85-107">If the backup is of a transaction log, the data can be restored up to a particular point in time by using the <xref:Microsoft.SqlServer.Management.Smo.Restore.ToPointInTime%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Restore> object.</span></span> <span data-ttu-id="c2d85-108">データは、<xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> メソッドを使用して検証することができます。</span><span class="sxs-lookup"><span data-stu-id="c2d85-108">The data can also be validated by using the <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> method.</span></span> <span data-ttu-id="c2d85-109">推奨されるバックアップ手順は、復元操作とデータベース内のデータのチェックを定期的に実行することによってバックアップの整合性をチェックすることです。</span><span class="sxs-lookup"><span data-stu-id="c2d85-109">The recommended backup procedure is to check the integrity of the backup by doing a restore operation and checking the data in the database on a regular basis.</span></span>  
  
 <span data-ttu-id="c2d85-110"><xref:Microsoft.SqlServer.Management.Smo.Backup> オブジェクトと同様、<xref:Microsoft.SqlServer.Management.Smo.Restore> オブジェクトは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス上のオブジェクトを表現しているのではないので、`Create` メソッドを使用して作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c2d85-110">Like the <xref:Microsoft.SqlServer.Management.Smo.Backup> object, the <xref:Microsoft.SqlServer.Management.Smo.Restore> object does not need to be created by using a `Create` method because it does not represent any object on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c2d85-111"><xref:Microsoft.SqlServer.Management.Smo.Restore> オブジェクトは、データベースの復元に使用されるプロパティとメソッドのセットです。</span><span class="sxs-lookup"><span data-stu-id="c2d85-111">The <xref:Microsoft.SqlServer.Management.Smo.Restore> object is a set of properties and methods used to restore a database.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c2d85-112">例</span><span class="sxs-lookup"><span data-stu-id="c2d85-112">Examples</span></span>  
 <span data-ttu-id="c2d85-113">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2d85-113">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="c2d85-114">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2d85-114">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="backing-up-databases-and-transaction-logs-in-visual-basic"></a><span data-ttu-id="c2d85-115">Visual Basic でのデータベースおよびトランザクション ログのバックアップ</span><span class="sxs-lookup"><span data-stu-id="c2d85-115">Backing Up Databases and Transaction Logs in Visual Basic</span></span>  
 <span data-ttu-id="c2d85-116">このコード例では、既存のデータベースをファイルにバックアップする方法と復元する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c2d85-116">This code example shows how to back up an existing database to a file, and then how to restore it.</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Common  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.VisualBasic.MyServices  
  
Module SMO_VBBackup3  
  
    Sub Main()  
        'Connect to the local, default instance of SQL Server.  
        Dim srv As Server  
        srv = New Server  
  
        'Reference the AdventureWorks2012 database.  
        Dim db As Database  
        db = srv.Databases("AdventureWorks2012")  
  
        'Store the current recovery model in a variable.  
        Dim recoverymod As Integer  
        recoverymod = db.DatabaseOptions.RecoveryModel  
  
        'Define a Backup object variable.   
        Dim bk As New Backup  
  
        'Specify the type of backup, the description, the name, and the database to be backed up.  
        bk.Action = BackupActionType.Database  
        bk.BackupSetDescription = "Full backup of AdventureWorks2012"  
        bk.BackupSetName = "AdventureWorks 2012 Backup"  
        bk.Database = "AdventureWorks2012"  
  
        'Declare a BackupDeviceItem by supplying the backup device file name in the constructor, and the type of device is a file.  
        Dim bdi As BackupDeviceItem  
        bdi = New BackupDeviceItem("Test_Full_Backup1", DeviceType.File)  
  
        'Add the device to the Backup object.  
        bk.Devices.Add(bdi)  
  
        'Set the Incremental property to False to specify that this is a full database backup.  
        bk.Incremental = False  
  
        'Set the expiration date.  
        Dim backupdate As New Date  
        backupdate = New Date(2006, 10, 5)  
        bk.ExpirationDate = backupdate  
  
        'Specify that the log must be truncated after the backup is complete.  
        bk.LogTruncation = BackupTruncateLogType.Truncate  
  
        'Run SqlBackup to perform the full database backup on the instance of SQL Server.  
        bk.SqlBackup(srv)  
  
        'Inform the user that the backup has been completed.  
        Console.WriteLine("Full Backup complete.")  
  
        'Remove the backup device from the Backup object.  
        bk.Devices.Remove(bdi)  
  
        'Make a change to the database, in this case, add a table called test_table.  
        Dim t As Table  
        t = New Table(db, "test_table")  
        Dim c As Column  
        c = New Column(t, "col", DataType.Int)  
        t.Columns.Add(c)  
        t.Create()  
  
        'Create another file device for the differential backup and add the Backup object.  
        Dim bdid As BackupDeviceItem  
        bdid = New BackupDeviceItem("Test_Differential_Backup1", DeviceType.File)  
  
        'Add the device to the Backup object.  
        bk.Devices.Add(bdid)  
  
        'Set the Incremental property to True for a differential backup.  
        bk.Incremental = True  
  
        'Run SqlBackup to perform the incremental database backup on the instance of SQL Server.  
        bk.SqlBackup(srv)  
  
        'Inform the user that the differential backup is complete.  
        Console.WriteLine("Differential Backup complete.")  
  
        'Remove the device from the Backup object.  
        bk.Devices.Remove(bdid)  
  
        'Delete the AdventureWorks2012 database before restoring it.  
        srv.Databases("AdventureWorks2012").Drop()  
  
        'Define a Restore object variable.  
        Dim rs As Restore  
        rs = New Restore  
  
        'Set the NoRecovery property to true, so the transactions are not recovered.  
        rs.NoRecovery = True  
  
        'Add the device that contains the full database backup to the Restore object.  
        rs.Devices.Add(bdi)  
  
        'Specify the database name.  
        rs.Database = "AdventureWorks2012"  
  
        'Restore the full database backup with no recovery.  
        rs.SqlRestore(srv)  
  
        'Inform the user that the Full Database Restore is complete.  
        Console.WriteLine("Full Database Restore complete.")  
  
        'Remove the device from the Restore object.  
        rs.Devices.Remove(bdi)  
  
        'Set te NoRecovery property to False.  
        rs.NoRecovery = False  
  
        'Add the device that contains the differential backup to the Restore object.  
        rs.Devices.Add(bdid)  
  
        'Restore the differential database backup with recovery.  
        rs.SqlRestore(srv)  
  
        'Inform the user that the differential database restore is complete.  
        Console.WriteLine("Differential Database Restore complete.")  
  
        'Remove the device.  
        rs.Devices.Remove(bdid)  
  
        'Set the database recovery mode back to its original value.  
        srv.Databases("AdventureWorks2012").DatabaseOptions.RecoveryModel = recoverymod  
  
        'Drop the table that was added.  
        srv.Databases("AdventureWorks2012").Tables("test_table").Drop()  
        srv.Databases("AdventureWorks2012").Alter()  
  
        'Remove the backup files from the hard disk.  
        My.Computer.FileSystem.DeleteFile("C:\Program Files\Microsoft SQL Server\MSSQL.12\MSSQL\Backup\Test_Full_Backup1")  
        My.Computer.FileSystem.DeleteFile("C:\Program Files\Microsoft SQL Server\MSSQL.12\MSSQL\Backup\Test_Differential_Backup1")  
    End Sub  
End Module  
```  
  
## <a name="backing-up-databases-and-transaction-logs-in-visual-c"></a><span data-ttu-id="c2d85-117">Visual C# でのデータベースおよびトランザクション ログのバックアップ</span><span class="sxs-lookup"><span data-stu-id="c2d85-117">Backing Up Databases and Transaction Logs in Visual C#</span></span>  
 <span data-ttu-id="c2d85-118">このコード例では、既存のデータベースをファイルにバックアップする方法と復元する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c2d85-118">This code example shows how to back up an existing database to a file, and then how to restore it.</span></span>  
  
```csharp
using Microsoft.SqlServer.Management.Common;  
using Microsoft.SqlServer.Management.Smo;  
  
class A {  
   public static void Main() {  
      // Connect to the local, default instance of SQL Server.   
      Server srv = new Server();  
      // Reference the AdventureWorks2012 database.   
      Database db = default(Database);  
      db = srv.Databases["AdventureWorks2012"];  
  
      // Store the current recovery model in a variable.   
      int recoverymod;  
      recoverymod = (int)db.DatabaseOptions.RecoveryModel;  
  
      // Define a Backup object variable.   
      Backup bk = new Backup();  
  
      // Specify the type of backup, the description, the name, and the database to be backed up.   
      bk.Action = BackupActionType.Database;  
      bk.BackupSetDescription = "Full backup of Adventureworks2012";  
      bk.BackupSetName = "AdventureWorks2012 Backup";  
      bk.Database = "AdventureWorks2012";  
  
      // Declare a BackupDeviceItem by supplying the backup device file name in the constructor, and the type of device is a file.   
      BackupDeviceItem bdi = default(BackupDeviceItem);  
      bdi = new BackupDeviceItem("Test_Full_Backup1", DeviceType.File);  
  
      // Add the device to the Backup object.   
      bk.Devices.Add(bdi);  
      // Set the Incremental property to False to specify that this is a full database backup.   
      bk.Incremental = false;  
  
      // Set the expiration date.   
      System.DateTime backupdate = new System.DateTime();  
      backupdate = new System.DateTime(2006, 10, 5);  
      bk.ExpirationDate = backupdate;  
  
      // Specify that the log must be truncated after the backup is complete.   
      bk.LogTruncation = BackupTruncateLogType.Truncate;  
  
      // Run SqlBackup to perform the full database backup on the instance of SQL Server.   
      bk.SqlBackup(srv);  
  
      // Inform the user that the backup has been completed.   
      System.Console.WriteLine("Full Backup complete.");  
  
      // Remove the backup device from the Backup object.   
      bk.Devices.Remove(bdi);  
  
      // Make a change to the database, in this case, add a table called test_table.   
      Table t = default(Table);  
      t = new Table(db, "test_table");  
      Column c = default(Column);  
      c = new Column(t, "col", DataType.Int);  
      t.Columns.Add(c);  
      t.Create();  
  
      // Create another file device for the differential backup and add the Backup object.   
      BackupDeviceItem bdid = default(BackupDeviceItem);  
      bdid = new BackupDeviceItem("Test_Differential_Backup1", DeviceType.File);  
  
      // Add the device to the Backup object.   
      bk.Devices.Add(bdid);  
  
      // Set the Incremental property to True for a differential backup.   
      bk.Incremental = true;  
  
      // Run SqlBackup to perform the incremental database backup on the instance of SQL Server.   
      bk.SqlBackup(srv);  
  
      // Inform the user that the differential backup is complete.   
      System.Console.WriteLine("Differential Backup complete.");  
  
      // Remove the device from the Backup object.   
      bk.Devices.Remove(bdid);  
  
      // Delete the AdventureWorks2012 database before restoring it  
      // db.Drop();  
  
      // Define a Restore object variable.  
      Restore rs = new Restore();  
  
      // Set the NoRecovery property to true, so the transactions are not recovered.   
      rs.NoRecovery = true;  
  
      // Add the device that contains the full database backup to the Restore object.   
      rs.Devices.Add(bdi);  
  
      // Specify the database name.   
      rs.Database = "AdventureWorks2012";  
  
      // Restore the full database backup with no recovery.   
      rs.SqlRestore(srv);  
  
      // Inform the user that the Full Database Restore is complete.   
      Console.WriteLine("Full Database Restore complete.");  
  
      // reacquire a reference to the database  
      db = srv.Databases["AdventureWorks2012"];  
  
      // Remove the device from the Restore object.  
      rs.Devices.Remove(bdi);  
  
      // Set the NoRecovery property to False.   
      rs.NoRecovery = false;  
  
      // Add the device that contains the differential backup to the Restore object.   
      rs.Devices.Add(bdid);  
  
      // Restore the differential database backup with recovery.   
      rs.SqlRestore(srv);  
  
      // Inform the user that the differential database restore is complete.   
      System.Console.WriteLine("Differential Database Restore complete.");  
  
      // Remove the device.   
      rs.Devices.Remove(bdid);  
  
      // Set the database recovery mode back to its original value.  
      db.RecoveryModel = (RecoveryModel)recoverymod;  
  
      // Drop the table that was added.   
      db.Tables["test_table"].Drop();  
      db.Alter();  
  
      // Remove the backup files from the hard disk.  
      // This location is dependent on the installation of SQL Server  
      System.IO.File.Delete("C:\\Program Files\\Microsoft SQL Server\\MSSQL12.MSSQLSERVER\\MSSQL\\Backup\\Test_Full_Backup1");  
      System.IO.File.Delete("C:\\Program Files\\Microsoft SQL Server\\MSSQL12.MSSQLSERVER\\MSSQL\\Backup\\Test_Differential_Backup1");  
   }  
}  
```  
  
## <a name="backing-up-databases-and-transaction-logs-in-powershell"></a><span data-ttu-id="c2d85-119">PowerShell でのデータベースおよびトランザクション ログのバックアップ</span><span class="sxs-lookup"><span data-stu-id="c2d85-119">Backing Up Databases and Transaction Logs in PowerShell</span></span>  
 <span data-ttu-id="c2d85-120">このコード例では、既存のデータベースをファイルにバックアップする方法と復元する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c2d85-120">This code example shows how to back up an existing database to a file, and then how to restore it.</span></span>  
  
```powershell
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Reference the AdventureWorks database.  
$db = $srv.Databases["AdventureWorks"]  
  
#Store the current recovery model in a variable.  
$recoverymod = $db.DatabaseOptions.RecoveryModel  
  
#Create a Backup object  
$bk = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Backup  
  
#set to backup the database  
$bk.Action = [Microsoft.SqlServer.Management.SMO.BackupActionType]::Database  
  
#Set back up properties  
$bk.BackupSetDescription = "Full backup of AdventureWorks"  
$bk.BackupSetName = "AdventureWorks Backup"  
$bk.Database = "AdventureWorks"  
  
#Declare a BackupDeviceItem by supplying the backup device file name in the constructor,   
#and the type of device is a file.  
$dt = [Microsoft.SqlServer.Management.SMO.DeviceType]::File  
$bdi = New-Object -TypeName Microsoft.SqlServer.Management.SMO.BackupDeviceItem `  
-argumentlist "Test_FullBackup1", $dt  
  
#Add the device to the Backup object.  
$bk.Devices.Add($bdi)  
  
#Set the Incremental property to False to specify that this is a full database backup.  
$bk.Incremental = $false  
  
#Set the expiration date.  
$bk.ExpirationDate = get-date "10/05/2006"  
  
#Specify that the log must be truncated after the backup is complete.  
$bk.LogTruncation = [Microsoft.SqlServer.Management.SMO.BackupTruncateLogType]::Truncate  
  
#Run SqlBackup to perform the full database backup on the instance of SQL Server.  
$bk.SqlBackup($srv)  
  
#Inform the user that the backup has been completed.  
"Full Backup complete."  
  
#Remove the backup device from the Backup object.  
$bk.Devices.Remove($bdi)  
  
#Make a change to the database, in this case, add a table called test_table.  
$t = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Table -argumentlist $db, "test_table"  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::int  
$c = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $t, "col", $type       
$t.Columns.Add($c)  
$t.Create()  
  
#Create another file device for the differential backup and add the Backup object.  
# $dt is file backup device  
$bdid = New-Object -TypeName Microsoft.SqlServer.Management.SMO.BackupDeviceItem `  
-argumentlist "Test_DifferentialBackup1", $dt  
#Add this device to the backup set  
$bk.Devices.Add($bdid)  
  
#Set the Incremental property to True for a differential backup.  
$bk.Incremental = $true  
  
#Run SqlBackup to perform the incremental database backup on the instance of SQL Server.  
$bk.SqlBackup($srv)  
  
#Inform the user that the differential backup is complete.  
"Differential Backup complete."  
  
#Remove the device from the Backup object.  
$bk.Devices.Remove($bdid)  
  
#Delete the AdventureWorks database before restoring it.  
$db.Drop()  
  
#Define a Restore object variable.  
$rs = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Restore  
  
#Set the NoRecovery property to true, so the transactions are not recovered.  
$rs.NoRecovery = $true  
  
#Add the device that contains the full database backup to the Restore object.  
$rs.Devices.Add($bdi)  
  
#Specify the database name.  
$rs.Database = "AdventureWorks"  
#Restore the full database backup with no recovery.  
$rs.SqlRestore($srv)  
  
#Inform the user that the Full Database Restore is complete.  
"Full Database Restore complete."  
  
#Remove the device from the Restore object.  
$rs.Devices.Remove($bdi)  
  
#Set the NoRecovery property to False.  
$rs.NoRecovery = $false  
  
#Add the device that contains the differential backup to the Restore object.  
$rs.Devices.Add($bdid)  
  
#Restore the differential database backup with recovery.  
$rs.SqlRestore($srv)  
  
#Inform the user that the differential database restore is complete.  
"Differential Database Restore complete."  
  
#Remove the device.  
$rs.Devices.Remove($bdid)  
  
#Set the database recovery mode back to its original value.  
$db = $srv.Databases["AdventureWorks"]  
$db.DatabaseOptions.RecoveryModel = $recoverymod  
  
#Drop the table that was added.  
$db.Tables["test_table"].Drop()  
$db.Alter()  
  
#Delete the backup files - the exact location depends on your installation  
del "C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\Test_FullBackup1"  
del "C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\Test_DifferentialBackup1"  
```  
  
## <a name="running-database-integrity-checks-in-visual-basic"></a><span data-ttu-id="c2d85-121">Visual Basic でのデータベースの整合性確認の実行</span><span class="sxs-lookup"><span data-stu-id="c2d85-121">Running Database Integrity Checks in Visual Basic</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c2d85-122">には、データ整合性の確認手段が提供されています。</span><span class="sxs-lookup"><span data-stu-id="c2d85-122">provides data integrity checking.</span></span> <span data-ttu-id="c2d85-123">このコード例では、指定されたデータベースに対してデータベース整合性の型チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="c2d85-123">This code example runs a database consistency type check on the specified database.</span></span> <span data-ttu-id="c2d85-124">この例では、<xref:Microsoft.SqlServer.Management.Smo.Database.CheckTables%2A> が使用されていますが、<xref:Microsoft.SqlServer.Management.Smo.Database.CheckAllocations%2A>、<xref:Microsoft.SqlServer.Management.Smo.Database.CheckCatalog%2A>、および <xref:Microsoft.SqlServer.Management.Smo.Database.CheckIdentityValues%2A> も同様に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c2d85-124">In this example, <xref:Microsoft.SqlServer.Management.Smo.Database.CheckTables%2A> is used, but <xref:Microsoft.SqlServer.Management.Smo.Database.CheckAllocations%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.CheckCatalog%2A>, or <xref:Microsoft.SqlServer.Management.Smo.Database.CheckIdentityValues%2A> can be used similarly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2d85-125"><xref:System.Collections.Specialized.StringCollection> オブジェクトの場合は、`imports System.Collections.Specialized` ステートメントの使用による名前空間への参照が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c2d85-125">The <xref:System.Collections.Specialized.StringCollection> object requires a reference to the namespace using the `imports System.Collections.Specialized` statement.</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
Imports System.Collections.Specialized  
Module S  
   Sub Main()  
      'Connect to the local, default instance of SQL Server.  
      Dim srv As Server  
      srv = New Server  
      'Reference the AdventureWorks2012 database.  
      Dim db As Database  
      db = srv.Databases("AdventureWorks2012")  
      'Note, to use the StringCollection type the System.Collections.Specialized system namespace must be included in the imports statements.  
      Dim sc As StringCollection  
      'Run the CheckTables method and display the results from the returned StringCollection variable.  
      sc = db.CheckTables(RepairType.None)  
      Dim c As Integer  
      For c = 0 To sc.Count - 1  
         Console.WriteLine(sc.Item(c))  
      Next  
   End Sub  
End Module  
```  
  
## <a name="running-database-integrity-checks-in-visual-c"></a><span data-ttu-id="c2d85-126">Visual C# でのデータベースの整合性確認の実行</span><span class="sxs-lookup"><span data-stu-id="c2d85-126">Running Database Integrity Checks in Visual C#</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c2d85-127">には、データ整合性の確認手段が提供されています。</span><span class="sxs-lookup"><span data-stu-id="c2d85-127">provides data integrity checking.</span></span> <span data-ttu-id="c2d85-128">このコード例では、指定されたデータベースに対してデータベース整合性の型チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="c2d85-128">This code example runs a database consistency type check on the specified database.</span></span> <span data-ttu-id="c2d85-129">この例では、<xref:Microsoft.SqlServer.Management.Smo.Database.CheckTables%2A> が使用されていますが、<xref:Microsoft.SqlServer.Management.Smo.Database.CheckAllocations%2A>、<xref:Microsoft.SqlServer.Management.Smo.Database.CheckCatalog%2A>、および <xref:Microsoft.SqlServer.Management.Smo.Database.CheckIdentityValues%2A> も同様に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c2d85-129">In this example, <xref:Microsoft.SqlServer.Management.Smo.Database.CheckTables%2A> is used, but <xref:Microsoft.SqlServer.Management.Smo.Database.CheckAllocations%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.CheckCatalog%2A>, or <xref:Microsoft.SqlServer.Management.Smo.Database.CheckIdentityValues%2A> can be used similarly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2d85-130"><xref:System.Collections.Specialized.StringCollection> オブジェクトの場合は、`imports System.Collections.Specialized` ステートメントの使用による名前空間への参照が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c2d85-130">The <xref:System.Collections.Specialized.StringCollection> object requires a reference to the namespace using the `imports System.Collections.Specialized` statement.</span></span>  
  
```csharp
using Microsoft.SqlServer.Management.Common;  
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
class A {  
   public static void Main() {  
      // Connect to the local, default instance of SQL Server.   
      Server srv = new Server();  
  
      // Reference the AdventureWorks2012 database.             
      Database db = srv.Databases["AdventureWorks2012"];  
  
      // Note, to use the StringCollection type the System.Collections.Specialized system namespace must be included in the imports statements.   
      System.Collections.Specialized.StringCollection sc;  
  
      // Run the CheckTables method and display the results from the returned StringCollection variable.   
      sc = db.CheckTables(RepairType.None);  
  
      foreach (string c in sc) {  
         Console.WriteLine(c);  
      }  
   }  
}  
```  
  
## <a name="running-database-integrity-checks-in-powershell"></a><span data-ttu-id="c2d85-131">PowerShell でのデータベースの整合性確認の実行</span><span class="sxs-lookup"><span data-stu-id="c2d85-131">Running Database Integrity Checks in PowerShell</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c2d85-132">には、データ整合性の確認手段が提供されています。</span><span class="sxs-lookup"><span data-stu-id="c2d85-132">provides data integrity checking.</span></span> <span data-ttu-id="c2d85-133">このコード例では、指定されたデータベースに対してデータベース整合性の型チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="c2d85-133">This code example runs a database consistency type check on the specified database.</span></span> <span data-ttu-id="c2d85-134">この例では、<xref:Microsoft.SqlServer.Management.Smo.Database.CheckTables%2A> が使用されていますが、<xref:Microsoft.SqlServer.Management.Smo.Database.CheckAllocations%2A>、<xref:Microsoft.SqlServer.Management.Smo.Database.CheckCatalog%2A>、および <xref:Microsoft.SqlServer.Management.Smo.Database.CheckIdentityValues%2A> も同様に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c2d85-134">In this example, <xref:Microsoft.SqlServer.Management.Smo.Database.CheckTables%2A> is used, but <xref:Microsoft.SqlServer.Management.Smo.Database.CheckAllocations%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.CheckCatalog%2A>, or <xref:Microsoft.SqlServer.Management.Smo.Database.CheckIdentityValues%2A> can be used similarly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2d85-135"><xref:System.Collections.Specialized.StringCollection> オブジェクトの場合は、`imports System.Collections.Specialized` ステートメントの使用による名前空間への参照が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c2d85-135">The <xref:System.Collections.Specialized.StringCollection> object requires a reference to the namespace using the `imports System.Collections.Specialized` statement.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
$sc = $db.CheckTables([Microsoft.SqlServer.Management.SMO.RepairType]::None)  
ForEach ($c In $sc)  
{  
    $c  
}  
```  
