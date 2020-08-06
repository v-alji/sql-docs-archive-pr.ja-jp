---
title: ログ配布の構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], enabling
- log shipping [SQL Server], configuring
ms.assetid: c42aa04a-4945-4417-b4c7-50589d727e9c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269b0ae2980435e507128cc87606f7eb702c2b7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713426"
---
# <a name="configure-log-shipping-sql-server"></a><span data-ttu-id="f23cb-102">ログ配布の構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f23cb-102">Configure Log Shipping (SQL Server)</span></span>
  <span data-ttu-id="f23cb-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ログ配布を構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-103">This topic describes how to configure log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="f23cb-104">以降のバージョンでは、バックアップの圧縮がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f23cb-104">and later versions support backup compression.</span></span> <span data-ttu-id="f23cb-105">ログ配布構成の作成時に、ログ バックアップのバックアップ圧縮動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="f23cb-105">When creating a log shipping configuration, you can control the backup compression behavior of log backups.</span></span> <span data-ttu-id="f23cb-106">詳細については、「[バックアップの圧縮 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f23cb-106">For more information, see [Backup Compression &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="f23cb-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f23cb-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f23cb-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f23cb-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f23cb-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="f23cb-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="f23cb-110">Security</span><span class="sxs-lookup"><span data-stu-id="f23cb-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f23cb-111">**以下を使用してログ配布を構成するには:**</span><span class="sxs-lookup"><span data-stu-id="f23cb-111">**To configure log shipping, using:**</span></span>  
  
     [<span data-ttu-id="f23cb-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f23cb-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f23cb-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f23cb-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="f23cb-114">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f23cb-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f23cb-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="f23cb-115">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f23cb-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="f23cb-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="f23cb-117">プライマリ データベースでは、完全復旧モデルか一括ログ復旧モデルを使用する必要があります。単純復旧モデルにデータベースを切り替えると、ログ配布が機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="f23cb-117">The primary database must use the full or bulk-logged recovery model; switching the database to simple recovery will cause log shipping to stop functioning.</span></span>  
  
-   <span data-ttu-id="f23cb-118">ログ配布を構成する前に、セカンダリ サーバーからトランザクション ログ バックアップを使用できるようにするための共有を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f23cb-118">Before you configure log shipping, you must create a share to make the transaction log backups available to the secondary server.</span></span> <span data-ttu-id="f23cb-119">この共有は、トランザクション ログ バックアップを生成するディレクトリにします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-119">This is a share of the directory where the transaction log backups will be generated.</span></span> <span data-ttu-id="f23cb-120">たとえば、トランザクション ログをディレクトリ c:\data\tlogs\\にバックアップする場合は、このディレクトリを基に \\\\*primaryserver*\tlogs という共有を作成します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-120">For example, if you back up your transaction logs to the directory c:\data\tlogs\\, you could create the \\\\*primaryserver*\tlogs share of that directory.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f23cb-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f23cb-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f23cb-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="f23cb-122">Permissions</span></span>  
 <span data-ttu-id="f23cb-123">ログ配布ストアド プロシージャには、 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="f23cb-123">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f23cb-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f23cb-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-log-shipping"></a><span data-ttu-id="f23cb-125">ログ配布を構成するには</span><span class="sxs-lookup"><span data-stu-id="f23cb-125">To configure log shipping</span></span>  
  
1.  <span data-ttu-id="f23cb-126">ログ配布構成のプライマリ データベースとして使用するデータベースを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-126">Right click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f23cb-127">**[ページの選択]** の **[トランザクション ログの配布]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-127">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
3.  <span data-ttu-id="f23cb-128">**[ログ配布構成のプライマリ データベースとして有効にする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-128">Select the **Enable this as a primary database in a log shipping configuration** check box.</span></span>  
  
4.  <span data-ttu-id="f23cb-129">**[トランザクション ログのバックアップ]** で **[バックアップの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-129">Under **Transaction log backups**, click **Backup Settings**.</span></span>  
  
5.  <span data-ttu-id="f23cb-130">**[バックアップ フォルダーのネットワーク パスを指定する]** ボックスに、トランザクション ログ バックアップ フォルダー用に作成した共有へのネットワーク パスを入力します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-130">In the **Network path to the backup folder** box, type the network path to the share you created for the transaction log backup folder.</span></span>  
  
6.  <span data-ttu-id="f23cb-131">バックアップ フォルダーがプライマリ サーバー上にある場合は、 **[バックアップ フォルダーがプライマリ サーバーに存在する場合は、バックアップ フォルダーのローカル パスを入力 (例: c:\\backup)]** ボックスに、バックアップ フォルダーへのローカル パスを入力します</span><span class="sxs-lookup"><span data-stu-id="f23cb-131">If the backup folder is located on the primary server, type the local path to the backup folder in the **If the backup folder is located on the primary server, type a local path to the folder** box.</span></span> <span data-ttu-id="f23cb-132">(バックアップ フォルダーが、プライマリ サーバー上にない場合は、このボックスは空のままでかまいません)。</span><span class="sxs-lookup"><span data-stu-id="f23cb-132">(If the backup folder is not on the primary server, you can leave this box empty.)</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f23cb-133">プライマリ サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントがローカル システム アカウントで実行されている場合、バックアップ フォルダーはプライマリ サーバー上に作成し、このフォルダーへのローカル パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f23cb-133">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account on your primary server runs under the local system account, you must create your backup folder on the primary server and specify a local path to that folder.</span></span>  
  
7.  <span data-ttu-id="f23cb-134">**[次の期間を経過したファイルを削除する]** と **[バックアップが次の期間内に行われない場合は警告する]** の各パラメーターを構成します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-134">Configure the **Delete files older than** and **Alert if no backup occurs within** parameters.</span></span>  
  
8.  <span data-ttu-id="f23cb-135">**[バックアップ ジョブ]** の **[スケジュール]** ボックスに、バックアップ スケジュールの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f23cb-135">Note the backup schedule listed in the **Schedule** box under **Backup job**.</span></span> <span data-ttu-id="f23cb-136">スケジュールをカスタマイズする場合は、 **[スケジュール]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのスケジュールを必要に応じて調整します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-136">If you want to customize the schedule for your installation, then click **Schedule** and adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span>  
  
9. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="f23cb-137">では、 [バックアップの圧縮](../../relational-databases/backup-restore/backup-compression-sql-server.md)がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f23cb-137">supports [backup compression](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span> <span data-ttu-id="f23cb-138">ログ配布構成を作成する際には、次のオプションのいずれかを選択して、ログ バックアップのバックアップ圧縮動作を制御することができます: **既定のサーバー設定を使用する**、**バックアップを圧縮する**、**バックアップを圧縮しない**。</span><span class="sxs-lookup"><span data-stu-id="f23cb-138">When creating a log shipping configuration, you can control the backup compression behavior of log backups by choosing one of the following options: **Use the default server setting**, **Compress backup**, or **Do not compress backup**.</span></span> <span data-ttu-id="f23cb-139">詳細については、「 [Log Shipping Transaction Log Backup Settings](../../relational-databases/databases/log-shipping-transaction-log-backup-settings.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f23cb-139">For more information, see [Log Shipping Transaction Log Backup Settings](../../relational-databases/databases/log-shipping-transaction-log-backup-settings.md).</span></span>  
  
10. <span data-ttu-id="f23cb-140">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-140">Click **OK**.</span></span>  
  
11. <span data-ttu-id="f23cb-141">**[セカンダリ サーバー インスタンスとデータベース]** の **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-141">Under **Secondary server instances and databases**, click **Add**.</span></span>  
  
12. <span data-ttu-id="f23cb-142">**[接続]** をクリックし、セカンダリ サーバーとして使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-142">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your secondary server.</span></span>  
  
13. <span data-ttu-id="f23cb-143">**[セカンダリ データベース]** ボックスで、一覧からデータベースを選択するか、作成するデータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-143">In the **Secondary Database** box, choose a database from the list or type the name of the database you want to create.</span></span>  
  
14. <span data-ttu-id="f23cb-144">**[セカンダリ データベースの初期化]** タブで、セカンダリ データベースを初期化するためのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-144">On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f23cb-145">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] によりセカンダリ データベースをデータベース バックアップから初期化することを選択した場合、セカンダリ データベースのデータとログ ファイルは **master** データベースのデータとログ ファイルと同じ場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="f23cb-145">If you choose to have [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] initialize the secondary database from a database backup, the data and log files of the secondary database are placed in the same location as the data and log files of the **master** database.</span></span> <span data-ttu-id="f23cb-146">この場所は、多くの場合、プライマリ データベースのデータとログ ファイルの場所とは異なります。</span><span class="sxs-lookup"><span data-stu-id="f23cb-146">This location is likely to be different than the location of the data and log files of the primary database.</span></span>  
  
15. <span data-ttu-id="f23cb-147">**[ファイルのコピー]** タブの **[ファイルのコピー先フォルダー]** ボックスに、トランザクション ログ バックアップのコピー先となるフォルダーのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-147">On the **Copy Files** tab, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied.</span></span> <span data-ttu-id="f23cb-148">多くの場合、セカンダリ サーバー上のフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-148">This folder is often located on the secondary server.</span></span>  
  
16. <span data-ttu-id="f23cb-149">**[復元ジョブ]** の **[スケジュール]** ボックスにコピー スケジュールの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f23cb-149">Note the copy schedule listed in the **Schedule** box under **Copy job**.</span></span> <span data-ttu-id="f23cb-150">スケジュールをカスタマイズする場合、 **[スケジュール]** をクリックして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのスケジュールを必要に応じて調整します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-150">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="f23cb-151">このスケジュールはバックアップ スケジュールに近い設定にします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-151">This schedule should approximate the backup schedule.</span></span>  
  
17. <span data-ttu-id="f23cb-152">**[復元]** タブの **[バックアップ復元時のデータベース状態]** で、 **[復旧モードなし]** または **[スタンバイ モード]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-152">On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.</span></span>  
  
18. <span data-ttu-id="f23cb-153">**[スタンバイ モード]** を選択する場合は、復元操作の進行中にセカンダリ データベースからユーザーを切断するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-153">If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.</span></span>  
  
19. <span data-ttu-id="f23cb-154">セカンダリ サーバーの復元処理を遅延させる場合、 **[バックアップの復元を最低限次の期間遅延する]** で遅延時間を選択します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-154">If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.</span></span>  
  
20. <span data-ttu-id="f23cb-155">**[復元が次の期間内に行われない場合は警告する]** で警告のしきい値を選択します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-155">Choose an alert threshold under **Alert if no restore occurs within**.</span></span>  
  
21. <span data-ttu-id="f23cb-156">**[復元ジョブ]** の **[スケジュール]** ボックスに表示される復元スケジュールを確認します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-156">Note the restore schedule listed in the **Schedule** box under **Restore job**.</span></span> <span data-ttu-id="f23cb-157">スケジュールをカスタマイズする場合、 **[スケジュール]** をクリックして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのスケジュールを必要に応じて調整します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-157">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="f23cb-158">このスケジュールはバックアップ スケジュールに近い設定にします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-158">This schedule should approximate the backup schedule.</span></span>  
  
22. <span data-ttu-id="f23cb-159">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-159">Click **OK**.</span></span>  
  
23. <span data-ttu-id="f23cb-160">**[監視サーバー インスタンス]** の **[監視サーバー インスタンスを使用する]** チェック ボックスをオンにし、 **[設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-160">Under **Monitor server instance**, select the **Use a monitor server instance** check box, and then click **Settings**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f23cb-161">このログ配布構成を監視するには、ここで監視サーバーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f23cb-161">To monitor this log shipping configuration, you must add the monitor server now.</span></span> <span data-ttu-id="f23cb-162">監視サーバーを後で追加するには、このログ配布構成を削除して、代わりに監視サーバーを含む新しい構成を用意します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-162">To add the monitor server later, you would need to remove this log shipping configuration and then replace it with a new configuration that includes a monitor server.</span></span>  
  
24. <span data-ttu-id="f23cb-163">**[接続]** をクリックして、監視サーバーとして使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-163">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your monitor server.</span></span>  
  
25. <span data-ttu-id="f23cb-164">**[モニター接続]** で、バックアップ、コピー、復元の各ジョブで監視サーバーへの接続に使用する接続方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-164">Under **Monitor connections**, choose the connection method to be used by the backup, copy, and restore jobs to connect to the monitor server.</span></span>  
  
26. <span data-ttu-id="f23cb-165">**[履歴の保有期間]** で、ログ配布の履歴レコードを保持する期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-165">Under **History retention**, choose the length of time you want to retain a record of your log shipping history.</span></span>  
  
27. <span data-ttu-id="f23cb-166">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-166">Click **OK**.</span></span>  
  
28. <span data-ttu-id="f23cb-167">**[データベースのプロパティ]** ダイアログ ボックスで **[OK]** をクリックし、構成処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-167">On the **Database Properties** dialog box, click **OK** to begin the configuration process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f23cb-168">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f23cb-168">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-log-shipping"></a><span data-ttu-id="f23cb-169">ログ配布を構成するには</span><span class="sxs-lookup"><span data-stu-id="f23cb-169">To configure log shipping</span></span>  
  
1.  <span data-ttu-id="f23cb-170">プライマリ データベースの完全バックアップをセカンダリ サーバーに復元して、セカンダリ データベースを初期化します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-170">Initialize the secondary database by restoring a full backup of the primary database on the secondary server.</span></span>  
  
2.  <span data-ttu-id="f23cb-171">プライマリ サーバーで [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql) を実行して、プライマリ データベースを追加します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-171">On the primary server, execute [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql) to add a primary database.</span></span> <span data-ttu-id="f23cb-172">このストアド プロシージャからは、バックアップ ジョブ ID とプライマリ ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="f23cb-172">The stored procedure returns the backup job ID and primary ID.</span></span>  
  
3.  <span data-ttu-id="f23cb-173">プライマリ サーバーで [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) を実行して、バックアップ ジョブのスケジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-173">On the primary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to add a schedule for the backup job.</span></span>  
  
4.  <span data-ttu-id="f23cb-174">監視サーバーで [sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql) を実行して、警告ジョブを追加します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-174">On the monitor server, execute [sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql) to add the alert job.</span></span>  
  
5.  <span data-ttu-id="f23cb-175">プライマリ サーバーでバックアップ ジョブを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-175">On the primary server, enable the backup job.</span></span>  
  
6.  <span data-ttu-id="f23cb-176">セカンダリ サーバーで [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) を実行します。このとき、プライマリ サーバーとプライマリ データベースの詳細情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-176">On the secondary server, execute [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) supplying the details of the primary server and database.</span></span> <span data-ttu-id="f23cb-177">このストアド プロシージャからは、セカンダリ ID、コピー ジョブ ID、および復元ジョブ ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="f23cb-177">This stored procedure returns the secondary ID and the copy and restore job IDs.</span></span>  
  
7.  <span data-ttu-id="f23cb-178">セカンダリ サーバーで [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) を実行して、コピー ジョブと復元ジョブのスケジュールを設定します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-178">On the secondary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to set the schedule for the copy and restore jobs.</span></span>  
  
8.  <span data-ttu-id="f23cb-179">セカンダリ サーバーで [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) を実行して、セカンダリ データベースを追加します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-179">On the secondary server, execute [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) to add a secondary database.</span></span>  
  
9. <span data-ttu-id="f23cb-180">プライマリ サーバーで [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) を実行して、新しいセカンダリ データベースに関する必要な情報をプライマリ サーバーに追加します。</span><span class="sxs-lookup"><span data-stu-id="f23cb-180">On the primary server, execute [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) to add the required information about the new secondary database to the primary server.</span></span>  
  
10. <span data-ttu-id="f23cb-181">セカンダリ サーバーでコピー ジョブと復元ジョブを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f23cb-181">On the secondary server, enable the copy and restore jobs.</span></span> <span data-ttu-id="f23cb-182">詳細については、「 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f23cb-182">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f23cb-183">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f23cb-183">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f23cb-184">ログ配布を SQL Server 2014 &#40;Transact-sql&#41;にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="f23cb-184">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="f23cb-185">ログ配布構成へのセカンダリ データベースの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f23cb-185">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="f23cb-186">ログ配布構成からのセカンダリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f23cb-186">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="f23cb-187">ログ配布の削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f23cb-187">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="f23cb-188">ログ配布レポートの表示 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f23cb-188">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f23cb-189">ログ配布の監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f23cb-189">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="f23cb-190">ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f23cb-190">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="f23cb-191">参照</span><span class="sxs-lookup"><span data-stu-id="f23cb-191">See Also</span></span>  
 <span data-ttu-id="f23cb-192">[ログ配布について &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f23cb-192">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="f23cb-193">ログ配布テーブルとストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f23cb-193">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
