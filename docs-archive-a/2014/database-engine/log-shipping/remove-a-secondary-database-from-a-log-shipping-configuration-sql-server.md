---
title: ログ配布構成からのセカンダリ データベースの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- deleting secondary databases
- secondary databases [SQL Server], in log shipping
- removing secondary databases
- secondary data files [SQL Server], removing
- log shipping [SQL Server], secondary databases
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 119f2762d41d0787b6b3279507e9671e89fddfca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642279"
---
# <a name="remove-a-secondary-database-from-a-log-shipping-configuration-sql-server"></a><span data-ttu-id="1dd0d-102">ログ配布構成からのセカンダリ データベースの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1dd0d-102">Remove a Secondary Database from a Log Shipping Configuration (SQL Server)</span></span>
  <span data-ttu-id="1dd0d-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ログ配布セカンダリ データベースを削除する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-103">This topic describes how to remove a log shipping secondary database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1dd0d-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="1dd0d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1dd0d-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="1dd0d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1dd0d-106">Security</span><span class="sxs-lookup"><span data-stu-id="1dd0d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1dd0d-107">**以下を使用してログ配布セカンダリ データベースを削除するには:**</span><span class="sxs-lookup"><span data-stu-id="1dd0d-107">**To remove a log shipping secondary database, using:**</span></span>  
  
     [<span data-ttu-id="1dd0d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1dd0d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1dd0d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1dd0d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="1dd0d-110">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1dd0d-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1dd0d-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="1dd0d-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1dd0d-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1dd0d-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1dd0d-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="1dd0d-113">Permissions</span></span>  
 <span data-ttu-id="1dd0d-114">ログ配布ストアド プロシージャには、 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1dd0d-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="1dd0d-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-a-log-shipping-secondary-database"></a><span data-ttu-id="1dd0d-116">ログ配布セカンダリ データベースを削除するには</span><span class="sxs-lookup"><span data-stu-id="1dd0d-116">To remove a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="1dd0d-117">現在のログ配布プライマリ サーバーである [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-117">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is currently the log shipping primary server and expand that instance.</span></span>  
  
2.  <span data-ttu-id="1dd0d-118">**[データベース]** を展開し、ログ配布プライマリ データベースを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-118">Expand **Databases**, right-click the log shipping primary database, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="1dd0d-119">**[ページの選択]** の **[トランザクション ログの配布]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-119">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
4.  <span data-ttu-id="1dd0d-120">**[セカンダリ サーバー インスタンスとデータベース]** で、削除するデータベースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-120">Under **Secondary server instances and databases**, click the database you want to remove.</span></span>  
  
5.  <span data-ttu-id="1dd0d-121">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-121">Click **Remove**.</span></span>  
  
6.  <span data-ttu-id="1dd0d-122">**[OK]** をクリックすると構成が更新されます。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-122">Click **OK** to update the configuration.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1dd0d-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="1dd0d-123">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-a-secondary-database"></a><span data-ttu-id="1dd0d-124">セカンダリ データベースを削除するには</span><span class="sxs-lookup"><span data-stu-id="1dd0d-124">To Remove a Secondary Database</span></span>  
  
1.  <span data-ttu-id="1dd0d-125">プライマリ サーバーで [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) を実行して、セカンダリ データベースに関する情報をプライマリ サーバーから削除します。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-125">On the primary server, execute [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) to delete the information about the secondary database from the primary server.</span></span>  
  
2.  <span data-ttu-id="1dd0d-126">セカンダリ サーバーで [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) を実行して、セカンダリ データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-126">On the secondary server, execute [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) to delete the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1dd0d-127">同じセカンダリ ID を持つセカンダリ データベースが他にない場合は、 **sp_delete_log_shipping_secondary_primary** が **sp_delete_log_shipping_secondary_database** により呼び出され、セカンダリ ID のエントリ、およびコピー ジョブと復元ジョブが削除されます。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-127">If there are no other secondary databases with the same secondary ID, **sp_delete_log_shipping_secondary_primary** is invoked from **sp_delete_log_shipping_secondary_database** and deletes the entry for the secondary ID and the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="1dd0d-128">セカンダリ サーバーでコピー ジョブと復元ジョブを無効にします。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-128">On the secondary server, disable the copy and restore jobs.</span></span> <span data-ttu-id="1dd0d-129">詳細については、「 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1dd0d-129">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1dd0d-130">関連タスク</span><span class="sxs-lookup"><span data-stu-id="1dd0d-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1dd0d-131">ログ配布を SQL Server 2014 &#40;Transact-sql&#41;にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="1dd0d-131">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="1dd0d-132">ログ配布の構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd0d-132">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="1dd0d-133">ログ配布構成へのセカンダリ データベースの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd0d-133">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="1dd0d-134">ログ配布の削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd0d-134">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="1dd0d-135">ログ配布レポートの表示 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd0d-135">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="1dd0d-136">ログ配布の監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd0d-136">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="1dd0d-137">ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd0d-137">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="1dd0d-138">参照</span><span class="sxs-lookup"><span data-stu-id="1dd0d-138">See Also</span></span>  
 <span data-ttu-id="1dd0d-139">[ログ配布について &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1dd0d-139">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="1dd0d-140">ログ配布テーブルとストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1dd0d-140">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
