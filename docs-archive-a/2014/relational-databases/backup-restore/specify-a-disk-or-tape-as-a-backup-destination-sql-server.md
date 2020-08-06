---
title: バックアップ先としてディスクまたはテープを指定する (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
- backups [SQL Server], creating
- tape backup devices, backing up
ms.assetid: e391f452-ed8c-4b40-b846-ac3881271b94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a0f8ec5d9741e42f3b7d8eda8ebdba23622982d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715413"
---
# <a name="specify-a-disk-or-tape-as-a-backup-destination-sql-server"></a><span data-ttu-id="21b93-102">バックアップ先としてディスクまたはテープを指定する (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="21b93-102">Specify a Disk or Tape As a Backup Destination (SQL Server)</span></span>
  <span data-ttu-id="21b93-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、バックアップ先としてディスクまたはテープを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="21b93-103">This topic describes how to specify a disk or tape as a backup destination in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21b93-104">テープ バックアップ デバイスは、将来のバージョンの SQL Server でサポートされなくなる予定です。</span><span class="sxs-lookup"><span data-stu-id="21b93-104">Support for tape backup devices will be removed in a future version of SQL Server.</span></span> <span data-ttu-id="21b93-105">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="21b93-105">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="21b93-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="21b93-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="21b93-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="21b93-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="21b93-108">Security</span><span class="sxs-lookup"><span data-stu-id="21b93-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="21b93-109">**バックアップ先としてディスクまたはテープを指定する方法:**</span><span class="sxs-lookup"><span data-stu-id="21b93-109">**To specify a disk or tape as a backup destination, using:**</span></span>  
  
     [<span data-ttu-id="21b93-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="21b93-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="21b93-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="21b93-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="21b93-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="21b93-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="21b93-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="21b93-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="21b93-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="21b93-114">Permissions</span></span>  
 <span data-ttu-id="21b93-115">BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。</span><span class="sxs-lookup"><span data-stu-id="21b93-115">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="21b93-116">バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。</span><span class="sxs-lookup"><span data-stu-id="21b93-116">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="21b93-117">では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="21b93-117">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="21b93-118">ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認されません。</span><span class="sxs-lookup"><span data-stu-id="21b93-118">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="21b93-119">バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="21b93-119">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="21b93-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="21b93-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-disk-or-tape-as-a-backup-destination"></a><span data-ttu-id="21b93-121">バックアップ先としてディスクまたはテープを指定するには</span><span class="sxs-lookup"><span data-stu-id="21b93-121">To specify a disk or tape as a backup destination</span></span>  
  
1.  <span data-ttu-id="21b93-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]で適切な オブジェクト エクスプローラーのインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="21b93-122">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="21b93-123">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="21b93-123">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="21b93-124">データベースを右クリックして **[タスク]** をポイントし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21b93-124">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="21b93-125">**[データベースのバックアップ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="21b93-125">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="21b93-126">**[全般]** ページの **[バックアップ先]** セクションで、 **[ディスク]** または **[テープ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21b93-126">In the **Destination** section of the **General** page, click **Disk** or **Tape**.</span></span> <span data-ttu-id="21b93-127">1 つのメディア セットを含んでいる最大 64 個のディスク ドライブまたはテープ ドライブのパスを選択するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21b93-127">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span>  
  
     <span data-ttu-id="21b93-128">バックアップ先を削除するには、バックアップ先を選択して **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21b93-128">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="21b93-129">バックアップ先の内容を表示するには、バックアップ先を選択して **[内容]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21b93-129">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="21b93-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="21b93-130">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-disk-or-tape-as-a-backup-destination"></a><span data-ttu-id="21b93-131">バックアップ先としてディスクまたはテープを指定するには</span><span class="sxs-lookup"><span data-stu-id="21b93-131">To specify a disk or tape as a backup destination</span></span>  
  
1.  <span data-ttu-id="21b93-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="21b93-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="21b93-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="21b93-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="21b93-134">[BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントは、ファイルまたはデバイスとその物理名を指定します。</span><span class="sxs-lookup"><span data-stu-id="21b93-134">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the file or device and its physical name.</span></span> <span data-ttu-id="21b93-135">この例では、 `AdventureWorks2012` データベースをディスク ファイル `Z:\SQLServerBackups\AdventureWorks2012.Bak`にバックアップします。</span><span class="sxs-lookup"><span data-stu-id="21b93-135">This example backs up the `AdventureWorks2012` database to the disk file `Z:\SQLServerBackups\AdventureWorks2012.Bak`.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="21b93-136">参照</span><span class="sxs-lookup"><span data-stu-id="21b93-136">See Also</span></span>  
 <span data-ttu-id="21b93-137">[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="21b93-137">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="21b93-138">[ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="21b93-138">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="21b93-139">[ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="21b93-139">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 <span data-ttu-id="21b93-140">[データベースの差分バックアップの作成 &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="21b93-140">[Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="21b93-141">テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="21b93-141">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
