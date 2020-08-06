---
title: バックアップ デバイス [SQL Server] | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tape backup devices, about tape backup devices
- backup devices [SQL Server]
- disk backup devices [SQL Server]
- database backups [SQL Server], backup devices
- logical devices [SQL Server]
- backup devices [SQL Server], about backup devices
- backing up [SQL Server], backup devices
- removable media [SQL Server]
- network shares [SQL Server]
- backups [SQL Server], backup devices
- tape backup devices
- physical devices [SQL Server]
- backing up databases [SQL Server], backup devices
- devices [SQL Server]
ms.assetid: 35a8e100-3ff2-4844-a5da-dd088c43cba4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8abbba087679d263c00484764ecf445d6e5a006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743326"
---
# <a name="backup-devices-sql-server"></a><span data-ttu-id="f37cf-102">バックアップ デバイス (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f37cf-102">Backup Devices (SQL Server)</span></span>
  <span data-ttu-id="f37cf-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース上でのバックアップ操作中、バックアップ対象のデータ ( *backup*) は、物理バックアップ デバイスに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-103">During a backup operation on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the backed up data (the *backup*) is written to a physical backup device.</span></span> <span data-ttu-id="f37cf-104">この物理バックアップ デバイスは、メディア セットの最初のバックアップが書き込まれるときに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-104">This physical backup device is initialized when the first backup in a media set is written to it.</span></span> <span data-ttu-id="f37cf-105">単一または一連のバックアップ デバイス上にあるバックアップによって、1 つのメディア セットが構成されます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-105">The backups on a set of one or more backup devices compose a single media set.</span></span>  
  
 <span data-ttu-id="f37cf-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f37cf-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="f37cf-107">用語と定義</span><span class="sxs-lookup"><span data-stu-id="f37cf-107">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="f37cf-108">ディスクバックアップデバイスの使用</span><span class="sxs-lookup"><span data-stu-id="f37cf-108">Using Disk Backup Devices</span></span>](#DiskBackups)  
  
-   [<span data-ttu-id="f37cf-109">テープデバイスの使用</span><span class="sxs-lookup"><span data-stu-id="f37cf-109">Using Tape Devices</span></span>](#TapeDevices)  
  
-   [<span data-ttu-id="f37cf-110">論理バックアップ デバイスの使用</span><span class="sxs-lookup"><span data-stu-id="f37cf-110">Using a Logical Backup Device</span></span>](#LogicalBackupDevice)  
  
-   [<span data-ttu-id="f37cf-111">ミラー化バックアップメディアセット</span><span class="sxs-lookup"><span data-stu-id="f37cf-111">Mirrored Backup Media Sets</span></span>](#MirroredMediaSets)  
  
-   [<span data-ttu-id="f37cf-112">SQL Server バックアップのアーカイブ</span><span class="sxs-lookup"><span data-stu-id="f37cf-112">Archiving SQL Server Backups</span></span>](#Archiving)  
  
-   [<span data-ttu-id="f37cf-113">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f37cf-113">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="f37cf-114">用語と定義</span><span class="sxs-lookup"><span data-stu-id="f37cf-114">Terms and Definitions</span></span>  
 <span data-ttu-id="f37cf-115">バックアップ ディスク (backup disk)</span><span class="sxs-lookup"><span data-stu-id="f37cf-115">backup disk</span></span>  
 <span data-ttu-id="f37cf-116">1 つ以上のバックアップ ファイルを含むハード ディスクまたはその他のディスク記憶メディア。</span><span class="sxs-lookup"><span data-stu-id="f37cf-116">A hard disk or other disk storage media that contains one or more backup files.</span></span> <span data-ttu-id="f37cf-117">バックアップ ファイルは正規のオペレーティング システム ファイルです。</span><span class="sxs-lookup"><span data-stu-id="f37cf-117">A backup file is a regular operating system file.</span></span>  
  
 <span data-ttu-id="f37cf-118">メディア セット (media set)</span><span class="sxs-lookup"><span data-stu-id="f37cf-118">media set</span></span>  
 <span data-ttu-id="f37cf-119">テープやディスク ファイルなどのバックアップ メディアに順序を付けてまとめたもの。決まった種類のバックアップ デバイスが複数使用されます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-119">An ordered collection of backup media, tapes or disk files, that uses a fixed type and number of backup devices.</span></span> <span data-ttu-id="f37cf-120">メディア セットの詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-120">For more information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="f37cf-121">物理バックアップ デバイス (physical backup device)</span><span class="sxs-lookup"><span data-stu-id="f37cf-121">physical backup device</span></span>  
 <span data-ttu-id="f37cf-122">オペレーティング システムによって提供されるテープ ドライブまたはディスク ファイル。</span><span class="sxs-lookup"><span data-stu-id="f37cf-122">Either a tape drive or a disk file that is provided by the operating system.</span></span> <span data-ttu-id="f37cf-123">バックアップは 1 ～ 64 個のバックアップ デバイスに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-123">A backup can be written to from 1 to 64 backup devices.</span></span> <span data-ttu-id="f37cf-124">バックアップに複数のバックアップ デバイスが必要な場合、デバイスはすべて 1 種類のデバイス (ディスクまたはテープ) に対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-124">If a backup requires multiple backup devices, the devices all must correspond to a single type of device (disk or tape).</span></span>  
  
 <span data-ttu-id="f37cf-125">SQL Server のバックアップは、ディスクやテープだけでなく、Azure Blob Storage サービスに書き込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-125">SQL Server Backups can also be written to Azure Blob storage service in addition to disk or tape.</span></span>  
  
##  <a name="using-disk-backup-devices"></a><a name="DiskBackups"></a><span data-ttu-id="f37cf-126">ディスクバックアップデバイスの使用</span><span class="sxs-lookup"><span data-stu-id="f37cf-126">Using Disk Backup Devices</span></span>  
 <span data-ttu-id="f37cf-127">**このセクションの内容**</span><span class="sxs-lookup"><span data-stu-id="f37cf-127">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="f37cf-128">物理名を使用したバックアップ ファイルの指定 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f37cf-128">Specifying a Backup File by Using Its Physical Name (Transact-SQL)</span></span>](#BackupFileUsingPhysicalName)  
  
-   [<span data-ttu-id="f37cf-129">ディスク バックアップ ファイルのパスの指定</span><span class="sxs-lookup"><span data-stu-id="f37cf-129">Specifying the Path of a Disk Backup File</span></span>](#BackupFileDiskPath)  
  
-   [<span data-ttu-id="f37cf-130">ネットワーク共有のファイルへのバックアップ</span><span class="sxs-lookup"><span data-stu-id="f37cf-130">Backing Up to a File on a Network Share</span></span>](#NetworkShare)  
  
 <span data-ttu-id="f37cf-131">バックアップ操作によってバックアップがメディア セットに追加されているときにディスク ファイルがいっぱいになると、バックアップ操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-131">If a disk file fills while a backup operation is appending a backup to the media set, the backup operation fails.</span></span> <span data-ttu-id="f37cf-132">バックアップ ファイルの最大サイズはディスク デバイス上の使用可能な空き領域によって決まるため、バックアップ ディスク デバイスの適切なサイズは、バックアップのサイズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-132">The maximum size of a backup file is determined by the free disk space available on the disk device; therefore, the appropriate size for a backup disk device depends on the size of your backups.</span></span>  
  
 <span data-ttu-id="f37cf-133">ディスク バックアップ デバイスには、ATA ドライブなどの単純なディスク デバイスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-133">A disk backup device could be a simple disk device, such as an ATA drive.</span></span> <span data-ttu-id="f37cf-134">また、ホットスワップ可能なディスク ドライブも使用できます。この場合、ドライブ上のいっぱいになったディスクを空のディスクと交換する作業を透過的に行えます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-134">Alternatively, you could use a hot-swappable disk drive that would let you transparently replace a full disk on the drive with an empty disk.</span></span> <span data-ttu-id="f37cf-135">バックアップ ディスクには、サーバー上のローカル ディスクや、共有ネットワーク リソースであるリモート ディスクを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-135">A backup disk can be a local disk on the server or a remote disk that is a shared network resource.</span></span> <span data-ttu-id="f37cf-136">リモート ディスクの使用方法については、このトピックの「 [ネットワーク共有のファイルへのバックアップ](#NetworkShare)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-136">For information about how to use a remote disk, see [Backing Up to a File on a Network Share](#NetworkShare), later in this topic.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f37cf-137">管理ツールを使用すると、タイムスタンプの付いた名前がディスク ファイルに対して自動的に生成されるため、ディスク バックアップ デバイスの操作を柔軟に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-137">management tools are very flexible at handling disk backup devices because they automatically generate a time-stamped name on the disk file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f37cf-138">バックアップ ディスクには、データベースのデータ ディスクやログ ディスクとは別のディスクを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f37cf-138">We recommend that a backup disk be a different disk than the database data and log disks.</span></span> <span data-ttu-id="f37cf-139">これは、データ ディスクやログ ディスクで障害が発生した場合に確実にバックアップにアクセスできるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-139">This is necessary to make sure that you can access the backups if the data or log disk fails.</span></span>  
  
###  <a name="specifying-a-backup-file-by-using-its-physical-name-transact-sql"></a><a name="BackupFileUsingPhysicalName"></a><span data-ttu-id="f37cf-140">物理名を使用したバックアップファイルの指定 (Transact-sql)</span><span class="sxs-lookup"><span data-stu-id="f37cf-140">Specifying a Backup File by Using Its Physical Name (Transact-SQL)</span></span>  
 <span data-ttu-id="f37cf-141">物理デバイス名を使用してバックアップ ファイルを指定するための基本的な [BACKUP](/sql/t-sql/statements/backup-transact-sql) 構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f37cf-141">The basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) syntax for specifying a backup file by using its physical device name is:</span></span>  
  
 <span data-ttu-id="f37cf-142">BACKUP DATABASE *database_name*</span><span class="sxs-lookup"><span data-stu-id="f37cf-142">BACKUP DATABASE *database_name*</span></span>  
  
 <span data-ttu-id="f37cf-143">TO DISK **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="f37cf-143">TO DISK **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="f37cf-144">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-144">For example:</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';  
GO  
```  
  
 <span data-ttu-id="f37cf-145">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントで物理ディスク デバイスを指定するための基本構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f37cf-145">To specify a physical disk device in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, the basic syntax is:</span></span>  
  
 <span data-ttu-id="f37cf-146">RESTORE { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="f37cf-146">RESTORE { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="f37cf-147">FROM DISK **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="f37cf-147">FROM DISK **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="f37cf-148">たとえば、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-148">For example,</span></span>  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';   
```  
  
###  <a name="specifying-the-path-of-a-disk-backup-file"></a><a name="BackupFileDiskPath"></a><span data-ttu-id="f37cf-149">ディスクバックアップファイルのパスの指定</span><span class="sxs-lookup"><span data-stu-id="f37cf-149">Specifying the Path of a Disk Backup File</span></span>  
 <span data-ttu-id="f37cf-150">バックアップ ファイルを指定する場合、その完全パスとファイル名を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-150">When you are specifying a backup file, you should enter its full path and file name.</span></span> <span data-ttu-id="f37cf-151">ファイルへのバックアップ時にファイル名または相対パスだけを指定すると、バックアップ ファイルは既定のバックアップ ディレクトリに配置されます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-151">If you specify only the file name or a relative path when you are backing up to a file, the backup file is put in the default backup directory.</span></span> <span data-ttu-id="f37cf-152">既定のバックアップ ディレクトリは、C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup です ( *n* はサーバー インスタンスの番号です)。</span><span class="sxs-lookup"><span data-stu-id="f37cf-152">The default backup directory is C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup, where *n* is the number of the server instance.</span></span> <span data-ttu-id="f37cf-153">したがって、既定のサーバー インスタンスの場合、既定のバックアップ ディレクトリは C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup になります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-153">Therefore, for the default server instance, the default backup directory is: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup.</span></span>  
  
 <span data-ttu-id="f37cf-154">指定があいまいになる状態を避けるために、特にスクリプトでは、バックアップ ディレクトリのパスを各 DISK 句で明示的に指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f37cf-154">To avoid ambiguity, especially in scripts, we recommend that you explicitly specify the path of the backup directory in every DISK clause.</span></span> <span data-ttu-id="f37cf-155">ただし、これは、クエリ エディターを使用している場合はそれほど重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="f37cf-155">However, this is less important when you are using Query Editor.</span></span> <span data-ttu-id="f37cf-156">この場合、バックアップ ファイルが既定のバックアップ ディレクトリに存在することがわかっていれば、DISK 句からパスを省略できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-156">In that case, if you are sure that the backup file resides in the default backup directory, you can omit the path from a DISK clause.</span></span> <span data-ttu-id="f37cf-157">たとえば、次の `BACKUP` ステートメントでは、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースが、既定のバックアップ ディレクトリにバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-157">For example, the following `BACKUP` statement backs up the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to the default backup directory.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'AdventureWorks2012.bak';  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f37cf-158">既定の場所は、 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer** の **BackupDirectory**レジストリ キーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-158">The default location is stored in the **BackupDirectory** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer**.</span></span>  
  
###  <a name="backing-up-to-a-file-on-a-network-share"></a><a name="NetworkShare"></a><span data-ttu-id="f37cf-159">ネットワーク共有上のファイルへのバックアップ</span><span class="sxs-lookup"><span data-stu-id="f37cf-159">Backing Up to a File on a Network Share</span></span>  
 <span data-ttu-id="f37cf-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からリモート ディスク ファイルにアクセスするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントにネットワーク共有へのアクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-160">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to access a remote disk file, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account must have access to the network share.</span></span> <span data-ttu-id="f37cf-161">これには、バックアップ操作によるネットワーク共有への書き込みに必要な権限、および復元操作によるネットワーク共有からの読み取りに必要な権限も含まれます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-161">This includes having the permissions needed for backup operations to write to the network share and for restore operations to read from it.</span></span> <span data-ttu-id="f37cf-162">ネットワーク ドライブおよび権限の可用性は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されている状況によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-162">The availability of network drives and permissions depends on the context is which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is running:</span></span>  
  
-   <span data-ttu-id="f37cf-163">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がドメイン ユーザー アカウントで実行されているときにネットワーク ドライブにバックアップするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されているセッションのネットワーク ドライブとして共有ドライブをマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-163">To back up to a network drive when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in a domain user account, the shared drive must be mapped as a network drive in the session where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="f37cf-164">コマンド ラインから Sqlservr.exe を起動すると、ログイン セッションでマップしたすべてのドライブが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で認識されます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-164">If you start Sqlservr.exe from command line, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sees any network drives you have mapped in your login session.</span></span>  
  
-   <span data-ttu-id="f37cf-165">Sqlservr.exe をサービスとして実行する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はログイン セッションと関係のない個別のセッションで実行されます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-165">When you run Sqlservr.exe as a service, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs in a separate session that has no relation to your login session.</span></span> <span data-ttu-id="f37cf-166">サービスが実行されているセッションには、マップされた独自のドライブがある場合がありますが、通常はありません。</span><span class="sxs-lookup"><span data-stu-id="f37cf-166">The session in which a service runs can have its own mapped drives, although it usually does not.</span></span>  
  
-   <span data-ttu-id="f37cf-167">ドメイン ユーザーではなくコンピューター アカウントを使用することにより、ネットワーク サービス アカウントで接続できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-167">You can connect with the network service account by using the computer account instead of a domain user.</span></span> <span data-ttu-id="f37cf-168">特定のコンピューターから共有ドライブへのバックアップを可能にするには、そのコンピューター アカウントにアクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-168">To enable backups from specific computers to a shared drive, grant access to the computer accounts.</span></span> <span data-ttu-id="f37cf-169">バックアップを書き込んでいる Sqlservr.exe のプロセスにアクセス権がある限り、BACKUP コマンドを送信するユーザーにアクセス権があるかどうかが問題になることはありません。</span><span class="sxs-lookup"><span data-stu-id="f37cf-169">As long as the Sqlservr.exe process that is writing the backup has access, it is irrelevant whether the user sending the BACKUP command has access.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f37cf-170">ネットワーク経由でデータをバックアップすると、ネットワーク エラーの影響を受ける場合があります。そのため、リモート ディスクを使用する際はバックアップ操作を終了後に検証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f37cf-170">Backing up data over a network can be subject to network errors; therefore, we recommend that when you are using a remote disk you verify the backup operation after it finishes.</span></span> <span data-ttu-id="f37cf-171">詳細については、「[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-171">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
#### <a name="specifying-a-universal-naming-convention-unc-name"></a><span data-ttu-id="f37cf-172">UNC (汎用名前付け規則) 名の指定</span><span class="sxs-lookup"><span data-stu-id="f37cf-172">Specifying a Universal Naming Convention (UNC) Name</span></span>  
 <span data-ttu-id="f37cf-173">バックアップ コマンドや復元コマンドでネットワーク共有を指定するには、ファイルの完全修飾 UNC (汎用名前付け規則) 名をバックアップ デバイスに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-173">To specify a network share in a backup or restore command, you should use the fully qualified universal naming convention (UNC) name of the file for the backup device.</span></span> <span data-ttu-id="f37cf-174">UNC 名の形式は、 **\\\\** _Systemname_ **\\** _ShareName_ **\\** _Path_ **\\** _FileName_です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-174">A UNC name has the form **\\\\**_Systemname_**\\**_ShareName_**\\**_Path_**\\**_FileName_.</span></span>  
  
 <span data-ttu-id="f37cf-175">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-175">For example:</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = '\\BackupSystem\BackupDisk1\AW_backups\AdventureWorksData.Bak';  
GO  
```  
  
##  <a name="using-tape-devices"></a><a name="TapeDevices"></a><span data-ttu-id="f37cf-176">テープデバイスの使用</span><span class="sxs-lookup"><span data-stu-id="f37cf-176">Using Tape Devices</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f37cf-177">テープ バックアップ デバイスは、将来のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でサポートされなくなる予定です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-177">Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f37cf-178">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-178">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="f37cf-179">**このセクションの内容**</span><span class="sxs-lookup"><span data-stu-id="f37cf-179">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="f37cf-180">物理名を使用したバックアップ テープの指定 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f37cf-180">Specifying a Backup Tape by Using Its Physical Name (Transact-SQL)</span></span>](#BackupTapeUsingPhysicalName)  
  
-   [<span data-ttu-id="f37cf-181">テープ固有のバックアップと復元のオプション (Transact-sql)</span><span class="sxs-lookup"><span data-stu-id="f37cf-181">Tape-Specific BACKUP and RESTORE Options (Transact-SQL)</span></span>](#TapeOptions)  
  
-   [<span data-ttu-id="f37cf-182">開いているテープの管理</span><span class="sxs-lookup"><span data-stu-id="f37cf-182">Managing Open Tapes</span></span>](#OpenTapes)  
  
 <span data-ttu-id="f37cf-183">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データをテープにバックアップするには、テープ ドライブが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows オペレーティング システムでサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-183">Backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data to tape requires that the tape drive or drives be supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows operating system.</span></span> <span data-ttu-id="f37cf-184">また、特定のテープ ドライブでは、ドライブの製造元で推奨されているテープのみを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f37cf-184">Additionally, for the given tape drive, we recommend that you use only tapes recommended by the drive manufacturer.</span></span> <span data-ttu-id="f37cf-185">テープ ドライブのインストール方法の詳細については、Windows オペレーティング システムのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-185">For more information about how to install a tape drive, see the documentation for the Windows operating system.</span></span>  
  
 <span data-ttu-id="f37cf-186">テープ ドライブを使用する場合、バックアップ操作は 1 つのテープがいっぱいになると、別のテープで続行できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-186">When a tape drive is used, a backup operation may fill one tape and continue onto another tape.</span></span> <span data-ttu-id="f37cf-187">各テープには、メディア ヘッダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f37cf-187">Each tape contains a media header.</span></span> <span data-ttu-id="f37cf-188">最初に使用されるメディアは *先頭テープ*といいます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-188">The first media used is called the *initial tape*.</span></span> <span data-ttu-id="f37cf-189">その後の各テープは *後続テープ* と呼ばれ、前のテープより 1 つ大きいメディア シーケンス番号が付けられます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-189">Each successive tape is known as a *continuation tape* and has a media sequence number that is one higher than the previous tape.</span></span> <span data-ttu-id="f37cf-190">たとえば、4 つのテープ デバイスに関連付けられているメディア セットには、少なくとも 4 つの先頭テープ (およびデータベースが収まらない場合は 4 組の後続テープ) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-190">For example, a media set associated with four tape devices contains at least four initial tapes (and, if the database does not fit, four series of continuation tapes).</span></span> <span data-ttu-id="f37cf-191">バックアップ セットを追加する場合は、その組に最終テープをセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-191">When appending a backup set, you must mount the last tape in the series.</span></span> <span data-ttu-id="f37cf-192">最終テープがセットされていない場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、セットされているテープの終わりまでスキャンし、テープを変更するように要求します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-192">If the last tape is not mounted, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] scans forward to the end of the mounted tape and then requires that you change the tape.</span></span> <span data-ttu-id="f37cf-193">その時点で、最終テープをセットします。</span><span class="sxs-lookup"><span data-stu-id="f37cf-193">At that point, mount the last tape.</span></span>  
  
 <span data-ttu-id="f37cf-194">テープ バックアップ デバイスは、次の点を除いて、ディスク デバイスと同じように使用します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-194">Tape backup devices are used like disk devices, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="f37cf-195">テープ デバイスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスが動作しているコンピューターに物理的に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-195">The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f37cf-196">リモートのテープ デバイスへのバックアップはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f37cf-196">Backing up to remote tape devices is not supported.</span></span>  
  
-   <span data-ttu-id="f37cf-197">バックアップ操作中にテープ バックアップ デバイスがいっぱいになっても、まだデータを書き込む必要がある場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は新しいテープを挿入するように要求するメッセージを表示し、新しいテープが挿入された後にバックアップ操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-197">If a tape backup device is filled during the backup operation, but more data still must be written, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prompts for a new tape and continues the backup operation after a new tape is loaded.</span></span>  
  
###  <a name="specifying-a-backup-tape-by-using-its-physical-name-transact-sql"></a><a name="BackupTapeUsingPhysicalName"></a><span data-ttu-id="f37cf-198">物理名を使用したバックアップテープの指定 (Transact-sql)</span><span class="sxs-lookup"><span data-stu-id="f37cf-198">Specifying a Backup Tape by Using Its Physical Name (Transact-SQL)</span></span>  
 <span data-ttu-id="f37cf-199">テープ ドライブの物理デバイス名を使用してバックアップ テープを指定するための基本的な [BACKUP](/sql/t-sql/statements/backup-transact-sql) 構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f37cf-199">The basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) syntax for specifying a backup tape using the physical device name of the tape drive is:</span></span>  
  
 <span data-ttu-id="f37cf-200">BACKUP { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="f37cf-200">BACKUP { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="f37cf-201">TO TAPE **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="f37cf-201">TO TAPE **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="f37cf-202">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-202">For example:</span></span>  
  
```  
BACKUP LOG AdventureWorks2012   
   TO TAPE = '\\.\tape0';  
GO  
```  
  
 <span data-ttu-id="f37cf-203">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントで物理テープ デバイスを指定するための基本構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f37cf-203">To specify a physical tape device in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, the basic syntax is:</span></span>  
  
 <span data-ttu-id="f37cf-204">RESTORE { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="f37cf-204">RESTORE { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="f37cf-205">FROM TAPE **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="f37cf-205">FROM TAPE **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
###  <a name="tape-specific-backup-and-restore-options-transact-sql"></a><a name="TapeOptions"></a><span data-ttu-id="f37cf-206">テープ固有のバックアップと復元のオプション (Transact-sql)</span><span class="sxs-lookup"><span data-stu-id="f37cf-206">Tape-Specific BACKUP and RESTORE Options (Transact-SQL)</span></span>  
 <span data-ttu-id="f37cf-207">テープ管理を容易にするには、BACKUP ステートメントで次のテープ固有のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-207">To facilitate tape management, the BACKUP statement provides the following tape-specific options:</span></span>  
  
-   <span data-ttu-id="f37cf-208">{ NOUNLOAD | **UNLOAD** }</span><span class="sxs-lookup"><span data-stu-id="f37cf-208">{ NOUNLOAD | **UNLOAD** }</span></span>  
  
     <span data-ttu-id="f37cf-209">バックアップ操作や復元操作の後にバックアップ テープをテープ ドライブから自動的にアンロードするかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-209">You can control whether a backup tape is unloaded automatically from the tape drive after a backup or restore operation.</span></span> <span data-ttu-id="f37cf-210">UNLOAD または NOUNLOAD はセッションの設定であり、セッションが終了するまで、または代わりとなるオプションの指定によりリセットされるまで有効です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-210">UNLOAD/NOUNLOAD is a session setting that persists for the life of the session or until it is reset by specifying the alternative.</span></span>  
  
-   <span data-ttu-id="f37cf-211">{ **REWIND** | NOREWIND }</span><span class="sxs-lookup"><span data-stu-id="f37cf-211">{ **REWIND** | NOREWIND }</span></span>  
  
     <span data-ttu-id="f37cf-212">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がバックアップ操作や復元操作の後にテープを開いたままにするかどうか、またはその操作が失敗した後にテープを解放して巻き戻すかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-212">You can control whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keeps the tape remains open after the backup or restore operation or releases and rewinds the tape after it fills.</span></span> <span data-ttu-id="f37cf-213">既定の動作では、テープを巻き戻します (REWIND)。</span><span class="sxs-lookup"><span data-stu-id="f37cf-213">The default behavior is to rewind the tape (REWIND).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f37cf-214">BACKUP 構文および引数の詳細については、「[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-214">For more information about the BACKUP syntax and arguments, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="f37cf-215">RESTORE 構文および引数の詳細については、それぞれ「[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)」と「[RESTORE の引数 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-215">For more information about the RESTORE syntax and arguments, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql), respectively.</span></span>  
  
###  <a name="managing-open-tapes"></a><a name="OpenTapes"></a><span data-ttu-id="f37cf-216">開いているテープの管理</span><span class="sxs-lookup"><span data-stu-id="f37cf-216">Managing Open Tapes</span></span>  
 <span data-ttu-id="f37cf-217">開いているテープ デバイスの一覧と、マウント要求の状態を確認するには、 [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) 動的管理ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-217">To view a list of open tape devices and the status of mount requests, query the [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) dynamic management view.</span></span> <span data-ttu-id="f37cf-218">このビューでは、開いているすべてのテープが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-218">This view shows all the open tapes.</span></span> <span data-ttu-id="f37cf-219">これには、次の BACKUP 操作または RESTORE 操作を待機して一時的にアイドル状態になっている使用中のテープも含まれます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-219">These include in-use tapes that are temporarily idle while they wait for the next BACKUP or RESTORE operation.</span></span>  
  
 <span data-ttu-id="f37cf-220">テープが誤って開いたままになっている場合、最も迅速にテープを解放するには、RESTORE REWINDONLY FROM TAPE **=** _backup_device_name_ コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-220">If a tape has been accidentally left open, the fastest way to release the tape is by using the following command: RESTORE REWINDONLY FROM TAPE **=**_backup_device_name_.</span></span> <span data-ttu-id="f37cf-221">詳細については、「[RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-221">For more information, see [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql).</span></span>  
  
## <a name="using-the-azure-blob-storage-service"></a><span data-ttu-id="f37cf-222">Azure Blob Storage サービスの使用</span><span class="sxs-lookup"><span data-stu-id="f37cf-222">Using the Azure Blob Storage Service</span></span>  
 <span data-ttu-id="f37cf-223">SQL Server のバックアップを Azure Blob Storage サービスに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-223">SQL Server Backups can be written to the Azure Blob Storage Service.</span></span>  <span data-ttu-id="f37cf-224">バックアップに Azure Blob ストレージサービスを使用する方法の詳細については、「 [Azure Blob Storage サービスを使用したバックアップと復元の SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-224">For more information on how to use the Azure Blob storage service for your backups, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
##  <a name="using-a-logical-backup-device"></a><a name="LogicalBackupDevice"></a><span data-ttu-id="f37cf-225">論理バックアップデバイスの使用</span><span class="sxs-lookup"><span data-stu-id="f37cf-225">Using a Logical Backup Device</span></span>  
 <span data-ttu-id="f37cf-226">" *論理バックアップ デバイス* " とは、特定の物理バックアップ デバイス (ディスク ファイルやテープ ドライブ) を示す、省略可能なユーザー定義名です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-226">A *logical backup device* is an optional, user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span> <span data-ttu-id="f37cf-227">論理バックアップ デバイスにより、対応する物理バックアップ デバイスを参照する際に間接指定を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-227">A logical backup device lets you use indirection when referencing the corresponding physical backup device.</span></span>  
  
 <span data-ttu-id="f37cf-228">論理バックアップ デバイスの定義には、物理デバイスへの論理名の割り当てが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-228">Defining a logical backup device involves assigning a logical name to a physical device.</span></span> <span data-ttu-id="f37cf-229">たとえば、論理デバイス AdventureWorksBackups が Z:\SQLServerBackups\AdventureWorks2012.bak ファイルまたは \\\\.\tape0 テープ ドライブを指すように定義されたとします。</span><span class="sxs-lookup"><span data-stu-id="f37cf-229">For example, a logical device, AdventureWorksBackups, could be defined to point to the Z:\SQLServerBackups\AdventureWorks2012.bak file or the \\\\.\tape0 tape drive.</span></span> <span data-ttu-id="f37cf-230">その後のバックアップ コマンドおよび復元コマンドでは、DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' や TAPE = '\\\\.\tape0' ではなく、AdventureWorksBackups をバックアップ デバイスとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-230">Backup and restore commands can then specify AdventureWorksBackups as the backup device, instead of DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' or TAPE = '\\\\.\tape0'.</span></span>  
  
 <span data-ttu-id="f37cf-231">論理デバイス名は、サーバー インスタンス上のすべての論理バックアップ デバイスで一意になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-231">The logical device name must be unique among all the logical backup devices on the server instance.</span></span> <span data-ttu-id="f37cf-232">既存の論理デバイス名を表示するには、 [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) カタログ ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-232">To view the existing logical device names, query the [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) catalog view.</span></span> <span data-ttu-id="f37cf-233">このビューでは、各論理バックアップ デバイスの名前が表示され、対応する物理バックアップ デバイスの種類と物理的なファイル名またはパスが示されます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-233">This view displays the name of each logical backup device and describes the type and physical file name or path of the corresponding physical backup device.</span></span>  
  
 <span data-ttu-id="f37cf-234">論理バックアップ デバイスを定義した後、BACKUP コマンドまたは RESTORE コマンドでは、デバイスの物理名ではなく論理バックアップ デバイスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-234">After a logical backup device is defined, in a BACKUP or RESTORE command, you can specify the logical backup device instead of the physical name of the device.</span></span> <span data-ttu-id="f37cf-235">たとえば、次のステートメントでは、 `AdventureWorks2012` データベースが `AdventureWorksBackups` 論理バックアップ デバイスにバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-235">For example, the following statement backs up the `AdventureWorks2012` database to the `AdventureWorksBackups` logical backup device.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO AdventureWorksBackups;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f37cf-236">特定の BACKUP ステートメントまたは RESTORE ステートメントでは、論理バックアップ デバイス名と対応する物理バックアップ デバイス名を交換できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-236">In a given BACKUP or RESTORE statement, the logical backup device name and the corresponding physical backup device name are interchangeable.</span></span>  
  
 <span data-ttu-id="f37cf-237">論理バックアップ デバイスを使用する 1 つの利点は、長い物理パスを使用するよりも使いやすいことです。</span><span class="sxs-lookup"><span data-stu-id="f37cf-237">One advantage of using a logical backup device is that it is simpler to use than a long path.</span></span> <span data-ttu-id="f37cf-238">一連のバックアップを同じパスまたはテープ デバイスに書き込む予定がある場合は、論理バックアップ デバイスを使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-238">Using a logical backup device can help if you plan to write a series of backups to the same path or to a tape device.</span></span> <span data-ttu-id="f37cf-239">論理バックアップ デバイスは、テープ バックアップ デバイスを識別する際に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-239">Logical backup devices are especially useful for identifying tape backup devices.</span></span>  
  
 <span data-ttu-id="f37cf-240">バックアップ スクリプトは、特定の論理バックアップ デバイスを使用するように記述できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-240">A backup script can be written to use a particular logical backup device.</span></span> <span data-ttu-id="f37cf-241">これにより、スクリプトを更新せずに、新しい物理バックアップ デバイスに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-241">This lets you switch to a new physical backup devices without updating the script.</span></span> <span data-ttu-id="f37cf-242">切り替えには、次の処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-242">Switching involves the following process:</span></span>  
  
1.  <span data-ttu-id="f37cf-243">元の論理バックアップ デバイスを削除します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-243">Dropping the original logical backup device.</span></span>  
  
2.  <span data-ttu-id="f37cf-244">新しい論理バックアップ デバイスを定義します。このデバイスは、元の論理デバイス名を使用しますが、別の物理バックアップ デバイスにマップされているものです。</span><span class="sxs-lookup"><span data-stu-id="f37cf-244">Defining a new logical backup device that uses the original logical device name but maps to a different physical backup device.</span></span> <span data-ttu-id="f37cf-245">論理バックアップ デバイスは、テープ バックアップ デバイスを識別する際に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-245">Logical backup devices are especially useful for identifying tape backup devices.</span></span>  
  
##  <a name="mirrored-backup-media-sets"></a><a name="MirroredMediaSets"></a><span data-ttu-id="f37cf-246">ミラー化バックアップメディアセット</span><span class="sxs-lookup"><span data-stu-id="f37cf-246">Mirrored Backup Media Sets</span></span>  
 <span data-ttu-id="f37cf-247">バックアップ メディア セットをミラー化すると、バックアップ デバイスの誤動作の影響を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-247">Mirroring of backup media sets reduces the effect of backup-device malfunctions.</span></span> <span data-ttu-id="f37cf-248">バックアップはデータ損失に対する最後の防護策なので、このような誤動作は非常に深刻です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-248">These malfunctions are especially serious because backups are the last line of defense against data loss.</span></span> <span data-ttu-id="f37cf-249">データベースのサイズが大きくなるにつれて、バックアップ デバイスやメディアの障害によってバックアップを復元できなくなる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-249">As the sizes of databases grow, the probability increases that a failure of a backup device or media will make a backup nonrestorable.</span></span> <span data-ttu-id="f37cf-250">バックアップ メディアをミラー化すると、物理バックアップ デバイスの冗長性が実現され、バックアップの信頼性が向上します。</span><span class="sxs-lookup"><span data-stu-id="f37cf-250">Mirroring backup media increases the reliability of backups by providing redundancy for the physical backup device.</span></span> <span data-ttu-id="f37cf-251">詳細については、「 [ミラー化バックアップ メディア セット &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f37cf-251">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f37cf-252">ミラー化バックアップ メディア セットは、 [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] 以降のバージョンのみでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f37cf-252">Mirrored backup media sets are supported only in [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] and later versions.</span></span>  
  
##  <a name="archiving-sql-server-backups"></a><a name="Archiving"></a><span data-ttu-id="f37cf-253">SQL Server バックアップのアーカイブ</span><span class="sxs-lookup"><span data-stu-id="f37cf-253">Archiving SQL Server Backups</span></span>  
 <span data-ttu-id="f37cf-254">ファイル システム バックアップ ユーティリティを使用してディスクのバックアップをアーカイブし、アーカイブをオフサイトに保存することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f37cf-254">We recommend that you use a file system backup utility to archive the disk backups and that you store the archives off-site.</span></span> <span data-ttu-id="f37cf-255">ディスクを使用することには、アーカイブしたバックアップをネットワーク経由でオフサイトのディスクに書き込めるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="f37cf-255">Using disk has the advantage that you use the network to write the archived backups onto an off-site disk.</span></span> <span data-ttu-id="f37cf-256">Azure Blob Storage サービスは、オフサイト保存のオプションとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-256">The Azure Blob storage service can be used as off-site archival option.</span></span>  <span data-ttu-id="f37cf-257">ディスク バックアップをアップロードするか、Azure Blob Storage サービスにバックアップを直接書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f37cf-257">You can either upload your disk backups, or directly write the backups to the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="f37cf-258">もう 1 つの一般的なアーカイブ方法は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップをローカルのバックアップ ディスクに書き込み、そのバックアップをテープにアーカイブして、そのテープをオフサイトで保存するという形態です。</span><span class="sxs-lookup"><span data-stu-id="f37cf-258">Another common archiving approach is to write [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups onto a local backup disk, archive them to tape, and then store the tapes off-site.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f37cf-259">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f37cf-259">Related Tasks</span></span>  
 <span data-ttu-id="f37cf-260">**ディスク デバイスを使用するには (SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="f37cf-260">**To specify a disk device (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="f37cf-261">バックアップ先としてディスクまたはテープを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-261">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 <span data-ttu-id="f37cf-262">**テープ デバイスを使用するには (SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="f37cf-262">**To specify a tape device (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="f37cf-263">バックアップ先としてディスクまたはテープを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-263">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 <span data-ttu-id="f37cf-264">**論理バックアップ デバイスを定義するには**</span><span class="sxs-lookup"><span data-stu-id="f37cf-264">**To define a logical backup device**</span></span>  
  
-   [<span data-ttu-id="f37cf-265">sp_addumpdevice &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-265">sp_addumpdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
-   [<span data-ttu-id="f37cf-266">ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-266">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="f37cf-267">テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-267">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   <span data-ttu-id="f37cf-268"><xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)</span><span class="sxs-lookup"><span data-stu-id="f37cf-268"><xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)</span></span>  
  
 <span data-ttu-id="f37cf-269">**論理バックアップ デバイスを使用するには**</span><span class="sxs-lookup"><span data-stu-id="f37cf-269">**To use a logical backup device**</span></span>  
  
-   [<span data-ttu-id="f37cf-270">バックアップ先としてディスクまたはテープを指定する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-270">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="f37cf-271">デバイスからのバックアップ復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-271">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
-   [<span data-ttu-id="f37cf-272">BACKUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-272">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  
-   [<span data-ttu-id="f37cf-273">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-273">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
 <span data-ttu-id="f37cf-274">**バックアップ デバイスの情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="f37cf-274">**To View Information About Backup Devices**</span></span>  
  
-   [<span data-ttu-id="f37cf-275">バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-275">Backup History and Header Information &#40;SQL Server&#41;</span></span>](backup-history-and-header-information-sql-server.md)  
  
-   [<span data-ttu-id="f37cf-276">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-276">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="f37cf-277">バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-277">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
 <span data-ttu-id="f37cf-278">**論理バックアップ デバイスを削除するには**</span><span class="sxs-lookup"><span data-stu-id="f37cf-278">**To delete a logical backup device**</span></span>  
  
-   [<span data-ttu-id="f37cf-279">sp_dropdevice &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-279">sp_dropdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)  
  
-   [<span data-ttu-id="f37cf-280">バックアップ デバイスの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-280">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="f37cf-281">参照</span><span class="sxs-lookup"><span data-stu-id="f37cf-281">See Also</span></span>  
 <span data-ttu-id="f37cf-282">[SQL Server: Backup Device オブジェクト](../performance-monitor/sql-server-backup-device-object.md) </span><span class="sxs-lookup"><span data-stu-id="f37cf-282">[SQL Server, Backup Device Object](../performance-monitor/sql-server-backup-device-object.md) </span></span>  
 <span data-ttu-id="f37cf-283">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f37cf-283">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="f37cf-284">[メンテナンス プラン](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="f37cf-284">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 <span data-ttu-id="f37cf-285">[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f37cf-285">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="f37cf-286">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f37cf-286">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="f37cf-287">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f37cf-287">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="f37cf-288">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f37cf-288">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="f37cf-289">[sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f37cf-289">[sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) </span></span>  
 [<span data-ttu-id="f37cf-290">ミラー化バックアップ メディア セット &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f37cf-290">Mirrored Backup Media Sets &#40;SQL Server&#41;</span></span>](mirrored-backup-media-sets-sql-server.md)  
  
  
