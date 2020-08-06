---
title: バックアップの有効期限の設定 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], expiration dates
- expiration [SQL Server]
- database backups [SQL Server], expiration dates
ms.assetid: 76e814df-6487-4893-9f09-7759f1863a5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9185222df93e0a1150256535526ba910c593cf6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634567"
---
# <a name="set-the-expiration-date-on-a-backup-sql-server"></a><span data-ttu-id="d1384-102">バックアップの有効期限の設定 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d1384-102">Set the Expiration Date on a Backup (SQL Server)</span></span>
  <span data-ttu-id="d1384-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、バックアップの有効期限を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1384-103">This topic describes how to set the expiration date on a backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d1384-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d1384-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d1384-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d1384-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d1384-106">Security</span><span class="sxs-lookup"><span data-stu-id="d1384-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d1384-107">**バックアップの有効期限を設定する方法:**</span><span class="sxs-lookup"><span data-stu-id="d1384-107">**To set the expiration date on a backup, using:**</span></span>  
  
     [<span data-ttu-id="d1384-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d1384-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d1384-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d1384-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d1384-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="d1384-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d1384-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d1384-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d1384-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="d1384-112">Permissions</span></span>  
 <span data-ttu-id="d1384-113">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="d1384-113">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="d1384-114">バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="d1384-114">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1384-115">では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d1384-115">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="d1384-116">ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認されません。</span><span class="sxs-lookup"><span data-stu-id="d1384-116">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="d1384-117">バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d1384-117">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d1384-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d1384-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a><span data-ttu-id="d1384-119">バックアップの有効期限を設定するには</span><span class="sxs-lookup"><span data-stu-id="d1384-119">To set the expiration date on a backup</span></span>  
  
1.  <span data-ttu-id="d1384-120">オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="d1384-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="d1384-121">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1384-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="d1384-122">データベースを右クリックして **[タスク]** をポイントし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1384-122">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="d1384-123">**[データベースのバックアップ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1384-123">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="d1384-124">**[全般]** ページの **[バックアップ セットの有効期限]** で、バックアップ セットを別のバックアップで上書きできる期日を示す有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1384-124">On the **General** page, for **Backup set will expire**, specify an expiration date to indicate when the backup set can be overwritten by another backup:</span></span>  
  
    -   <span data-ttu-id="d1384-125">バックアップ セットが指定の日数後に期限切れになるようにするには、 **[期間指定]** \(既定のオプション) をクリックし、セットを作成してからセットが期限切れになるまでの日数を入力します。</span><span class="sxs-lookup"><span data-stu-id="d1384-125">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="d1384-126">0 ～ 99,999 日の値を指定できます。0 日を指定すると、バックアップ セットの有効期限は無期限になります。</span><span class="sxs-lookup"><span data-stu-id="d1384-126">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="d1384-127">既定値は、 **[サーバーのプロパティ]** ダイアログ ボックス ( **[データベースの設定]** ページ) の **[バックアップ メディアの既定の保有期間 (日)]** オプションで設定されています。</span><span class="sxs-lookup"><span data-stu-id="d1384-127">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="d1384-128">このオプションを表示するには、オブジェクト エクスプローラーでサーバー名を右クリックし、プロパティを選択してから **[データベースの設定]** ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1384-128">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="d1384-129">バックアップ セットが特定の日付に期限切れになるようにするには、 **[日時指定]** をクリックし、セットの有効期限が切れる日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="d1384-129">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d1384-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d1384-130">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a><span data-ttu-id="d1384-131">バックアップの有効期限を設定するには</span><span class="sxs-lookup"><span data-stu-id="d1384-131">To set the expiration date on a backup</span></span>  
  
1.  <span data-ttu-id="d1384-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="d1384-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d1384-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1384-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d1384-134">[BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントで、 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] がいつバックアップを上書きできるようになるかを決定する EXPIREDATE または RETAINDAYS オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1384-134">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify either the EXPIREDATE or RETAINDAYS option to determine when the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] can overwrite the backup.</span></span> <span data-ttu-id="d1384-135">どちらのオプションも指定しない場合、失効日は [media retention](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) (メディア保持期間) のサーバー設定によって決まります。</span><span class="sxs-lookup"><span data-stu-id="d1384-135">If neither option is specified, the expiration date is determined by the [media retention](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) server configuration setting.</span></span> <span data-ttu-id="d1384-136">この例では、 `EXPIREDATE` オプションを使用して、2015 年 6 月 30 日 (`6/30/2015`) の有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1384-136">This example uses the `EXPIREDATE` option to specify an expiration date of June 30, 2015 (`6/30/2015`).</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH EXPIREDATE = '6/30/2015' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1384-137">参照</span><span class="sxs-lookup"><span data-stu-id="d1384-137">See Also</span></span>  
 <span data-ttu-id="d1384-138">[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d1384-138">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="d1384-139">[ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d1384-139">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="d1384-140">[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d1384-140">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="d1384-141">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1384-141">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
  
