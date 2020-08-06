---
title: backup compression default サーバー構成オプションの表示または構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], backup compression default option
- backup compression [SQL Server], backup compression default Option
ms.assetid: 23029395-3e93-4c29-b7d6-e5a47a3526ff
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f02458c069d7c155b199e24feb7ef028ae0f258a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645837"
---
# <a name="view-or-configure-the-backup-compression-default-server-configuration-option"></a><span data-ttu-id="6d787-102">backup compression default サーバー構成オプションの表示または構成</span><span class="sxs-lookup"><span data-stu-id="6d787-102">View or Configure the backup compression default Server Configuration Option</span></span>
  <span data-ttu-id="6d787-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] backup compression default [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを確認または構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6d787-103">This topic describes how to view or configure the **backup compression default** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6d787-104">**backup compression default** オプションは、圧縮されたバックアップを既定で作成するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="6d787-104">The **backup compression default** option determines whether the server instance creates compressed backups by default.</span></span> <span data-ttu-id="6d787-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールした場合、 **backup compression default** オプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="6d787-105">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, the **backup compression default** option is off.</span></span>  
  
 <span data-ttu-id="6d787-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6d787-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6d787-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="6d787-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6d787-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="6d787-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6d787-109">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="6d787-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="6d787-110">Security</span><span class="sxs-lookup"><span data-stu-id="6d787-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6d787-111">**以下を使用して backup compression default オプションを表示および構成するには:**</span><span class="sxs-lookup"><span data-stu-id="6d787-111">**To view or configure the backup compression default option, using:**</span></span>  
  
     [<span data-ttu-id="6d787-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6d787-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6d787-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6d787-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="6d787-114">**補足情報:** [backup compression default オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="6d787-114">**Follow Up:**  [After you configure the backup compression default option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6d787-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="6d787-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6d787-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="6d787-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6d787-117">バックアップ圧縮は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディッションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="6d787-117">Backup compression is not available in all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6d787-118">詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d787-118">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="6d787-119">既定の設定では、圧縮によって CPU 使用率が著しく増加し、圧縮処理によって CPU がさらに消費されるために、同時に実行される操作が悪影響を受ける場合があります。</span><span class="sxs-lookup"><span data-stu-id="6d787-119">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="6d787-120">このため、 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)によって CPU 使用率が制限されるセッションでは、優先度の低い圧縮バックアップを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="6d787-120">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).</span></span> <span data-ttu-id="6d787-121">詳細については、「 [リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d787-121">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6d787-122">推奨事項</span><span class="sxs-lookup"><span data-stu-id="6d787-122">Recommendations</span></span>  
  
-   <span data-ttu-id="6d787-123">個別のバックアップを作成する場合、ログ配布構成を構成する場合、またはメンテナンス プランを作成する場合は、サーバー レベルの既定値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="6d787-123">When you are creating an individual backup, configuring a log shipping configuration, or creating a maintenance plan, you can override the server-level default.</span></span>  
  
-   <span data-ttu-id="6d787-124">バックアップの圧縮は、ディスク バックアップ デバイスとテープ バックアップ デバイスの両方でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6d787-124">Backup compression is supported for both disk backup devices and tape backup devices.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6d787-125">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6d787-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6d787-126">Permissions</span><span class="sxs-lookup"><span data-stu-id="6d787-126">Permissions</span></span>  
 <span data-ttu-id="6d787-127">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="6d787-127">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="6d787-128">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d787-128">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="6d787-129">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="6d787-129">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6d787-130">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6d787-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-configure-the-backup-compression-default-option"></a><span data-ttu-id="6d787-131">backup compression default オプションを表示および構成するには</span><span class="sxs-lookup"><span data-stu-id="6d787-131">To view or configure the backup compression default option</span></span>  
  
1.  <span data-ttu-id="6d787-132">オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d787-132">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="6d787-133">**[データベースの設定]** ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d787-133">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="6d787-134">**[バックアップと復元]** の **[バックアップを圧縮する]** に、 **backup compression default** オプションの現在の設定が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d787-134">Under **Backup and restore**, **Compress backup** shows the current setting of the **backup compression default** option.</span></span> <span data-ttu-id="6d787-135">この設定によって、バックアップの圧縮についてのサーバー レベルの既定値が次のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="6d787-135">This setting determines the server-level default for compressing backups, as follows:</span></span>  
  
    -   <span data-ttu-id="6d787-136">**[バックアップを圧縮する]** チェック ボックスがオフの場合、既定では新しいバックアップは圧縮されません。</span><span class="sxs-lookup"><span data-stu-id="6d787-136">If the **Compress backup** box is blank, new backups are uncompressed by default.</span></span>  
  
    -   <span data-ttu-id="6d787-137">**[バックアップを圧縮する]** チェック ボックスがオンの場合、既定で新しいバックアップが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="6d787-137">If the **Compress backup** box is checked, new backups are compressed by default.</span></span>  
  
     <span data-ttu-id="6d787-138">**sysadmin** 固定サーバー ロールまたは **serveradmin** 固定サーバー ロールのメンバーである場合は、 **[バックアップを圧縮する]** チェック ボックスをクリックして既定の設定を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="6d787-138">If you are a member of the **sysadmin** or **serveradmin** fixed server role, you can also change the default setting by clicking the **Compress backup** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6d787-139">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6d787-139">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-backup-compression-default-option"></a><span data-ttu-id="6d787-140">backup compression default オプションを表示するには</span><span class="sxs-lookup"><span data-stu-id="6d787-140">To view the backup compression default option</span></span>  
  
1.  <span data-ttu-id="6d787-141">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="6d787-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6d787-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d787-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6d787-143">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d787-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6d787-144">この例では、 [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) カタログ ビューをクエリして、 `backup compression default`の値を判定しています。</span><span class="sxs-lookup"><span data-stu-id="6d787-144">This example queries the [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view to determine the value for `backup compression default`.</span></span> <span data-ttu-id="6d787-145">値 0 はバックアップの圧縮がオフであることを示し、値 1 はバックアップの圧縮が有効であることを示します。</span><span class="sxs-lookup"><span data-stu-id="6d787-145">A value of 0 means that backup compression is off, and a value of 1 means that backup compression is enabled.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
SELECT value   
FROM sys.configurations   
WHERE name = 'backup compression default' ;  
GO  
  
```  
  
#### <a name="to-configure-the-backup-compression-default-option"></a><span data-ttu-id="6d787-146">backup compression default オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="6d787-146">To configure the backup compression default option</span></span>  
  
1.  <span data-ttu-id="6d787-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="6d787-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6d787-148">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d787-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6d787-149">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d787-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6d787-150">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、圧縮されたバックアップが既定で作成されるようにサーバー インスタンスを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6d787-150">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the server instance to create compressed backups by default.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_configure 'backup compression default', 1 ;  
RECONFIGURE WITH OVERRIDE ;  
GO  
  
```  
  
 <span data-ttu-id="6d787-151">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d787-151">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-backup-compression-default-option"></a><a name="FollowUp"></a><span data-ttu-id="6d787-152">補足情報: backup compression default オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="6d787-152">Follow Up: After you configure the backup compression default option</span></span>  
 <span data-ttu-id="6d787-153">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="6d787-153">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d787-154">参照</span><span class="sxs-lookup"><span data-stu-id="6d787-154">See Also</span></span>  
 <span data-ttu-id="6d787-155">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6d787-155">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="6d787-156">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6d787-156">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="6d787-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6d787-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="6d787-158">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6d787-158">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="6d787-159">バックアップの概要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6d787-159">Backup Overview &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/backup-overview-sql-server.md)  
  
  
