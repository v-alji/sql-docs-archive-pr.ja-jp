---
title: 別のコンピューターへのレポート サーバー データベースの移動 (SSRS ネイティブ モード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 44a9854d-e333-44f6-bdc7-8837b9f34416
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49fd35f57cf783b262b3c690e3047e5f479ab193
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711594"
---
# <a name="moving-the-report-server-databases-to-another-computer-ssrs-native-mode"></a><span data-ttu-id="8ce4a-102">別のコンピューターへのレポート サーバー データベースの移動 (SSRS ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="8ce4a-102">Moving the Report Server Databases to Another Computer (SSRS Native Mode)</span></span>
  <span data-ttu-id="8ce4a-103">インストールで使用されているレポートサーバーデータベースは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 別のコンピューター上のインスタンスに移動できます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-103">You can move the report server databases that are used in an installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] to an instance that is on a different computer.</span></span> <span data-ttu-id="8ce4a-104">reportserver と reportservertempdb データベースは、一緒に移動またはコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-104">Both the reportserver and reportservertempdb databases must be moved or copied together.</span></span> <span data-ttu-id="8ce4a-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の使用環境には、両方のデータベースが必要です。reportservertempdb データベースは、移動する reportserver プライマリ データベースに名前を関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-105">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation requires both databases; the reportservertempdb database must be related by name to the primary reportserver database you are moving.</span></span>  
  
 <span data-ttu-id="8ce4a-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="8ce4a-107">データベースの移動は、レポート サーバー アイテムに現在定義されているスケジュールされた操作には影響しません。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-107">Moving a database does not effect scheduled operations that are currently defined for report server items.</span></span>  
  
-   <span data-ttu-id="8ce4a-108">レポート サーバー サービスを初めて再起動したときに、スケジュールが再作成されます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-108">Schedules will be recreated the first time that you restart the Report Server service.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8ce4a-109">エージェント ジョブは、スケジュールを開始する際に使用され、新しいデータベース インスタンスで再作成されます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-109">Agent jobs that are used to trigger a schedule will be recreated on the new database instance.</span></span> <span data-ttu-id="8ce4a-110">このジョブを新しいコンピューターに移動する必要はありませんが、そのコンピューターで今後使用しないジョブは削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-110">You do not have to move the jobs to the new computer, but you might want to delete jobs on the computer that will no longer be used.</span></span>  
  
-   <span data-ttu-id="8ce4a-111">サブスクリプション、キャッシュされたレポート、およびスナップショットは、移動したデータベースに保持されます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-111">Subscriptions, cached reports, and snapshots are preserved in the moved database.</span></span> <span data-ttu-id="8ce4a-112">データベースの移動後にスナップショットが更新されたデータを取得していない場合は、レポート マネージャーでスナップショット オプションを解除し、 **[適用]** をクリックして変更を保存します。次に、スケジュールを再作成し、もう一度 **[適用]** をクリックして変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-112">If a snapshot is not picking up refreshed data after the database is moved, clear the snapshot options in Report Manager, click **Apply** to save your changes, re-create the schedule, and click **Apply** again to save your changes.</span></span>  
  
-   <span data-ttu-id="8ce4a-113">reportservertempdb に格納される一時的なレポートとユーザー セッション データは、データベースを移動すると保存されます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-113">Temporary report and user session data that is stored in reportservertempdb are persisted when you move that database.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8ce4a-114">には、バックアップと復元、アタッチとデタッチ、コピーなど、データベースを移動するための方法がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-114">provides several approaches for moving databases, including backup and restore, attach and detach, and copy.</span></span> <span data-ttu-id="8ce4a-115">ただし、既存のデータベースを新しいサーバー インスタンスに再配置する場合に、これらすべての方法が適切とは限りません。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-115">Not all approaches are appropriate for relocating an existing database to a new server instance.</span></span> <span data-ttu-id="8ce4a-116">レポート サーバー データベースを移動するために使用する方法は、システムの可用性要件によって異なります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-116">The approach that you should use to move the report server database will vary depending on your system availability requirements.</span></span> <span data-ttu-id="8ce4a-117">レポート サーバー データベースを移動する最も簡単な方法は、レポート サーバー データベースをアタッチおよびデタッチすることです。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-117">The easiest way to move the report server databases is to attach and detach them.</span></span> <span data-ttu-id="8ce4a-118">ただし、この方法を使用する場合、データベースをデタッチするときにレポート サーバーをオフラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-118">However, this approach requires that you take the report server offline while you detach the database.</span></span> <span data-ttu-id="8ce4a-119">サービスの中断を最小限に抑えるには、バックアップと復元が適しています。ただし、この操作を行うには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-119">Backup and restore is a better choice if you want to minimize service disruptions, but you must run [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to perform the operations.</span></span> <span data-ttu-id="8ce4a-120">権限設定がデータベースに保持されないため、データベースをコピーすること (特に、データベース コピー ウィザードの使用) は推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-120">Copying the database is not recommended (specifically, by using the Copy Database Wizard); it does not preserve permission settings in the database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8ce4a-121">このトピックの手順をお勧めできるのは、既存環境に対して行う変更が、レポート サーバー データベースの再配置のみの場合です。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-121">The steps provided in this topic are recommended when relocating the report server database is the only change you are making to the existing installation.</span></span> <span data-ttu-id="8ce4a-122">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストール全体を移行する場合 (データベースの移動と、データベースを使用するレポート サーバー Windows サービスの ID の変更を行う場合)、接続を再構成して、暗号化キーを再設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-122">Migrating an entire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation (that is, moving the database and changing the identity of the Report Server Windows service that uses the database) requires connection reconfiguration and an encryption key reset.</span></span>  
  
## <a name="detaching-and-attaching-the-report-server-databases"></a><span data-ttu-id="8ce4a-123">レポート サーバー データベースのデタッチとアタッチ</span><span class="sxs-lookup"><span data-stu-id="8ce4a-123">Detaching and Attaching the Report Server Databases</span></span>  
 <span data-ttu-id="8ce4a-124">レポート サーバーをオフラインにすると、データベースをデタッチして、使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにデータベースを移動できます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-124">If you can take the report server offline, you can detach the databases to move them to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to use.</span></span> <span data-ttu-id="8ce4a-125">この方法では、権限がデータベースに保持されます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-125">This approach preserves permissions in the databases.</span></span> <span data-ttu-id="8ce4a-126">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] データベースを使用している場合は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の別のインスタンスにそのデータベースを移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-126">If you are using a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] database, you must move it to another [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance.</span></span> <span data-ttu-id="8ce4a-127">データを移動した後、レポート サーバーがそのレポート サーバー データベースに接続されるように再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-127">After you move the databases, you must reconfigure the report server connection to the report server database.</span></span> <span data-ttu-id="8ce4a-128">スケールアウト配置を実行している場合は、各レポート サーバーについて、レポート サーバー データベースの接続を再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-128">If you are running a scale-out deployment, you must reconfigure the report server database connection for each report server in the deployment.</span></span>  
  
 <span data-ttu-id="8ce4a-129">次の手順に従ってデータベースを移動します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-129">Use the following steps to move the databases:</span></span>  
  
1.  <span data-ttu-id="8ce4a-130">移動するレポート サーバー データベースの暗号化キーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-130">Backup the encryption keys for the report server database you want to move.</span></span> <span data-ttu-id="8ce4a-131">キーは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用してバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-131">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool backup the keys.</span></span>  
  
2.  <span data-ttu-id="8ce4a-132">レポート サーバー サービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-132">Stop the Report Server service.</span></span> <span data-ttu-id="8ce4a-133">サービスは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを使用して停止できます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-133">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to stop the service.</span></span>  
  
3.  <span data-ttu-id="8ce4a-134">を起動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レポートサーバーデータベースをホストするインスタンスへの接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-134">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and open a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server databases.</span></span>  
  
4.  <span data-ttu-id="8ce4a-135">レポート サーバー データベースを右クリックし、[タスク] をポイントして **[デタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-135">Right-click the report server database, point to Tasks, and click **Detach**.</span></span> <span data-ttu-id="8ce4a-136">レポート サーバーの一時データベースに対しても、この手順を行います。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-136">Repeat this step for the report server temporary database.</span></span>  
  
5.  <span data-ttu-id="8ce4a-137">使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータ フォルダーに .mdf ファイルおよび .ldf ファイルをコピーまたは移動します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-137">Copy or move the .mdf and .ldf files to the Data folder of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to use.</span></span> <span data-ttu-id="8ce4a-138">2 つのデータベースを移動するので、4 つのファイルがすべて移動またはコピーされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-138">Because you are moving two databases, make sure that you move or copy all four files.</span></span>  
  
6.  <span data-ttu-id="8ce4a-139">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、レポート サーバー データベースを新しくホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-139">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a connection to the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that will host the report server databases.</span></span>  
  
7.  <span data-ttu-id="8ce4a-140">[データベース] ノードを右クリックし、 **[アタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-140">Right-click the Databases node, and then click **Attach**.</span></span>  
  
8.  <span data-ttu-id="8ce4a-141">**[追加]** をクリックして、アタッチするレポート サーバー データベースの .mdf ファイルおよび .ldf ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-141">Click **Add** to select the report server database .mdf and .ldf files that you want to attach.</span></span> <span data-ttu-id="8ce4a-142">レポート サーバーの一時データベースに対しても、この手順を行います。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-142">Repeat this step for the report server temporary database.</span></span>  
  
9. <span data-ttu-id="8ce4a-143">データベースがアタッチされたら、 `RSExecRole` がレポートサーバーデータベースと一時データベースのデータベースロールであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-143">After the databases are attached, verify that the `RSExecRole` is a database role in the report server database and temporary database.</span></span> <span data-ttu-id="8ce4a-144">`RSExecRole`には、レポートサーバーデータベースのテーブルに対する select、insert、update、delete、および reference 権限、およびストアドプロシージャに対する実行権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-144">`RSExecRole` must have select, insert, update, delete, and reference permissions on the report server database tables, and execute permissions on the stored procedures.</span></span> <span data-ttu-id="8ce4a-145">詳細については、「 [RSExecRole の作成](../security/create-the-rsexecrole.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-145">For more information, see [Create the RSExecRole](../security/create-the-rsexecrole.md).</span></span>  
  
10. <span data-ttu-id="8ce4a-146">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動して、レポート サーバー インスタンスへの接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-146">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and open a connection to the report server.</span></span>  
  
11. <span data-ttu-id="8ce4a-147">[データベース] ページで新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを選択し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-147">On the Database page, select the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and then click **Connect**.</span></span>  
  
12. <span data-ttu-id="8ce4a-148">移動したレポート サーバー データベースを選択し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-148">Select the report server database that you just moved, and then click **Apply**.</span></span>  
  
13. <span data-ttu-id="8ce4a-149">[暗号化キー] ページで、[復元] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-149">On the Encryption Keys page, click Restore.</span></span> <span data-ttu-id="8ce4a-150">キーのバックアップ コピーが格納されているファイルとそのパスワードを指定し、ファイルのロックを解除します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-150">Specify the file that contains the backup copy of the keys and the password to unlock the file.</span></span>  
  
14. <span data-ttu-id="8ce4a-151">レポート サーバー サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-151">Restart the Report Server service.</span></span>  
  
## <a name="backing-up-and-restoring-the-report-server-databases"></a><span data-ttu-id="8ce4a-152">レポート サーバー データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="8ce4a-152">Backing Up and Restoring the Report Server Databases</span></span>  
 <span data-ttu-id="8ce4a-153">レポート サーバーをオフラインにできない場合は、バックアップと復元を使用して、レポート サーバー データベースを再配置できます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-153">If you cannot take the report server offline, you can use backup and restore to relocate the report server databases.</span></span> <span data-ttu-id="8ce4a-154">バックアップと復元を実行するには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-154">You must use [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to do the backup and restore.</span></span> <span data-ttu-id="8ce4a-155">データベースを復元した後、新しいサーバー インスタンスのデータベースを使用できるように、レポート サーバーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-155">After you restore the databases, you must configure the report server to use the database on the new server instance.</span></span> <span data-ttu-id="8ce4a-156">詳細については、このトピックの最後にある手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-156">For more information, see the instructions at the end of this topic.</span></span>  
  
### <a name="using-backup-and-copy_only-to-backup-the-report-server-databases"></a><span data-ttu-id="8ce4a-157">レポート サーバー データベースをバックアップする BACKUP および COPY_ONLY の使用</span><span class="sxs-lookup"><span data-stu-id="8ce4a-157">Using BACKUP and COPY_ONLY to Backup the Report Server Databases</span></span>  
 <span data-ttu-id="8ce4a-158">データベースをバックアップする場合、COPY_ONLY 引数を設定します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-158">When backing up the databases, set the COPY_ONLY argument.</span></span> <span data-ttu-id="8ce4a-159">データベースとログ ファイルの両方を必ずバックアップしてください。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-159">Be sure to back up both of the databases and log files.</span></span>  
  
```  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServer  
   SET RECOVERY FULL  
  
-- If the ReportServerData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerData',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerData.bak'  
  
-- Create a logical backup device, ReportServerLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerLog.bak'  
  
-- Back up the full ReportServer database.  
BACKUP DATABASE ReportServer  
   TO ReportServerData  
   WITH COPY_ONLY  
  
-- Back up the ReportServer log.  
BACKUP LOG ReportServer  
   TO ReportServerLog  
   WITH COPY_ONLY  
  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServerTempdb  
   SET RECOVERY FULL  
  
-- If the ReportServerTempDBData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBData',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBData.bak'  
  
-- Create a logical backup device, ReportServerTempDBLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBLog.bak'  
  
-- Back up the full ReportServerTempDB database.  
BACKUP DATABASE ReportServerTempDB  
   TO ReportServerTempDBData  
   WITH COPY_ONLY  
  
-- Back up the ReportServerTempDB log.  
BACKUP LOG ReportServerTempDB  
   TO ReportServerTempDBLog  
   WITH COPY_ONLY  
```  
  
### <a name="using-restore-and-move-to-relocate-the-report-server-databases"></a><span data-ttu-id="8ce4a-160">レポート サーバー データベースを再配置する RESTORE および MOVE の使用</span><span class="sxs-lookup"><span data-stu-id="8ce4a-160">Using RESTORE and MOVE to Relocate the Report Server Databases</span></span>  
 <span data-ttu-id="8ce4a-161">データベースを復元する際には、パスを指定できるように MOVE 引数を使用してください。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-161">When restoring the databases, be sure to include the MOVE argument so that you can specify a path.</span></span> <span data-ttu-id="8ce4a-162">NORECOVERY 引数を使用して最初の復元を行うと、データベースが RESTORING 状態で保たれ、ログのバックアップを確認してどのデータベースを復元するかを決定する時間ができます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-162">Use the NORECOVERY argument to perform the initial restore; this keeps the database in a RESTORING state, giving you time to review log backups to determine which one to restore.</span></span> <span data-ttu-id="8ce4a-163">最後の手順では、RECOVERY 引数を使用して RESTORE 操作を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-163">The final step repeats the RESTORE operation with the RECOVERY argument.</span></span>  
  
 <span data-ttu-id="8ce4a-164">MOVE 引数では、データ ファイルの論理名を使用します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-164">The MOVE argument uses the logical name of the data file.</span></span> <span data-ttu-id="8ce4a-165">論理名を検索するには、 ステートメントを実行してください。 `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`</span><span class="sxs-lookup"><span data-stu-id="8ce4a-165">To find the logical name, execute the following statement: `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`</span></span>  
  
 <span data-ttu-id="8ce4a-166">復元するログ ファイルの位置を指定できるように、次の例では FILE 引数を使用しています。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-166">The following examples include the FILE argument so that you can specify the file position of the log file to restore.</span></span> <span data-ttu-id="8ce4a-167">ファイルの位置を検索するには、 ステートメントを実行してください。 `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`</span><span class="sxs-lookup"><span data-stu-id="8ce4a-167">To find the file position, execute the following statement: `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`</span></span>  
  
 <span data-ttu-id="8ce4a-168">データベースとログ ファイルを復元する場合、RESTORE 操作は個別に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-168">When restoring the database and log files, you should run each RESTORE operation separately.</span></span>  
  
```  
-- Restore the report server database and move to new instance folder   
RESTORE DATABASE ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore the report server log file to new instance folder   
RESTORE LOG ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore and move the report server temporary database  
RESTORE DATABASE ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Restore the temporary database log file to new instance folder   
RESTORE LOG ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServer  
   WITH RECOVERY  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServerTempDB  
   WITH RECOVERY  
GO  
```  
  
### <a name="how-to-configure-the-report-server-database-connection"></a><span data-ttu-id="8ce4a-169">レポート サーバー データベースの接続を構成する方法</span><span class="sxs-lookup"><span data-stu-id="8ce4a-169">How to Configure the Report Server Database Connection</span></span>  
  
1.  <span data-ttu-id="8ce4a-170">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動して、レポート サーバー インスタンスへの接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-170">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and open a connection to the report server.</span></span>  
  
2.  <span data-ttu-id="8ce4a-171">[データベース] ページの **[データベースの変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-171">On the Database page, click **Change Database**.</span></span> <span data-ttu-id="8ce4a-172">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-172">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="8ce4a-173">**[既存のレポート サーバー データベースを選択する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-173">Click **Choose an existing report server database**.</span></span> <span data-ttu-id="8ce4a-174">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-174">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="8ce4a-175">現在レポート サーバー データベースをホストしている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択し、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-175">Select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that now hosts the report server database and click **Test Connection**.</span></span> <span data-ttu-id="8ce4a-176">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-176">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="8ce4a-177">[データベース名] で、使用するレポート サーバー データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-177">In Database Name, select the report server database that you want to use.</span></span> <span data-ttu-id="8ce4a-178">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-178">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="8ce4a-179">レポート サーバーがレポート サーバー データベースに接続するときに使用する資格情報を [資格情報] に指定します。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-179">In Credentials, specify the credentials that the report server will use to connect to the report server database.</span></span> <span data-ttu-id="8ce4a-180">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-180">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="8ce4a-181">**[次へ]** 、 **[完了]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-181">Click **Next** and then **Finish**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ce4a-182">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストールでは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] インスタンスに `RSExecRole` ロールが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-182">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation requires that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance include the `RSExecRole` role.</span></span> <span data-ttu-id="8ce4a-183">ロールの作成、ログインの登録、およびロールの割り当ては、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールでレポート サーバー データベースの接続を設定する際に行います。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-183">Role creation, login registration, and role assignments occur when you set the report server database connection through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="8ce4a-184">別の方法 (特に、rsconfig.exe コマンド プロンプト ユーティリティを使用する場合) で接続を構成する場合は、レポート サーバーが非動作状態になります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-184">If you use alternate approaches (specifically, if you use the rsconfig.exe command prompt utility) to configure the connection, the report server will not be in a working state.</span></span> <span data-ttu-id="8ce4a-185">場合によっては、レポート サーバーを利用可能な状態にするための WMI コードを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-185">You might have to write WMI code to make the report server available.</span></span> <span data-ttu-id="8ce4a-186">詳細については、「 [Reporting Service WMI プロバイダーへのアクセス](../tools/access-the-reporting-services-wmi-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ce4a-186">For more information, see [Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce4a-187">参照</span><span class="sxs-lookup"><span data-stu-id="8ce4a-187">See Also</span></span>  
 <span data-ttu-id="8ce4a-188">[RSExecRole を作成する](../security/create-the-rsexecrole.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4a-188">[Create the RSExecRole](../security/create-the-rsexecrole.md) </span></span>  
 <span data-ttu-id="8ce4a-189">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4a-189">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span></span>  
 <span data-ttu-id="8ce4a-190">[SSRS Configuration Manager &#40;レポートサーバーデータベース接続の構成&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4a-190">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="8ce4a-191">[SSRS Configuration Manager &#40;自動実行アカウントを構成&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4a-191">[Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="8ce4a-192">[Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4a-192">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="8ce4a-193">[rsconfig ユーティリティ &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4a-193">[rsconfig Utility &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) </span></span>  
 <span data-ttu-id="8ce4a-194">[SSRS Configuration Manager &#40;暗号化キーの構成と管理&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4a-194">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="8ce4a-195">レポート サーバー データベース &#40;SSRS ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="8ce4a-195">Report Server Database &#40;SSRS Native Mode&#41;</span></span>](report-server-database-ssrs-native-mode.md)  
  
  
