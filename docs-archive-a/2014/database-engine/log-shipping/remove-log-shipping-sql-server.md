---
title: ログ配布の削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], removing
- removing log shipping
- deleting log shipping
ms.assetid: 859373db-c744-4a4b-8479-45163f61e8cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 14fdc36c66073e89dcc2014aed4319a2ce78a98f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641210"
---
# <a name="remove-log-shipping-sql-server"></a><span data-ttu-id="6373a-102">ログ配布の削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6373a-102">Remove Log Shipping (SQL Server)</span></span>
  <span data-ttu-id="6373a-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ログ配布を削除する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6373a-103">This topic describes how to remove log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6373a-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6373a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6373a-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="6373a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6373a-106">Security</span><span class="sxs-lookup"><span data-stu-id="6373a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6373a-107">**以下を使用してログ配布を削除するには:**</span><span class="sxs-lookup"><span data-stu-id="6373a-107">**To remove log shipping, using:**</span></span>  
  
     [<span data-ttu-id="6373a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6373a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6373a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6373a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="6373a-110">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6373a-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6373a-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="6373a-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6373a-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6373a-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6373a-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="6373a-113">Permissions</span></span>  
 <span data-ttu-id="6373a-114">ログ配布ストアド プロシージャには、 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="6373a-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6373a-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6373a-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-log-shipping"></a><span data-ttu-id="6373a-116">ログ配布を削除するには</span><span class="sxs-lookup"><span data-stu-id="6373a-116">To remove log shipping</span></span>  
  
1.  <span data-ttu-id="6373a-117">現在のログ配布プライマリ サーバーである [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="6373a-117">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is currently the log shipping primary server and expand that instance.</span></span>  
  
2.  <span data-ttu-id="6373a-118">**[データベース]** を展開し、ログ配布プライマリ データベースを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6373a-118">Expand **Databases**, right-click the log shipping primary database, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="6373a-119">**[ページの選択]** の **[トランザクション ログの配布]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6373a-119">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
4.  <span data-ttu-id="6373a-120">**[ログ配布構成のプライマリ データベースとして有効にする]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="6373a-120">Clear the **Enable this as a primary database in a log shipping configuration** check box.</span></span>  
  
5.  <span data-ttu-id="6373a-121">**[OK]** をクリックして、このプライマリ データベースからログ配布を削除します。</span><span class="sxs-lookup"><span data-stu-id="6373a-121">Click **OK** to remove log shipping from this primary database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6373a-122">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6373a-122">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-log-shipping"></a><span data-ttu-id="6373a-123">ログ配布を削除するには</span><span class="sxs-lookup"><span data-stu-id="6373a-123">To Remove Log Shipping</span></span>  
  
1.  <span data-ttu-id="6373a-124">ログ配布プライマリ サーバーで [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) を実行して、セカンダリ データベースに関する情報をプライマリ サーバーから削除します。</span><span class="sxs-lookup"><span data-stu-id="6373a-124">On the log shipping primary server, execute [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) to delete the information about the secondary database from the primary server.</span></span>  
  
2.  <span data-ttu-id="6373a-125">ログ配布セカンダリ サーバーで [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) を実行して、セカンダリ データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="6373a-125">On the log shipping secondary server, execute [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) to delete the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6373a-126">同じセカンダリ ID を持つセカンダリ データベースが他にない場合は、 **sp_delete_log_shipping_secondary_primary** が **sp_delete_log_shipping_secondary_database** により呼び出され、セカンダリ ID のエントリ、およびコピー ジョブと復元ジョブが削除されます。</span><span class="sxs-lookup"><span data-stu-id="6373a-126">If there are no other secondary databases with the same secondary ID, **sp_delete_log_shipping_secondary_primary** is invoked from **sp_delete_log_shipping_secondary_database** and deletes the entry for the secondary ID and the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="6373a-127">ログ配布プライマリ サーバーで **sp_delete_log_shipping_primary_database** を実行して、ログ配布構成に関する情報をプライマリ サーバーから削除します。</span><span class="sxs-lookup"><span data-stu-id="6373a-127">On the log shipping primary server, execute **sp_delete_log_shipping_primary_database** to delete information about the log shipping configuration from the primary server.</span></span> <span data-ttu-id="6373a-128">これは、バックアップ ジョブも同時に削除します。</span><span class="sxs-lookup"><span data-stu-id="6373a-128">This also deletes the backup job.</span></span>  
  
4.  <span data-ttu-id="6373a-129">ログ配布プライマリ サーバーでバックアップ ジョブを無効にします。</span><span class="sxs-lookup"><span data-stu-id="6373a-129">On the log shipping primary server, disable the backup job.</span></span> <span data-ttu-id="6373a-130">詳細については、「 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6373a-130">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
5.  <span data-ttu-id="6373a-131">ログ配布セカンダリ サーバーでコピー ジョブと復元ジョブを無効にします。</span><span class="sxs-lookup"><span data-stu-id="6373a-131">On the log shipping secondary server, disable the copy and restore jobs.</span></span>  
  
6.  <span data-ttu-id="6373a-132">必要に応じて、使用しなくなったログ配布セカンダリ データベースをセカンダリ サーバーから削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="6373a-132">Optionally, if you are no longer using the log shipping secondary database, you can delete it from the secondary server.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6373a-133">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6373a-133">Related Tasks</span></span>  
  
-   [<span data-ttu-id="6373a-134">ログ配布を SQL Server 2014 &#40;Transact-sql&#41;にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="6373a-134">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="6373a-135">ログ配布の構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6373a-135">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="6373a-136">ログ配布構成へのセカンダリ データベースの追加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6373a-136">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="6373a-137">ログ配布構成からのセカンダリ データベースの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6373a-137">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="6373a-138">ログ配布の監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6373a-138">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="6373a-139">ログ配布のセカンダリへのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6373a-139">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="6373a-140">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="6373a-140">Disable or Enable a Job</span></span>](../../ssms/agent/disable-or-enable-a-job.md)  
  
## <a name="see-also"></a><span data-ttu-id="6373a-141">参照</span><span class="sxs-lookup"><span data-stu-id="6373a-141">See Also</span></span>  
 <span data-ttu-id="6373a-142">[ログ配布について &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6373a-142">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="6373a-143">ログ配布テーブルとストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="6373a-143">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
