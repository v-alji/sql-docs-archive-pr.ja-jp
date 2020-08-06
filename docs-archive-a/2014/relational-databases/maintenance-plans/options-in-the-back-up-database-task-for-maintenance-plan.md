---
title: '[データベースのバックアップ タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.backup.f1
- sql12.swb.maint.maintplanproperties.logbackup.f1
helpviewer_keywords:
- Back Up Database Task dialog box
ms.assetid: ed1ef012-fa14-4ba5-bafe-d1527ba065b3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 952730f09deeede360dff5e2bd83f8cdc8a20a67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639485"
---
# <a name="back-up-database-task-maintenance-plan"></a><span data-ttu-id="bacd4-102">[データベースのバックアップ タスク] (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="bacd4-102">Back Up Database Task (Maintenance Plan)</span></span>
  <span data-ttu-id="bacd4-103">**[データベースのバックアップ タスク]** ダイアログ ボックスを使用すると、バックアップ タスクをメンテナンス プランに追加できます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-103">Use the **Back Up Database Task** dialog to add a backup task to the maintenance plan.</span></span> <span data-ttu-id="bacd4-104">システムまたはハードウェアのトラブル (またはユーザー エラー) が原因でデータがなんらかの損傷を受けた場合、データの回復にはバックアップ コピーからの復元が必要になるため、データベースのバックアップは定期的に実行することが重要です。</span><span class="sxs-lookup"><span data-stu-id="bacd4-104">Backing up the database is important in case of system or hardware failure (or user errors) that cause the database to be damaged in some way, thus requiring a backed-up copy to be restored.</span></span> <span data-ttu-id="bacd4-105">このタスクを使用すると、ファイル、ファイル グループ、トランザクション ログの完全バックアップと差分バックアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-105">This task allows you to perform full, differential, files and filegroups, and transaction log backups.</span></span>  
  
 <span data-ttu-id="bacd4-106">**データベースのバックアップ タスクを作成するには**</span><span class="sxs-lookup"><span data-stu-id="bacd4-106">**To create a backup database task**</span></span>  
  
-   [<span data-ttu-id="bacd4-107">メンテナンス プランの作成</span><span class="sxs-lookup"><span data-stu-id="bacd4-107">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)  
  
## <a name="options"></a><span data-ttu-id="bacd4-108">Options</span><span class="sxs-lookup"><span data-stu-id="bacd4-108">Options</span></span>  
 <span data-ttu-id="bacd4-109">**接続**</span><span class="sxs-lookup"><span data-stu-id="bacd4-109">**Connection**</span></span>  
 <span data-ttu-id="bacd4-110">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-110">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="bacd4-111">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-111">**New**</span></span>  
 <span data-ttu-id="bacd4-112">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-112">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="bacd4-113">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-113">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="bacd4-114">**データベース**</span><span class="sxs-lookup"><span data-stu-id="bacd4-114">**Databases**</span></span>  
 <span data-ttu-id="bacd4-115">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-115">Specify the databases affected by this task.</span></span> <span data-ttu-id="bacd4-116">選択すると、ドロップ ダウン リストに次のオプションが表示されます: **[すべてのデータベース]** 、 **[すべてのシステム データベース]** **[すべてのユーザー データベース]** 、 **[These specific databases]\(これらの特定のデータベース\)** 。</span><span class="sxs-lookup"><span data-stu-id="bacd4-116">When selected, the drop down list provides the following options: **All databases**, **All system databases**, **All user databases**, **These specific databases**.</span></span>  
  
 <span data-ttu-id="bacd4-117">**[すべてのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-117">**All databases**</span></span>  
 <span data-ttu-id="bacd4-118">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-118">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="bacd4-119">**[すべてのシステム データベース] (master、msdb、model)**</span><span class="sxs-lookup"><span data-stu-id="bacd4-119">**All system databases (master, msdb, model)**</span></span>  
 <span data-ttu-id="bacd4-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各システム データベースを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-120">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span> <span data-ttu-id="bacd4-121">ユーザーが作成したデータベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="bacd4-121">No maintenance tasks are run against user-created databases.</span></span>  
  
 <span data-ttu-id="bacd4-122">**[すべてのユーザー データベース] \(master、model、msdb、tempdb は対象外)**</span><span class="sxs-lookup"><span data-stu-id="bacd4-122">**All user databases (excluding master, model, msdb, tempdb)**</span></span>  
 <span data-ttu-id="bacd4-123">ユーザーが作成したすべてのデータベースを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-123">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="bacd4-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="bacd4-124">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
 <span data-ttu-id="bacd4-125">**[これらのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-125">**These databases**</span></span>  
 <span data-ttu-id="bacd4-126">選択されたデータベースだけを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-126">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="bacd4-127">このオプションをオンにする場合は、少なくとも 1 つのデータベースが一覧内で選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bacd4-127">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="bacd4-128">**バックアップの種類**</span><span class="sxs-lookup"><span data-stu-id="bacd4-128">**Backup type**</span></span>  
 <span data-ttu-id="bacd4-129">実行するバックアップの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-129">Shows the type of backup to be performed.</span></span>  
  
 <span data-ttu-id="bacd4-130">**[バックアップ コンポーネント]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-130">**Backup component**</span></span>  
 <span data-ttu-id="bacd4-131">データベース全体をバックアップするには、 **[データベース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-131">Select **Database** to back up the entire database.</span></span> <span data-ttu-id="bacd4-132">データベースの一部だけをバックアップするには、 **[ファイルとファイル グループ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-132">Select **File and filegroups** to back up only a portion of the database.</span></span> <span data-ttu-id="bacd4-133">後者のオプションを選択した場合は、ファイル名またはファイル グループ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-133">If selected, provide the file or filegroup name.</span></span> <span data-ttu-id="bacd4-134">**[データベース]** ボックスで複数のデータベースを選択した場合、 **[バックアップ コンポーネント]** には **[データベース]** のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-134">When multiple databases are selected in the **Databases** box, only specify **Databases** for the **Backup components**.</span></span> <span data-ttu-id="bacd4-135">ファイルまたはファイル グループのバックアップを実行するには、データベースごとにタスクを作成します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-135">To perform file or filegroup backups, create a task for each database.</span></span>  
  
 <span data-ttu-id="bacd4-136">**[バックアップ セットの有効期限]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-136">**Backup set will expire**</span></span>  
 <span data-ttu-id="bacd4-137">バックアップ セットを別のバックアップ セットでいつ上書きできるようになるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-137">Specify when the backup set can be overwritten by another backup set.</span></span>  
  
 <span data-ttu-id="bacd4-138">**[バックアップ先]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-138">**Back up to**</span></span>  
 <span data-ttu-id="bacd4-139">データベースをファイルまたはテープにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="bacd4-139">Back up the database to a file or to tape.</span></span> <span data-ttu-id="bacd4-140">データベースを格納しているコンピューターに接続したテープ デバイスのみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-140">Only tape devices attached to the computer containing the database are available.</span></span>  
  
 <span data-ttu-id="bacd4-141">**[1 つ以上のファイルにデータベースをバックアップする]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-141">**Back up databases across one or more files**</span></span>  
 <span data-ttu-id="bacd4-142">**[追加]** をクリックして **[バックアップ先の選択]** ダイアログ ボックスを開き、1 つまたは複数のディスクの場所またはテープ デバイスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-142">Click **Add** to open the **Select Backup Destination** dialog box, and provide one or more a disk location, or tape device.</span></span>  
  
 <span data-ttu-id="bacd4-143">**[バックアップ ファイルが存在する場合に行う操作]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-143">**If backup files exist**</span></span>  
 <span data-ttu-id="bacd4-144">このバックアップをファイルの末尾に追加する場合は、 **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-144">Select **Append** to add this backup to the end of the file.</span></span> <span data-ttu-id="bacd4-145">ファイル内にある古いバックアップをすべて削除し、今回の新しいバックアップに置き換える場合は、 **[上書き]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-145">Select **Overwrite**, to remove any old backup in the file and replace them with this new backup.</span></span>  
  
 <span data-ttu-id="bacd4-146">**[すべてのデータベースにバックアップ ファイルを作成する]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-146">**Create a backup file for every database**</span></span>  
 <span data-ttu-id="bacd4-147">[フォルダー] ボックスで指定された場所にバックアップ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-147">Create a backup file in the location specified in the folder box.</span></span> <span data-ttu-id="bacd4-148">選択されたデータベースごとに 1 つのファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-148">One file will be created for each database selected.</span></span>  
  
 <span data-ttu-id="bacd4-149">**[データベースごとにサブディレクトリを作成する]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-149">**Create a sub-directory for each database**</span></span>  
 <span data-ttu-id="bacd4-150">各データベースをサブフォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-150">Select to place each database in a subfolder.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bacd4-151">メンテナンス プランによってサブディレクトリが作成される場合もありますが、メンテナンス タスクはサブディレクトリを削除できません。</span><span class="sxs-lookup"><span data-stu-id="bacd4-151">Although maintenance plans can create subdirectories, maintenance tasks cannot delete subdirectories.</span></span> <span data-ttu-id="bacd4-152">この機能によって、メンテナンス クリーンアップ タスクを使ってファイルを削除するなど、悪意のある攻撃を受ける危険性を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-152">This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bacd4-153">サブディレクトリには、親ディレクトリから権限が継承されます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-153">The subdirectory inherits permissions from the parent directory.</span></span> <span data-ttu-id="bacd4-154">不正アクセスを防ぐには、権限を制限してください。</span><span class="sxs-lookup"><span data-stu-id="bacd4-154">Restrict permissions to avoid unauthorized access.</span></span>  
  
 <span data-ttu-id="bacd4-155">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="bacd4-155">**Folder**</span></span>  
 <span data-ttu-id="bacd4-156">自動的に作成されたデータベース ファイルを格納するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-156">Specify the folder to contain the automatically created database files.</span></span>  
  
 <span data-ttu-id="bacd4-157">**[バックアップ ファイルの拡張子]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-157">**Backup file extension**</span></span>  
 <span data-ttu-id="bacd4-158">バックアップ ファイルに使用する拡張子を指定します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-158">Specify the extension to use for the backup files.</span></span> <span data-ttu-id="bacd4-159">既定値は **.bak**です。</span><span class="sxs-lookup"><span data-stu-id="bacd4-159">The default is **.bak**.</span></span>  
  
 <span data-ttu-id="bacd4-160">**[バックアップの整合性を検証する]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-160">**Verify backup integrity**</span></span>  
 <span data-ttu-id="bacd4-161">バックアップ セットが完全で、すべてのボリュームが読み取り可能であることを検証します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-161">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
 <span data-ttu-id="bacd4-162">**[ログの末尾をバックアップし、データベースを復元中の状態にしておく]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-162">**Back up the tail of the log, and leave the database in the restoring state**</span></span>  
 <span data-ttu-id="bacd4-163">データベースを復元する前に、最後のステップとしてログのバックアップを実行します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-163">Perform a log backup as the last step before restoring a database.</span></span> <span data-ttu-id="bacd4-164">詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bacd4-164">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="bacd4-165">**[バックアップの圧縮の設定]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-165">**Set backup compression**</span></span>  
 <span data-ttu-id="bacd4-166">[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (またはそれ以降のバージョン) で、 [バックアップの圧縮](../backup-restore/backup-compression-sql-server.md) の値を次の中から 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-166">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or a later version), select one the following [backup compression](../backup-restore/backup-compression-sql-server.md) values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bacd4-167">**[既定のサーバー設定を使用する]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-167">**Use the default server setting**</span></span>|<span data-ttu-id="bacd4-168">オンにすると、サーバー レベルの既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-168">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="bacd4-169">この既定値は、 **backup compression default** サーバー構成オプションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-169">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="bacd4-170">このオプションの現在の設定を表示する方法については、「 [backup compression default サーバー構成オプションの表示または構成](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bacd4-170">For information about how to view the current setting of this option,  see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="bacd4-171">**[バックアップを圧縮する]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-171">**Compress backup**</span></span>|<span data-ttu-id="bacd4-172">オンにすると、サーバー レベルの既定値に関係なく、バックアップが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-172">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="bacd4-173">**\*\* 重要 \*\*** 既定の設定では、圧縮によって CPU 使用率が著しく増加し、圧縮処理によって CPU がさらに消費されるために、同時に実行される操作が悪影響を受ける場合があります。</span><span class="sxs-lookup"><span data-stu-id="bacd4-173">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="bacd4-174">このため、 [リソース ガバナー](../resource-governor/resource-governor.md)によって CPU 使用率が制限されるセッションでは、優先度の低い圧縮バックアップを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-174">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="bacd4-175">詳細については、「 [リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bacd4-175">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="bacd4-176">**[バックアップを圧縮しない]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-176">**Do not compress backup**</span></span>|<span data-ttu-id="bacd4-177">オンにすると、サーバー レベルの既定値に関係なく、圧縮されていないバックアップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bacd4-177">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
 <span data-ttu-id="bacd4-178">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-178">**View T-SQL**</span></span>  
 <span data-ttu-id="bacd4-179">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-179">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bacd4-180">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bacd4-180">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="bacd4-181">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="bacd4-181">New Connection Dialog Box</span></span>  
 <span data-ttu-id="bacd4-182">**接続名**</span><span class="sxs-lookup"><span data-stu-id="bacd4-182">**Connection name**</span></span>  
 <span data-ttu-id="bacd4-183">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-183">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="bacd4-184">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-184">**Select or enter a server name**</span></span>  
 <span data-ttu-id="bacd4-185">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-185">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="bacd4-186">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-186">**Refresh**</span></span>  
 <span data-ttu-id="bacd4-187">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-187">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="bacd4-188">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-188">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="bacd4-189">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-189">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="bacd4-190">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-190">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="bacd4-191">Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-191">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="bacd4-192">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="bacd4-192">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="bacd4-193">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-193">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="bacd4-194">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="bacd4-194">This option is not available.</span></span>  
  
 <span data-ttu-id="bacd4-195">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="bacd4-195">**User name**</span></span>  
 <span data-ttu-id="bacd4-196">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-196">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="bacd4-197">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="bacd4-197">This option is not available.</span></span>  
  
 <span data-ttu-id="bacd4-198">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="bacd4-198">**Password**</span></span>  
 <span data-ttu-id="bacd4-199">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="bacd4-199">Provide a password to use when authenticating.</span></span> <span data-ttu-id="bacd4-200">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="bacd4-200">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bacd4-201">参照</span><span class="sxs-lookup"><span data-stu-id="bacd4-201">See Also</span></span>  
 [<span data-ttu-id="bacd4-202">BACKUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bacd4-202">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  
  
