---
title: ログ配布構成へのセカンダリ データベースの追加 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- adding secondary databases
- secondary databases [SQL Server], in log shipping
- secondary data files [SQL Server], adding
- log shipping [SQL Server], secondary databases
ms.assetid: b02eba13-f8e6-4684-b7e4-75ea038ea473
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 062df1b53ed74321ba0c75c9df763de79a4802bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641211"
---
# <a name="add-a-secondary-database-to-a-log-shipping-configuration-sql-server"></a><span data-ttu-id="4db4d-102">ログ配布構成へのセカンダリ データベースの追加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4db4d-102">Add a Secondary Database to a Log Shipping Configuration (SQL Server)</span></span>
  <span data-ttu-id="4db4d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、既存のログ配布構成にセカンダリ データベースを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-103">This topic describes how to add a secondary database to an existing log shipping configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4db4d-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4db4d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4db4d-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4db4d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4db4d-106">Security</span><span class="sxs-lookup"><span data-stu-id="4db4d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4db4d-107">**以下を使用してログ配布セカンダリ データベースを追加するには:**</span><span class="sxs-lookup"><span data-stu-id="4db4d-107">**To add a log shipping secondary database, using:**</span></span>  
  
     [<span data-ttu-id="4db4d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4db4d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4db4d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4db4d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="4db4d-110">関連タスク</span><span class="sxs-lookup"><span data-stu-id="4db4d-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4db4d-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="4db4d-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4db4d-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4db4d-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4db4d-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="4db4d-113">Permissions</span></span>  
 <span data-ttu-id="4db4d-114">ログ配布ストアド プロシージャには、 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="4db4d-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4db4d-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4db4d-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a><span data-ttu-id="4db4d-116">ログ配布セカンダリ データベースを追加するには</span><span class="sxs-lookup"><span data-stu-id="4db4d-116">To add a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="4db4d-117">ログ配布構成のプライマリ データベースとして使用するデータベースを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db4d-117">Right-click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="4db4d-118">**[ページの選択]** の **[トランザクション ログの配布]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db4d-118">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
3.  <span data-ttu-id="4db4d-119">**[セカンダリ サーバー インスタンスとデータベース]** の **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db4d-119">Under **Secondary server instances and databases**, click **Add**.</span></span>  
  
4.  <span data-ttu-id="4db4d-120">**[接続]** をクリックし、セカンダリ サーバーとして使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-120">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your secondary server.</span></span>  
  
5.  <span data-ttu-id="4db4d-121">**[セカンダリ データベース]** ボックスで、一覧からデータベースを選択するか、作成するデータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-121">In the **Secondary database** box, choose a database from the list or type the name of the database you want to create.</span></span>  
  
6.  <span data-ttu-id="4db4d-122">**[セカンダリ データベースの初期化]** タブで、セカンダリ データベースを初期化するためのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-122">On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.</span></span>  
  
7.  <span data-ttu-id="4db4d-123">**[ファイルのコピー]** タブの **[ファイルのコピー先フォルダー]** に、トランザクション ログ バックアップのコピー先フォルダーのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-123">On the **Copy Files tab**, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied.</span></span> <span data-ttu-id="4db4d-124">多くの場合、セカンダリ サーバー上のフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-124">This folder is often located on the secondary server.</span></span>  
  
8.  <span data-ttu-id="4db4d-125">**[復元ジョブ]** の **[スケジュール]** ボックスにコピー スケジュールの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4db4d-125">Note the copy schedule listed in the **Schedule** box under **Copy job**.</span></span> <span data-ttu-id="4db4d-126">スケジュールをカスタマイズする場合、 **[スケジュール]** をクリックして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのスケジュールを必要に応じて調整します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-126">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="4db4d-127">このスケジュールはバックアップ スケジュールに近い設定にします。</span><span class="sxs-lookup"><span data-stu-id="4db4d-127">This schedule should approximate the backup schedule.</span></span>  
  
9. <span data-ttu-id="4db4d-128">**[復元]** タブの **[バックアップ復元時のデータベース状態]** で、 **[復旧モードなし]** または **[スタンバイ モード]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-128">On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.</span></span>  
  
10. <span data-ttu-id="4db4d-129">**[スタンバイ モード]** を選択する場合は、復元操作の進行中にセカンダリ データベースからユーザーを切断するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-129">If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.</span></span>  
  
11. <span data-ttu-id="4db4d-130">セカンダリ サーバーの復元処理を遅延させる場合、 **[バックアップの復元を最低限次の期間遅延する]** で遅延時間を選択します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-130">If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.</span></span>  
  
12. <span data-ttu-id="4db4d-131">**[復元が次の期間内に行われない場合は警告する]** で警告のしきい値を選択します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-131">Choose an alert threshold under **Alert if no restore occurs within**.</span></span>  
  
13. <span data-ttu-id="4db4d-132">**[復元ジョブ]** の **[スケジュール]** ボックスに表示される復元スケジュールを確認します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-132">Note the restore schedule listed in the **Schedule** box under **Restore job**.</span></span> <span data-ttu-id="4db4d-133">スケジュールをカスタマイズする場合、 **[スケジュール]** をクリックして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのスケジュールを必要に応じて調整します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-133">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="4db4d-134">このスケジュールはバックアップ スケジュールに近い設定にします。</span><span class="sxs-lookup"><span data-stu-id="4db4d-134">This schedule should approximate the backup schedule.</span></span>  
  
14. <span data-ttu-id="4db4d-135">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4db4d-135">Click **OK**.</span></span>  
  
15. <span data-ttu-id="4db4d-136">[データベースのプロパティ] ダイアログ ボックスの **[OK]** をクリックして、構成処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-136">Click **OK** on the Database Properties dialog box to begin the configuration process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4db4d-137">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4db4d-137">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a><span data-ttu-id="4db4d-138">ログ配布セカンダリ データベースを追加するには</span><span class="sxs-lookup"><span data-stu-id="4db4d-138">To add a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="4db4d-139">セカンダリ サーバーで [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) を実行します。このとき、プライマリ サーバーとプライマリ データベースの詳細情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-139">On the secondary server, execute [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) supplying the details of the primary server and database.</span></span> <span data-ttu-id="4db4d-140">このストアド プロシージャからは、セカンダリ ID、コピー ジョブ ID、および復元ジョブ ID が返されます。</span><span class="sxs-lookup"><span data-stu-id="4db4d-140">This stored procedure returns the secondary ID and the copy and restore job IDs.</span></span>  
  
2.  <span data-ttu-id="4db4d-141">セカンダリ サーバーで [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) を実行して、コピー ジョブと復元ジョブのスケジュールを設定します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-141">On the secondary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to set the schedule for the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="4db4d-142">セカンダリ サーバーで [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) を実行して、セカンダリ データベースを追加します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-142">On the secondary server, execute [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) to add a secondary database.</span></span>  
  
4.  <span data-ttu-id="4db4d-143">プライマリ サーバーで [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) を実行して、新しいセカンダリ データベースに関する必要な情報をプライマリ サーバーに追加します。</span><span class="sxs-lookup"><span data-stu-id="4db4d-143">On the primary server, execute [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) to add the required information about the new secondary database to the primary server.</span></span>  
  
5.  <span data-ttu-id="4db4d-144">セカンダリ サーバーでコピー ジョブと復元ジョブを有効にします。</span><span class="sxs-lookup"><span data-stu-id="4db4d-144">On the secondary server, enable the copy and restore jobs.</span></span> <span data-ttu-id="4db4d-145">詳細については、「 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4db4d-145">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4db4d-146">関連タスク</span><span class="sxs-lookup"><span data-stu-id="4db4d-146">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4db4d-147">ログ配布を SQL Server 2014 &#40;Transact-sql&#41;にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="4db4d-147">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="4db4d-148">ログ配布の構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4db4d-148">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="4db4d-149">ログ配布構成からのセカンダリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4db4d-149">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="4db4d-150">ログ配布の削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4db4d-150">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="4db4d-151">ログ配布レポートの表示 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4db4d-151">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="4db4d-152">ログ配布の監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4db4d-152">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="4db4d-153">ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4db4d-153">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4db4d-154">参照</span><span class="sxs-lookup"><span data-stu-id="4db4d-154">See Also</span></span>  
 <span data-ttu-id="4db4d-155">[ログ配布について &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4db4d-155">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="4db4d-156">ログ配布テーブルとストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4db4d-156">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
