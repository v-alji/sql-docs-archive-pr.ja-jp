---
title: '[データベースのバックアップ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.general.f1
ms.assetid: 5c344dfd-1ad3-41cc-98cd-732973b4a162
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c315c827e1c8b206b2098009510bf6468bd7d74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645692"
---
# <a name="back-up-database-general-page"></a><span data-ttu-id="02aa3-102">[データベースのバックアップ] \([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="02aa3-102">Back Up Database (General Page)</span></span>
  <span data-ttu-id="02aa3-103">**[データベースのバックアップ]** ダイアログ ボックスの **[全般]** ページでは、データベースのバックアップ操作の設定を表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-103">Use the **General** page of the **Back Up Database** dialog box to view or modify settings for a database back up operation.</span></span>  
  
 <span data-ttu-id="02aa3-104">バックアップの基本的な概念については、「[バックアップの概要 &#40;SQL Server&#41;](backup-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02aa3-104">For more information about basic backup concepts, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02aa3-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してバックアップ タスクを指定する場合、 [!INCLUDE[tsql](../../includes/tsql-md.md)][[スクリプト]](/sql/t-sql/statements/backup-transact-sql) ボタンをクリックしてスクリプトの保存先を選択することにより、対応する **BACKUP** スクリプトを生成できます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-105">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
 <span data-ttu-id="02aa3-106">**SQL Server Management Studio を使用してバックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="02aa3-106">**To use SQL Server Management Studio to create a backup**</span></span>  
  
-   [<span data-ttu-id="02aa3-107">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02aa3-107">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="02aa3-108">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02aa3-108">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="02aa3-109">データベース メンテナンス プランを定義して、データベース バックアップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-109">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="02aa3-110">詳細については、 [オンライン ブックの「](../maintenance-plans/maintenance-plans.md) メンテナンス プラン [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02aa3-110">For more information, see [Database Maintenance Plans](../maintenance-plans/maintenance-plans.md) in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="02aa3-111">**部分バックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="02aa3-111">**To create a partial backup**</span></span>  
  
-   <span data-ttu-id="02aa3-112">部分バックアップを作成するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] の [BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントで PARTIAL オプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02aa3-112">For a partial backup, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="02aa3-113">Options</span><span class="sxs-lookup"><span data-stu-id="02aa3-113">Options</span></span>  
  
### <a name="source"></a><span data-ttu-id="02aa3-114">source</span><span class="sxs-lookup"><span data-stu-id="02aa3-114">Source</span></span>  
 <span data-ttu-id="02aa3-115">**[ソース]** パネルのオプションでは、データベースを特定し、バックアップ操作のバックアップの種類とコンポーネントを指定します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-115">The options of the **Source** panel identify the database and specify the backup type and component for the back up operation.</span></span>  
  
 <span data-ttu-id="02aa3-116">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-116">**Database**</span></span>  
 <span data-ttu-id="02aa3-117">バックアップするデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-117">Select the database to back up.</span></span>  
  
 <span data-ttu-id="02aa3-118">**復旧モデル**</span><span class="sxs-lookup"><span data-stu-id="02aa3-118">**Recovery model**</span></span>  
 <span data-ttu-id="02aa3-119">選択したデータベースで表示される復旧モデル (SIMPLE、FULL、または BULK_LOGGED) を表示します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-119">View the recovery model (SIMPLE, FULL, or BULK_LOGGED) displayed for the selected database.</span></span>  
  
 <span data-ttu-id="02aa3-120">**バックアップの種類**</span><span class="sxs-lookup"><span data-stu-id="02aa3-120">**Backup type**</span></span>  
 <span data-ttu-id="02aa3-121">指定したデータベースで実行するバックアップの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-121">Select the type of backup you want to perform on the specified database.</span></span>  
  
|<span data-ttu-id="02aa3-122">バックアップの種類</span><span class="sxs-lookup"><span data-stu-id="02aa3-122">Backup type</span></span>|<span data-ttu-id="02aa3-123">適用対象</span><span class="sxs-lookup"><span data-stu-id="02aa3-123">Available for</span></span>|<span data-ttu-id="02aa3-124">制限</span><span class="sxs-lookup"><span data-stu-id="02aa3-124">Restrictions</span></span>|  
|-----------------|-------------------|------------------|  
|<span data-ttu-id="02aa3-125">[完全]</span><span class="sxs-lookup"><span data-stu-id="02aa3-125">Full</span></span>|<span data-ttu-id="02aa3-126">データベース、ファイル、ファイル グループ</span><span class="sxs-lookup"><span data-stu-id="02aa3-126">Databases, files, and filegroups</span></span>|<span data-ttu-id="02aa3-127">**master** データベースでは、完全バックアップのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="02aa3-127">On the **master** database, only full backups are possible.</span></span><br /><br /> <span data-ttu-id="02aa3-128">SIMPLE (単純) 復旧モデルの場合、ファイルおよびファイル グループのバックアップは読み取り専用ファイル グループについてのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-128">Under the Simple Recovery Model, file and filegroup backups are available only for read-only filegroups.</span></span>|  
|<span data-ttu-id="02aa3-129">差分</span><span class="sxs-lookup"><span data-stu-id="02aa3-129">Differential</span></span>|<span data-ttu-id="02aa3-130">データベース、ファイル、ファイル グループ</span><span class="sxs-lookup"><span data-stu-id="02aa3-130">Databases, files, and filegroups</span></span>|<span data-ttu-id="02aa3-131">SIMPLE (単純) 復旧モデルの場合、ファイルおよびファイル グループのバックアップは読み取り専用ファイル グループについてのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-131">Under the Simple Recovery Model, file and filegroup backups are available only for read-only filegroups.</span></span>|  
|<span data-ttu-id="02aa3-132">トランザクション ログ</span><span class="sxs-lookup"><span data-stu-id="02aa3-132">Transaction Log</span></span>|<span data-ttu-id="02aa3-133">トランザクション ログ</span><span class="sxs-lookup"><span data-stu-id="02aa3-133">Transaction logs</span></span>|<span data-ttu-id="02aa3-134">トランザクション ログ バックアップは、単純復旧モデルでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="02aa3-134">Transaction log backups are not available for the Simple Recovery Model.</span></span>|  
  
 <span data-ttu-id="02aa3-135">**[バックアップのみコピーする]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-135">**Copy Only Backup**</span></span>  
 <span data-ttu-id="02aa3-136">コピーのみのバックアップを作成する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-136">Select to create a copy-only backup.</span></span> <span data-ttu-id="02aa3-137">*コピーのみのバックアップ*は、従来の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップのシーケンスから独立した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップです。</span><span class="sxs-lookup"><span data-stu-id="02aa3-137">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="02aa3-138">詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](copy-only-backups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02aa3-138">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02aa3-139">**[差分]** オプションが選択されている場合、コピーのみのバックアップは作成できません。</span><span class="sxs-lookup"><span data-stu-id="02aa3-139">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
 <span data-ttu-id="02aa3-140">**[バックアップ コンポーネント]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-140">**Backup component**</span></span>  
 <span data-ttu-id="02aa3-141">バックアップするデータベース コンポーネントを選択します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-141">Select the database component to be backed up.</span></span> <span data-ttu-id="02aa3-142">**[バックアップの種類]** ボックスの一覧で **[トランザクション ログ]** を選択した場合は、このオプションを設定できません。</span><span class="sxs-lookup"><span data-stu-id="02aa3-142">If **Transaction Log** is selected in the **Backup type** list, this option is not activated.</span></span>  
  
 <span data-ttu-id="02aa3-143">次のいずれかのオプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="02aa3-143">Select one of the following option buttons:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02aa3-144">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-144">**Database**</span></span>|<span data-ttu-id="02aa3-145">データベース全体がバックアップされるように指定します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-145">Specifies that the entire database be backed up.</span></span>|  
|<span data-ttu-id="02aa3-146">**[ファイルおよびファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-146">**Files and filegroups**</span></span>|<span data-ttu-id="02aa3-147">指定したファイルやファイル グループがバックアップされるように指定します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-147">Specifies that the specified files and/or filegroups be backed up.</span></span><br /><br /> <span data-ttu-id="02aa3-148">このオプションをクリックすると、 **[ファイルおよびファイル グループの選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-148">Selecting this option, opens the **Select Files and Filegroups** dialog box.</span></span> <span data-ttu-id="02aa3-149">バックアップするファイル グループまたはファイルを選択して **[OK]** をクリックすると、選択した項目が **[ファイルおよびファイル グループ]** ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-149">After you select the filegroups or files you want to back up and click **Ok**, your selections appear in the **Filegroups and files** box.</span></span>|  
  
### <a name="destination"></a><span data-ttu-id="02aa3-150">宛先</span><span class="sxs-lookup"><span data-stu-id="02aa3-150">Destination</span></span>  
 <span data-ttu-id="02aa3-151">**[バックアップ先]** パネルのオプションでは、バックアップ操作で使用するバックアップ デバイスの種類を指定して、既存の論理バックアップ デバイスまたは物理バックアップ デバイスを検索できます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-151">The options of the **Destination** panel allow for you to specify the type of backup device for the back up operation and find an existing logical or physical backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02aa3-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ デバイスの詳細については、「[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02aa3-152">For information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="02aa3-153">**[バックアップ先]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-153">**Back up to**</span></span>  
 <span data-ttu-id="02aa3-154">バックアップ先のメディアの種類を、次の中から 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-154">Select one of the following types of media to which to back up.</span></span> <span data-ttu-id="02aa3-155">選択したバックアップ先が、 **[バックアップ先]** 一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-155">The destinations you select appear in the **Back up to** list.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02aa3-156">**ディスク**</span><span class="sxs-lookup"><span data-stu-id="02aa3-156">**Disk**</span></span>|<span data-ttu-id="02aa3-157">ディスクにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="02aa3-157">Backs up to disk.</span></span> <span data-ttu-id="02aa3-158">データベース用に作成されたシステム ファイルやディスク ベースの論理バックアップ デバイスを指定する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="02aa3-158">This may be a system file or a disk-based logical backup device created for the database.</span></span> <span data-ttu-id="02aa3-159">現在選択されているディスクが、 **[バックアップ先]** 一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-159">The currently selected disks appear in the **Back up to** list.</span></span> <span data-ttu-id="02aa3-160">バックアップ操作には最大 64 台のディスク デバイスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-160">You can select up to 64 disk devices for your backup operation.</span></span>|  
|<span data-ttu-id="02aa3-161">**[テープ]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-161">**Tape**</span></span>|<span data-ttu-id="02aa3-162">テープにバックアップします。</span><span class="sxs-lookup"><span data-stu-id="02aa3-162">Backs up to tape.</span></span> <span data-ttu-id="02aa3-163">データベース用に作成されたローカル テープ ドライブやテープ ベースの論理バックアップ デバイスを指定する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="02aa3-163">This may be a local tape drive or a tape-based logical backup device created for the database.</span></span> <span data-ttu-id="02aa3-164">現在選択されているテープが、 **[バックアップ先]** リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-164">The currently selected tapes appear in the **Back up to** list.</span></span> <span data-ttu-id="02aa3-165">最大数は 64 です。</span><span class="sxs-lookup"><span data-stu-id="02aa3-165">The maximum number is 64.</span></span> <span data-ttu-id="02aa3-166">サーバーにテープ デバイスが接続されていない場合、このオプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="02aa3-166">If there are no tape devices attached to the server, this option is deactivated.</span></span> <span data-ttu-id="02aa3-167">選択したテープが **[バックアップ先]** 一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-167">The tapes you select are listed in the **Back up to** list.</span></span><br /><br /> <span data-ttu-id="02aa3-168">注:テープ バックアップ デバイスは、将来のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でサポートされなくなる予定です。</span><span class="sxs-lookup"><span data-stu-id="02aa3-168">Note: Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="02aa3-169">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="02aa3-169">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>|  
|<span data-ttu-id="02aa3-170">**URL**</span><span class="sxs-lookup"><span data-stu-id="02aa3-170">**URL**</span></span>|<span data-ttu-id="02aa3-171">Azure Blob storage にバックアップします。</span><span class="sxs-lookup"><span data-stu-id="02aa3-171">Backs up to Azure Blob storage.</span></span>|  
  
 <span data-ttu-id="02aa3-172">次に示すオプションの表示は、選択したバックアップ先の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="02aa3-172">The next set of options displayed depends on the type of destination selected.</span></span> <span data-ttu-id="02aa3-173">[ディスク] または [テープ] を選択すると、次のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-173">If you select Disk or Tape, the following options are displayed.</span></span>  
  
 <span data-ttu-id="02aa3-174">**追加**</span><span class="sxs-lookup"><span data-stu-id="02aa3-174">**Add**</span></span>  
 <span data-ttu-id="02aa3-175">ファイルまたはデバイスを **[バックアップ先]** 一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-175">Adds a file or device to the **Back up to** list.</span></span> <span data-ttu-id="02aa3-176">ローカル ディスクまたはリモート ディスクの最大 64 個のデバイスで同時にバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-176">You can back up to 64 devices simultaneously on a local disk or remote disk.</span></span> <span data-ttu-id="02aa3-177">リモート ディスクのファイルを指定するには、完全修飾の汎用名前付け規則 (UNC) 名を使用してください。</span><span class="sxs-lookup"><span data-stu-id="02aa3-177">To specify a file on a remote disk, use the fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="02aa3-178">詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02aa3-178">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="02aa3-179">**Remove**</span><span class="sxs-lookup"><span data-stu-id="02aa3-179">**Remove**</span></span>  
 <span data-ttu-id="02aa3-180">**[バックアップ先]** 一覧から、現在選択されているデバイスを削除します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-180">Removes one or more currently selected devices from the **Back up to** list.</span></span>  
  
 <span data-ttu-id="02aa3-181">**Contents**</span><span class="sxs-lookup"><span data-stu-id="02aa3-181">**Contents**</span></span>  
 <span data-ttu-id="02aa3-182">選択したデバイスのメディア コンテンツを表示します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-182">Displays the media contents for the selected device.</span></span>  
  
 <span data-ttu-id="02aa3-183">バックアップ先として [URL] を選択すると、次のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-183">If you select URL as the backup destination, the following options are displayed:</span></span>  
  
 <span data-ttu-id="02aa3-184">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-184">**File Name**</span></span>  
 <span data-ttu-id="02aa3-185">バックアップ ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-185">Specify the name of the backup file.</span></span>  
  
 <span data-ttu-id="02aa3-186">**SQL 資格情報**</span><span class="sxs-lookup"><span data-stu-id="02aa3-186">**SQL credential**</span></span>  
 <span data-ttu-id="02aa3-187">Azure Storage の認証に使用する SQL 資格情報を選択します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-187">Select a SQL Credential used to authenticate to  Azure Storage.</span></span> <span data-ttu-id="02aa3-188">使用できる既存の SQL 資格情報がない場合は、 **[作成]** ボタンをクリックして新しい SQL 資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-188">If you do not have an existing SQL Credential you can use, click the **Create** button to create a new SQL Credential.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="02aa3-189">**[作成]** をクリックすると開くダイアログでは、サブスクリプションの管理証明書または公開プロファイルが求められます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-189">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="02aa3-190">管理証明書または公開プロファイルにアクセスできない場合は、Transact-SQL または SQL Server Management Studio を使用してストレージ アカウント名とアクセス キーの情報を指定し、SQL 資格情報を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-190">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="02aa3-191">Transact-sql を使用して資格情報を作成する方法について[は、「](../security/authentication-access/create-a-credential.md#Credential) 」の「」のサンプルコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="02aa3-191">See the sample code in the in the [To create a credential](../security/authentication-access/create-a-credential.md#Credential) topic to create a credential using Transact-SQL.</span></span> <span data-ttu-id="02aa3-192">または SQL Server Management Studio を使用して、データベース エンジン インスタンスから、 **[セキュリティ]** を右クリックし、 **[新規作成]**、 **[資格情報]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="02aa3-192">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="02aa3-193">**[ID]** にストレージ アカウント名、 **[パスワード]** にアクセス キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="02aa3-193">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
 <span data-ttu-id="02aa3-194">**[Azure ストレージ コンテナー]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-194">**Azure storage container**</span></span>  
 <span data-ttu-id="02aa3-195">Azure ストレージ コンテナーの名前を指定します</span><span class="sxs-lookup"><span data-stu-id="02aa3-195">Specify the name of the Azure storage container</span></span>  
  
 <span data-ttu-id="02aa3-196">**[URL プレフィックス]**</span><span class="sxs-lookup"><span data-stu-id="02aa3-196">**URL prefix:**</span></span>  
 <span data-ttu-id="02aa3-197">これは、SQL 資格情報に格納されているストレージ アカウント情報と、指定した Azure ストレージ コンテナー名に基づいて自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="02aa3-197">This is automatically generated based on the storage account information stored in the SQL Credential, and Azure storage container name you specified.</span></span> <span data-ttu-id="02aa3-198">**\<storage account>.blob.core.windows.net** 以外の形式を使ったドメインを使用している場合を除き、このフィールドの情報は編集しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="02aa3-198">We recommend that you do not edit the information in this field unless you are using a domain that uses a format other than **\<storage account>.blob.core.windows.net**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02aa3-199">参照</span><span class="sxs-lookup"><span data-stu-id="02aa3-199">See Also</span></span>  
 <span data-ttu-id="02aa3-200">[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="02aa3-200">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="02aa3-201">[ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="02aa3-201">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="02aa3-202">[ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="02aa3-202">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 <span data-ttu-id="02aa3-203">[テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="02aa3-203">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="02aa3-204">復旧モデル &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02aa3-204">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
