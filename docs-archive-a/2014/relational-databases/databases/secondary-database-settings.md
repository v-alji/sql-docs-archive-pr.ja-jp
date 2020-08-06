---
title: '[セカンダリ データベースの設定] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.dest.f1
ms.assetid: f992ffc9-ee42-43fe-acec-512032f0ded1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 265d6beda830e2090392918ae14d10c8b7752d02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640046"
---
# <a name="secondary-database-settings"></a><span data-ttu-id="9ff7e-102">[セカンダリ データベースの設定]</span><span class="sxs-lookup"><span data-stu-id="9ff7e-102">Secondary Database Settings</span></span>
  <span data-ttu-id="9ff7e-103">このダイアログ ボックスを使用すると、ログ配布構成におけるセカンダリ データベースのプロパティを構成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-103">Use this dialog box to configure and to modify the properties of a secondary database in the log shipping configuration.</span></span>  
  
 <span data-ttu-id="9ff7e-104">ログ配布の概念については、「 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9ff7e-105">オプション</span><span class="sxs-lookup"><span data-stu-id="9ff7e-105">Options</span></span>  
 <span data-ttu-id="9ff7e-106">**[セカンダリ サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-106">**Secondary server instance**</span></span>  
 <span data-ttu-id="9ff7e-107">ログ配布構成において、現在、セカンダリ サーバーとして構成されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-107">Displays the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] currently configured to be a secondary server in the log shipping configuration.</span></span>  
  
 <span data-ttu-id="9ff7e-108">**[セカンダリ データベース]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-108">**Secondary database**</span></span>  
 <span data-ttu-id="9ff7e-109">ログ配布構成のセカンダリ データベースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-109">Displays the name of the secondary database for the log shipping configuration.</span></span> <span data-ttu-id="9ff7e-110">新しいセカンダリ データベースをログ配布構成に追加する場合は、一覧からデータベースを選択するか、ボックスに新しいデータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-110">When adding a new secondary database to a log shipping configuration, you can choose a database from the list or type the name of a new of the database into the box.</span></span> <span data-ttu-id="9ff7e-111">新しいデータベースの名前を入力する場合は、セカンダリ データベースにプライマリ データベースの完全なデータベース バックアップを復元するオプションを **[初期化]** タブで選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-111">If you enter the name of a new database, you must select an option on the **Initialization** tab that restores a full database backup of the primary database into the secondary database.</span></span> <span data-ttu-id="9ff7e-112">新しいデータベースは復元操作の一部として作成されます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-112">The new database is created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="9ff7e-113">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-113">**Connect**</span></span>  
 <span data-ttu-id="9ff7e-114">ログ配布構成において、セカンダリ サーバーとして使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-114">Connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for use as a secondary server in the log shipping configuration.</span></span> <span data-ttu-id="9ff7e-115">接続に使用するアカウントは、セカンダリ サーバーのインスタンスの sysadmin 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-115">The account used to connect must be a member of the sysadmin fixed server role on the secondary server instance.</span></span>  
  
 <span data-ttu-id="9ff7e-116">**[初期化] タブ**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-116">**Initialize tab**</span></span>  
 <span data-ttu-id="9ff7e-117">次のようなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-117">The options are as follows:</span></span>  
  
 <span data-ttu-id="9ff7e-118">**[はい、プライマリ データベースの完全バックアップを生成して、セカンダリ データベースに復元します]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-118">**Yes, generate a full backup of the primary database and restore it to the secondary database**</span></span>  
 <span data-ttu-id="9ff7e-119">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、プライマリ データベースをバックアップし、それをセカンダリ サーバーに復元することで、セカンダリ データベースを構成します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-119">Have [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] configure your secondary database by backing up the primary database and restoring it on the secondary server.</span></span> <span data-ttu-id="9ff7e-120">**[セカンダリ データベース]** ボックスに新しいデータベースの名前を入力した場合、データベースは復元操作の一部として作成されます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-120">If you entered a new database name in the **Secondary database** box, the database will be created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="9ff7e-121">**[復元オプション]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-121">**Restore Options**</span></span>  
 <span data-ttu-id="9ff7e-122">セカンダリ データベースのデータ ファイルおよびログ ファイルをセカンダリ サーバー上の既定以外の場所に復元する場合は、これをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-122">Click if you want to restore the data and log files for the secondary database into nondefault locations on the secondary server.</span></span>  
  
 <span data-ttu-id="9ff7e-123">このボタンをクリックすると、 **[復元オプション]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-123">This button opens the **Restore Options** dialog box.</span></span> <span data-ttu-id="9ff7e-124">このダイアログ ボックスで、セカンダリ データベースおよびそのログを保存する既定以外のフォルダーのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-124">There, you can specify paths to nondefault folders where you want the secondary database and its log to reside.</span></span> <span data-ttu-id="9ff7e-125">どちらかのフォルダーを指定した場合は、もう一方のフォルダーも指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-125">If you specify either folder, you must specify both.</span></span>  
  
 <span data-ttu-id="9ff7e-126">パスでは、セカンダリ サーバーに対してローカルなドライブを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-126">The paths must refer to drives that are local to the secondary server.</span></span> <span data-ttu-id="9ff7e-127">また、パスは、ローカル ドライブ名とコロンで始まっている必要があります (たとえば、 `C:`)。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-127">Also, the paths must begin with a local drive letter and colon (for example, `C:`).</span></span> <span data-ttu-id="9ff7e-128">マップされたドライブ名およびネットワーク パスは無効です。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-128">Mapped drive letters or network paths are invalid.</span></span>  
  
 <span data-ttu-id="9ff7e-129">**[復元オプション]** ボタンをクリックした後で既定のフォルダーを使用することにした場合は、 **[復元オプション]** ダイアログ ボックスを取り消すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-129">If you click the **Restore Options** button and then decide that you want to use the default folders, we recommend that you cancel the **Restore Options** dialog box.</span></span> <span data-ttu-id="9ff7e-130">既定以外の場所を既に指定した後で既定の場所を使用することにした場合は、 **[復元オプション]** をもう一度クリックし、テキスト ボックスを消去し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-130">If you have already specified nondefault locations and now want to use the default locations instead, click **Restore Options** again, clear the text boxes, and click OK.</span></span>  
  
 <span data-ttu-id="9ff7e-131">**[はい、プライマリ データベースの既存のバックアップをセカンダリ データベースに復元します]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-131">**Yes, restore an existing backup of the primary database to the secondary database**</span></span>  
 <span data-ttu-id="9ff7e-132">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で、プライマリ データベースの既存のバックアップを使用して、セカンダリ データベースを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-132">Have [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] use an existing backup of your primary database to initialize the secondary database.</span></span> <span data-ttu-id="9ff7e-133">対象のバックアップの場所を **[バックアップ ファイル]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-133">Type the location of that backup in the **Backup file** box.</span></span> <span data-ttu-id="9ff7e-134">[セカンダリ データベース] ボックスに新しいデータベースの名前を入力した場合、データベースは復元操作の一部として作成されます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-134">If you entered a new database name in the Secondary database box, the database will be created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="9ff7e-135">**[バックアップ ファイル]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-135">**Backup file**</span></span>  
 <span data-ttu-id="9ff7e-136">**[はい、プライマリ データベースの既存のバックアップをセカンダリ データベースに復元します]** を選択した場合は、セカンダリ データベースを初期化するために使用する、データベースの完全バックアップのパスとファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-136">Type the path and filename of the full database backup you want to use to initialize the secondary database if you chose the **Yes, restore and existing backup of the primary database to the secondary database option**.</span></span>  
  
 <span data-ttu-id="9ff7e-137">**[復元オプション]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-137">**Restore Options**</span></span>  
 <span data-ttu-id="9ff7e-138">このトピックで既に説明したこのボタンに関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-138">See the description of this button earlier in this topic.</span></span>  
  
 <span data-ttu-id="9ff7e-139">**[いいえ、セカンダリ データベースは初期化されています]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-139">**No, the secondary database is initialized**</span></span>  
 <span data-ttu-id="9ff7e-140">セカンダリ データベースが既に初期化されていて、プライマリ データベースからトランザクション ログ バックアップを受け入れる準備が整っていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-140">Specify that the secondary database is already initialized and ready to accept transaction log backups from the primary database.</span></span> <span data-ttu-id="9ff7e-141">**[セカンダリ データベース]** ボックスに新しいデータベース名を入力した場合は、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-141">This option is not available if you typed a new database name in the **Secondary database** box.</span></span>  
  
 <span data-ttu-id="9ff7e-142">**[ファイルのコピー] タブ**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-142">**Copy Files tab**</span></span>  
 <span data-ttu-id="9ff7e-143">次のようなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-143">The options are as follows:</span></span>  
  
 <span data-ttu-id="9ff7e-144">**[ファイルのコピー先フォルダー: (通常、このフォルダーはセカンダリ サーバーにあります)]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-144">**Destination folder for copied files**</span></span>  
 <span data-ttu-id="9ff7e-145">セカンダリ データベースに復元するために、トランザクション ログ バックアップのコピー先のパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-145">Type the path to which transaction log backups should be copied for restoration to the secondary database.</span></span> <span data-ttu-id="9ff7e-146">通常は、セカンダリ サーバー上のフォルダーへのローカル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-146">This is usually a local path to a folder located on the secondary server.</span></span> <span data-ttu-id="9ff7e-147">フォルダーが別のサーバー上にある場合は、フォルダーへの UNC パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-147">If the folder is located on another server, however, you must specify a UNC path to the folder.</span></span> <span data-ttu-id="9ff7e-148">セカンダリ サーバー インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントには、このフォルダーに対する読み取り権限を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-148">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the secondary server instance must have Read permissions on this folder.</span></span> <span data-ttu-id="9ff7e-149">さらに、コピー ジョブおよび復元ジョブをセカンダリ サーバー インスタンスで実行するプロキシ アカウントに対して、このネットワーク共有に対する読み取り/書き込み権限を許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-149">You must also grant read and write permissions on this network share to the proxy accounts under which the copy and restore jobs will run at the secondary server instances.</span></span> <span data-ttu-id="9ff7e-150">既定では、セカンダリ サーバー インスタンスの SQL Server エージェント サービス アカウントが使用されますが、sysadmin はジョブに他のプロキシ アカウントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-150">By default, this is the SQL Server Agent service account of the secondary server instance, but a sysadmin can choose other proxy accounts for the jobs.</span></span>  
  
 <span data-ttu-id="9ff7e-151">**[次の期間経過したコピー済みファイルを削除する]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-151">**Delete copied files after**</span></span>  
 <span data-ttu-id="9ff7e-152">コピーされたトランザクション ログ バックアップ ファイルを削除する前に、コピー先フォルダーに保持する期間を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-152">Choose the length of time you want the copied transaction log backup files to remain in the destination folder before being deleted.</span></span>  
  
 <span data-ttu-id="9ff7e-153">**ジョブ名**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-153">**Job name**</span></span>  
 <span data-ttu-id="9ff7e-154">トランザクション ログ バックアップ ファイルをプライマリ サーバーからセカンダリ サーバーにコピーするときに使用する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-154">Displays the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job used to copy transaction log backup files from the primary server to the secondary server.</span></span> <span data-ttu-id="9ff7e-155">このジョブを作成しているときは、ボックスに入力することで名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-155">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="9ff7e-156">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-156">**Schedule**</span></span>  
 <span data-ttu-id="9ff7e-157">トランザクション ログ バックアップを、プライマリ サーバーからセカンダリ サーバーにコピーする、SQL Server エージェントのコピー ジョブの現在のスケジュールを表示します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-157">Displays the current schedule for the SQL Server Agent copy job to copy transaction log backups from the primary server to the secondary server.</span></span> <span data-ttu-id="9ff7e-158">**[スケジュール]** をクリックすると、このスケジュールを変更できます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-158">You can modify this schedule by clicking **Schedule...**.</span></span>  
  
 <span data-ttu-id="9ff7e-159">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-159">**Schedule...**</span></span>  
 <span data-ttu-id="9ff7e-160">トランザクション ログ バックアップを、プライマリ サーバーからセカンダリ サーバーにコピーする、SQL Server エージェント ジョブのパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-160">Modify the parameters of the SQL Server Agent job that copies transaction log backups from the primary server to the secondary server.</span></span>  
  
 <span data-ttu-id="9ff7e-161">**[このジョブを無効にする]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-161">**Disable this job**</span></span>  
 <span data-ttu-id="9ff7e-162">SQL Server エージェントのコピー ジョブを中断します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-162">Suspend the SQL Server Agent copy job.</span></span>  
  
 <span data-ttu-id="9ff7e-163">**[トランザクション ログの復元] タブ**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-163">**Restore Transaction Log tab**</span></span>  
 <span data-ttu-id="9ff7e-164">次のようなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-164">The options are as follows:</span></span>  
  
 <span data-ttu-id="9ff7e-165">**[バックアップの復元時に、データベースのユーザーを切断する]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-165">**Disconnect users in the database when restoring backups**</span></span>  
 <span data-ttu-id="9ff7e-166">トランザクション ログのバックアップの復元時にセカンダリ データベースから自動的にユーザーを切断します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-166">Automatically disconnect users from the secondary database while transaction log backups are being restored.</span></span>  
  
 <span data-ttu-id="9ff7e-167">**[復旧モードなし]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-167">**No recovery mode**</span></span>  
 <span data-ttu-id="9ff7e-168">セカンダリ データベースを NORECOVERY モードで保持します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-168">Leave the secondary database in NORECOVERY mode.</span></span>  
  
 <span data-ttu-id="9ff7e-169">**[スタンバイ モード]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-169">**Standby mode**</span></span>  
 <span data-ttu-id="9ff7e-170">セカンダリ データベースを STANDBY モードで保持します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-170">Leave the secondary database in STANDBY mode.</span></span> <span data-ttu-id="9ff7e-171">このモードでは、データベースに対して読み取り専用の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-171">This mode will allow read-only operations to be performed on the database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9ff7e-172">既存のセカンダリ データベースの復旧モードを、たとえば、 **[復旧モードなし]** から **[スタンバイ モード]** に変更した場合、この変更は、次のログのバックアップがデータベースに復元されるまで有効になりません。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-172">If you change the recovery mode of an existing secondary database, for example, from **No recovery mode** to **Standby mode**, the change takes effect only after the next log backup is restored to the database.</span></span>  
  
 <span data-ttu-id="9ff7e-173">**[バックアップの復元を最低限次の期間遅延する]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-173">**Delay restoring backups at least**</span></span>  
 <span data-ttu-id="9ff7e-174">トランザクション ログ バックアップがセカンダリ データベースに復元されるまでの遅延を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-174">Choose the delay before transaction log backups are restored to the secondary database, if any.</span></span>  
  
 <span data-ttu-id="9ff7e-175">**[復元が次の期間内に行われない場合は警告する]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-175">**Alert if no restore occurs within**</span></span>  
 <span data-ttu-id="9ff7e-176">トランザクション ログの復元処理が発生しなかった場合に、ログ配布の警告を発生させる前に待機する期間を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-176">Choose the amount of time you want log shipping to wait before raising an alert that no transaction log restores have occurred.</span></span>  
  
 <span data-ttu-id="9ff7e-177">**ジョブ名**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-177">**Job name**</span></span>  
 <span data-ttu-id="9ff7e-178">トランザクション ログ バックアップを、セカンダリ データベースに復元するために使用する SQL Server エージェント ジョブの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-178">Displays the name of the SQL Server Agent job used to restore transaction log backups to the secondary database.</span></span> <span data-ttu-id="9ff7e-179">このジョブを作成しているときは、ボックスに入力することで名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-179">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="9ff7e-180">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-180">**Schedule**</span></span>  
 <span data-ttu-id="9ff7e-181">トランザクション ログ バックアップを、セカンダリ データベースに復元するために使用する SQL Server エージェント ジョブの現在のスケジュールを表示します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-181">Displays the current schedule for the SQL Server Agent job used for restoring transaction log backups to the secondary database.</span></span> <span data-ttu-id="9ff7e-182">**[スケジュール]** をクリックすると、このオプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-182">You can modify this option by clicking **Schedule...**.</span></span>  
  
 <span data-ttu-id="9ff7e-183">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-183">**Schedule...**</span></span>  
 <span data-ttu-id="9ff7e-184">SQL Server エージェントの復元ジョブに関連するパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-184">Modify the parameters associate with the SQL Server Agent restore job.</span></span>  
  
 <span data-ttu-id="9ff7e-185">**[このジョブを無効にする]**</span><span class="sxs-lookup"><span data-stu-id="9ff7e-185">**Disable this job**</span></span>  
 <span data-ttu-id="9ff7e-186">セカンダリ データベースへの復元操作を中断します。</span><span class="sxs-lookup"><span data-stu-id="9ff7e-186">Suspend restore operations to the secondary database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff7e-187">参照</span><span class="sxs-lookup"><span data-stu-id="9ff7e-187">See Also</span></span>  
 <span data-ttu-id="9ff7e-188">[SQL Server データベースのバックアップと復元](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="9ff7e-188">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="9ff7e-189">ログ配布について &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9ff7e-189">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
