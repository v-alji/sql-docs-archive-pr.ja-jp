---
title: バックアップと復元によるデータベースのコピー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], back up and restore
- restoring databases [SQL Server], previous SQL Server versions
- database restores [SQL Server], copying databases
- restoring databases [SQL Server], onto another server instance
- restoring [SQL Server], onto another server instance
- backing up databases [SQL Server], copying databases
- database backups [SQL Server], copying databases
ms.assetid: b93e9701-72a0-408e-958c-dc196872c040
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8ffed36767f961f7482aa0dccf755118c80c019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715397"
---
# <a name="copy-databases-with-backup-and-restore"></a><span data-ttu-id="aeaae-102">バックアップと復元によるデータベースのコピー</span><span class="sxs-lookup"><span data-stu-id="aeaae-102">Copy Databases with Backup and Restore</span></span>
  <span data-ttu-id="aeaae-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンを使用して作成したユーザー データベースのバックアップを復元して、新しいデータベースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can create a new database by restoring a backup of a user database created by using [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version.</span></span> <span data-ttu-id="aeaae-104">ただし、以前のバージョンの **を使用して作成された**master **、** model **、および** msdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="aeaae-104">However, backups of **master**, **model** and **msdb** that were created by using an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="aeaae-105">また、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のバックアップを以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で復元することもできません。</span><span class="sxs-lookup"><span data-stu-id="aeaae-105">Also, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] backups cannot be restored by any earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="aeaae-106">では、以前のバージョンとは異なる既定パスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-106">uses a different default path than earlier versions.</span></span> <span data-ttu-id="aeaae-107">そのため、以前のバージョンの既定の場所で作成されたデータベースのバックアップを復元するには、MOVE オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeaae-107">Therefore, to restore backups of a database created in the default location of earlier versions you must use the MOVE option.</span></span> <span data-ttu-id="aeaae-108">新しい既定パスの詳細については、「 [SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeaae-108">For information about the new default path see [File Locations for Default and Named Instances of SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).</span></span> <span data-ttu-id="aeaae-109">データベース ファイルの移動の詳細については、このトピックの「データベース ファイルの移動」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeaae-109">For more information about moving database files, see "Moving the Database Files," later in this topic.</span></span>  
  
## <a name="general-steps-for-using-backup-and-restore-to-copy-a-database"></a><span data-ttu-id="aeaae-110">バックアップと復元を使用してデータベースをコピーする一般的な手順</span><span class="sxs-lookup"><span data-stu-id="aeaae-110">General Steps for Using Backup and Restore to Copy a Database</span></span>  
 <span data-ttu-id="aeaae-111">バックアップと復元を使用して他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにデータベースをコピーするとき、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行するコピー元とコピー先のコンピューターのプラットフォームは問いません。</span><span class="sxs-lookup"><span data-stu-id="aeaae-111">When you use backup and restore to copy a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the source and destination computers can be any platform on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs.</span></span>  
  
 <span data-ttu-id="aeaae-112">一般的な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aeaae-112">The general steps are:</span></span>  
  
1.  <span data-ttu-id="aeaae-113">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のインスタンスにあるコピー元データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="aeaae-113">Back up the source database, which can reside on an instance of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later.</span></span> <span data-ttu-id="aeaae-114">この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを実行しているコンピューターが *コピー元コンピューター*です。</span><span class="sxs-lookup"><span data-stu-id="aeaae-114">The computer on which this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running is the *source computer*.</span></span>  
  
2.  <span data-ttu-id="aeaae-115">データベースのコピー先となるコンピューター (*対象のコンピューター*) で、データベースの復元先ののインスタンスに接続し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-115">On the computer to which you want to copy the database (the *destination computer*), connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you plan to restore the database.</span></span> <span data-ttu-id="aeaae-116">必要に応じて、コピー元データベースのバックアップに使用したのと同じバックアップ デバイスをコピー先のサーバー インスタンスにも作成します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-116">If needed, on the destination server instance, create the same backup devices as used to the backup of the source databases.</span></span>  
  
3.  <span data-ttu-id="aeaae-117">コピー元データベースのバックアップをコピー先コンピューターに復元します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-117">Restore the backup of the source database on the destination computer.</span></span> <span data-ttu-id="aeaae-118">データベースを復元すると、すべてのデータベース ファイルが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-118">Restoring the database automatically creates all of the database files.</span></span>  
  
 <span data-ttu-id="aeaae-119">次のトピックで、この処理に影響する可能性がある考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-119">The following topics address additional considerations that may affect this process.</span></span>  
  
## <a name="before-you-restore-database-files"></a><span data-ttu-id="aeaae-120">データベース ファイルを復元する前に</span><span class="sxs-lookup"><span data-stu-id="aeaae-120">Before You Restore Database Files</span></span>  
 <span data-ttu-id="aeaae-121">データベースを復元すると、復元しているデータベースに必要なデータベース ファイルが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-121">Restoring a database automatically creates the database files that are needed by the restoring database.</span></span> <span data-ttu-id="aeaae-122">既定では、復元操作時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって作成されるファイルの名前とパスは、コピー元コンピューター上の元のデータベースのバックアップ ファイルと同一です。</span><span class="sxs-lookup"><span data-stu-id="aeaae-122">By default, the files that are created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] during the restoration process use the same names and paths as the backup files from the original database on the source computer.</span></span>  
  
 <span data-ttu-id="aeaae-123">必要に応じて、データベースを復元するときに、復元するデータベースのデバイス マッピング、ファイル名、またはパスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-123">Optionally, when restoring the database, you can specify the device mapping, file names, or path for the restoring database.</span></span> <span data-ttu-id="aeaae-124">これは、次のような状況で必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="aeaae-124">This might be necessary in the following situations:</span></span>  
  
-   <span data-ttu-id="aeaae-125">コピー元のコンピューター上のデータベースで使用されているディレクトリ構造やドライブ マッピングが他のコンピューター上に存在しない。</span><span class="sxs-lookup"><span data-stu-id="aeaae-125">The directory structure or drive mapping used by the database on the original computer not exist on the other computer.</span></span> <span data-ttu-id="aeaae-126">たとえば、既定でドライブ E に復元されるファイルがバックアップに含まれているのに、コピー先コンピューターにドライブ E が存在しない場合です。</span><span class="sxs-lookup"><span data-stu-id="aeaae-126">For example, perhaps the backup contains a file that would be restored to drive E by default, but the destination computer lacks a drive E.</span></span>  
  
-   <span data-ttu-id="aeaae-127">コピー先の場所の容量が十分ではない。</span><span class="sxs-lookup"><span data-stu-id="aeaae-127">The target location might have insufficient space.</span></span>  
  
-   <span data-ttu-id="aeaae-128">復元先に存在するデータベースの名前を再利用していて、そのファイルのいずれかがバックアップ セット内のデータベース ファイルと同じ名前である場合は、次のいずれかの結果になります。</span><span class="sxs-lookup"><span data-stu-id="aeaae-128">You are reusing a database name that exists on the restore destination and any of its files is named the same as a database file in the backup set, one of the following occurs:</span></span>  
  
    -   <span data-ttu-id="aeaae-129">既存のデータベース ファイルを上書きできる場合は、上書きされます (別のデータベース名に属しているファイルには影響しません)。</span><span class="sxs-lookup"><span data-stu-id="aeaae-129">If the existing database file can be overwritten, it will be overwritten (this would not affect a file that belongs to a different database name).</span></span>  
  
    -   <span data-ttu-id="aeaae-130">既存のファイルを上書きできない場合は、復元エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-130">If the existing file cannot be overwritten, a restore error would occur.</span></span>  
  
 <span data-ttu-id="aeaae-131">エラーや意図しない結果を回避するには、復元操作の前に、 [backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql)履歴テーブルを使用して、復元するバックアップのデータベースとログファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-131">To avoid errors and unintended consequences, before the restore operation, you can use the [backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql) history table to find out the database and log files in the backup you plan to restore.</span></span>  
  
## <a name="moving-the-database-files"></a><span data-ttu-id="aeaae-132">データベースファイルの移動</span><span class="sxs-lookup"><span data-stu-id="aeaae-132">Moving the Database Files</span></span>  
 <span data-ttu-id="aeaae-133">前に示した理由によりデータベース バックアップ内のファイルをコピー先コンピューターに復元できない場合は、復元のときにファイルを新しい場所に移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeaae-133">If the files within the database backup cannot be restored onto the destination computer because of the reasons mentioned earlier, it is necessary to move the files to a new location while they are being restored.</span></span> <span data-ttu-id="aeaae-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-134">For example:</span></span>  
  
-   <span data-ttu-id="aeaae-135">以前のバージョンの既定の場所に作成されたバックアップからデータベースを復元する場合。</span><span class="sxs-lookup"><span data-stu-id="aeaae-135">You want to restore a database from backups created in the default location of the earlier version.</span></span>  
  
-   <span data-ttu-id="aeaae-136">容量の制限により、バックアップ内のデータベース ファイルを別のドライブに復元する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="aeaae-136">It may be necessary to restore some of the database files in the backup to a different drive because of capacity considerations.</span></span> <span data-ttu-id="aeaae-137">ディスク ドライブの数やサイズ、またはソフトウェア構成が同じであるコンピューターが組織内に存在することはまれなので、このようなことが頻発します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-137">This is likely to be a common occurrence because most computers within an organization do not have the same number and size of disk drives or identical software configurations.</span></span>  
  
-   <span data-ttu-id="aeaae-138">既存のデータベースをテストするため、そのコピーを同じコンピューター上に作成する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="aeaae-138">It may be necessary to create a copy of an existing database on the same computer for testing purposes.</span></span> <span data-ttu-id="aeaae-139">この場合、元のデータベースのデータベース ファイルが既に存在するので、復元操作でデータベースをコピーする場合は異なるファイル名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeaae-139">In this case, the database files for the original database already exist, so different file names need to be specified when the database copy is created during the restore operation.</span></span>  
  
 <span data-ttu-id="aeaae-140">詳細については、このトピックの「ファイルとファイル グループを新しい場所に復元するには」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeaae-140">For more information, see "To restore files and filegroups to a new location," later in this topic.</span></span>  
  
## <a name="changing-the-database-name"></a><span data-ttu-id="aeaae-141">データベース名の変更</span><span class="sxs-lookup"><span data-stu-id="aeaae-141">Changing the Database Name</span></span>  
 <span data-ttu-id="aeaae-142">データベースをコピー先コンピューターに復元するときにデータベースの名前を変更できます。データベースを先に復元してから名前を手動で変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="aeaae-142">The name of the database can be changed as it is restored to the destination computer, without having to restore the database first and then change the name manually.</span></span> <span data-ttu-id="aeaae-143">たとえば、データベースがコピーであることを示すため、名前を **Sales** から **SalesCopy** に変更する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="aeaae-143">For example, it may be necessary to change the database name from **Sales** to **SalesCopy** to indicate that this is a copy of a database.</span></span>  
  
 <span data-ttu-id="aeaae-144">データベースを復元するときに明示的に指定するデータベース名が、新しいデータベース名として自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-144">The database name that is explicitly supplied when you restore a database is used automatically as the new database name.</span></span> <span data-ttu-id="aeaae-145">そのデータベース名はまだ存在していないため、新しい名前のデータベースがバックアップ内のファイルを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-145">Because the database name does not already exist, a new one is created by using the files in the backup.</span></span>  
  
## <a name="when-upgrading-a-database-by-using-restore"></a><span data-ttu-id="aeaae-146">復元を使用してデータベースをアップグレードする場合</span><span class="sxs-lookup"><span data-stu-id="aeaae-146">When Upgrading a Database by Using Restore</span></span>  
 <span data-ttu-id="aeaae-147">バックアップを以前のバージョンから復元する場合は、バックアップにある各フルテキスト カタログのパス (ドライブとディレクトリ) がコピー先コンピューターに存在するかどうかを事前に知っておくと便利です。</span><span class="sxs-lookup"><span data-stu-id="aeaae-147">When restoring backups from an earlier version, it is helpful to know in advance whether the path (drive and directory) of each of the full-text catalogs in a backup exists on the destination computer.</span></span> <span data-ttu-id="aeaae-148">バックアップにある、カタログ ファイルを含めたすべてのファイルの論理名と物理名 (パスとファイル名) を一覧にするには、RESTORE FILELISTONLY FROM *<backup_device>* ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-148">To list the logical names and physical names, path and file name) of every file in a backup, including the catalog files, use a RESTORE FILELISTONLY FROM *<backup_device>* statement.</span></span> <span data-ttu-id="aeaae-149">詳細については、[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeaae-149">For more information, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>  
  
 <span data-ttu-id="aeaae-150">コピー先のコンピューターに同一のパスが存在しない場合、2 つの方法で対処できます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-150">If the same path does not exist on the destination computer, you have two alternatives:</span></span>  
  
-   <span data-ttu-id="aeaae-151">コピー先コンピューターにも同じドライブ/ディレクトリ マッピングを作成します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-151">Create the equivalent drive/directory mapping on the destination computer.</span></span>  
  
-   <span data-ttu-id="aeaae-152">RESTORE DATABASE ステートメントで WITH MOVE 句を使用して、復元操作中にカタログ ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="aeaae-152">Move the catalog files to a new location during the restore operation, by using the WITH MOVE clause in your RESTORE DATABASE statement.</span></span> <span data-ttu-id="aeaae-153">詳細については、「 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)で復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="aeaae-153">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
 <span data-ttu-id="aeaae-154">フルテキスト インデックスをアップグレードするための別のオプションの詳細については、「 [フルテキスト検索のアップグレード](../search/upgrade-full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeaae-154">For information about alternative options for upgrading full-text indexes, see [Upgrade Full-Text Search](../search/upgrade-full-text-search.md).</span></span>  
  
## <a name="database-ownership"></a><span data-ttu-id="aeaae-155">データベースの所有権</span><span class="sxs-lookup"><span data-stu-id="aeaae-155">Database Ownership</span></span>  
 <span data-ttu-id="aeaae-156">データベースを別のコンピューターに復元すると、復元操作を開始した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン ユーザーまたは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザーが自動的に新しいデータベースの所有者になります。</span><span class="sxs-lookup"><span data-stu-id="aeaae-156">When a database is restored on another computer, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user who initiates the restore operation becomes the owner of the new database automatically.</span></span> <span data-ttu-id="aeaae-157">復元されたデータベースのシステム管理者または新しいデータベース所有者は、そのデータベースの所有権を変更できます。</span><span class="sxs-lookup"><span data-stu-id="aeaae-157">When the database is restored, the system administrator or the new database owner can change database ownership.</span></span> <span data-ttu-id="aeaae-158">認められていないデータベースの復元を防止するため、メディアまたはバックアップ セットのパスワードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="aeaae-158">To prevent unauthorized restoration of a database, use media or backup set passwords.</span></span>  
  
## <a name="managing-metadata-when-restoring-to-another-server-instance"></a><span data-ttu-id="aeaae-159">別のサーバー インスタンスに復元するときのメタデータの管理</span><span class="sxs-lookup"><span data-stu-id="aeaae-159">Managing Metadata When Restoring to Another Server Instance</span></span>  
 <span data-ttu-id="aeaae-160">データベースを別のサーバー インスタンスに復元するときは、ユーザーおよびアプリケーションに一貫した使用環境を提供するために、復元先のサーバー インスタンスで、ログインやジョブなどのデータベースのメタデータの一部またはすべてを作成し直す必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="aeaae-160">When you restore a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="aeaae-161">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeaae-161">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
 <span data-ttu-id="aeaae-162">**バックアップ セットに含まれているデータ ファイルおよびログ ファイルを表示するには**</span><span class="sxs-lookup"><span data-stu-id="aeaae-162">**To view the data and log files in a backup set**</span></span>  
  
-   [<span data-ttu-id="aeaae-163">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="aeaae-163">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
 <span data-ttu-id="aeaae-164">**ファイルとファイル グループを新しい場所に復元するには**</span><span class="sxs-lookup"><span data-stu-id="aeaae-164">**To restore files and filegroups to a new location**</span></span>  
  
-   [<span data-ttu-id="aeaae-165">新しい場所へのファイルの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="aeaae-165">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="aeaae-166">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="aeaae-166">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 <span data-ttu-id="aeaae-167">**ファイルとファイル グループを既存のファイルに復元するには**</span><span class="sxs-lookup"><span data-stu-id="aeaae-167">**To restore files and filegroups over existing files**</span></span>  
  
-   [<span data-ttu-id="aeaae-168">既存のファイルにファイルとファイル グループを復元する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="aeaae-168">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
 <span data-ttu-id="aeaae-169">**新しい名前でデータベースを復元するには**</span><span class="sxs-lookup"><span data-stu-id="aeaae-169">**To restore a database with a new name**</span></span>  
  
-   [<span data-ttu-id="aeaae-170">データベースバックアップを復元する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="aeaae-170">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 <span data-ttu-id="aeaae-171">**中断された復元操作を再開するには**</span><span class="sxs-lookup"><span data-stu-id="aeaae-171">**To restart an interrupted restore operation**</span></span>  
  
-   [<span data-ttu-id="aeaae-172">中断された復元操作の再開 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="aeaae-172">Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;</span></span>](../backup-restore/restart-an-interrupted-restore-operation-transact-sql.md)  
  
 <span data-ttu-id="aeaae-173">**データベースの所有者を変更するには**</span><span class="sxs-lookup"><span data-stu-id="aeaae-173">**To change the owner of a database**</span></span>  
  
-   [<span data-ttu-id="aeaae-174">sp_changedbowner &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="aeaae-174">sp_changedbowner &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-changedbowner-transact-sql)  
  
 <span data-ttu-id="aeaae-175">**SQL Server 管理オブジェクト (SMO) を使用してデータベースをコピーするには**</span><span class="sxs-lookup"><span data-stu-id="aeaae-175">**To copy a database by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.RelocateFiles%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReplaceDatabase%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
## <a name="see-also"></a><span data-ttu-id="aeaae-176">参照</span><span class="sxs-lookup"><span data-stu-id="aeaae-176">See Also</span></span>  
 <span data-ttu-id="aeaae-177">[他のサーバーへのデータベースのコピー](copy-databases-to-other-servers.md) </span><span class="sxs-lookup"><span data-stu-id="aeaae-177">[Copy Databases to Other Servers](copy-databases-to-other-servers.md) </span></span>  
 <span data-ttu-id="aeaae-178">[SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aeaae-178">[File Locations for Default and Named Instances of SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md) </span></span>  
 <span data-ttu-id="aeaae-179">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="aeaae-179">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 [<span data-ttu-id="aeaae-180">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="aeaae-180">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
