---
title: デバイスからのバックアップ復元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], device restores
- backup devices [SQL Server], restoring from
- database restores [SQL Server], device restores
- devices [SQL Server]
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50d7f7b8e255aea470a1065df669c0cc3169a8dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714438"
---
# <a name="restore-a-backup-from-a-device-sql-server"></a><span data-ttu-id="c6347-102">デバイスからのバックアップ復元 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c6347-102">Restore a Backup from a Device (SQL Server)</span></span>
  <span data-ttu-id="c6347-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、バックアップをデバイスから復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6347-103">This topic describes how to restore a backup from a device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6347-104">Azure Blob ストレージサービスへの SQL Server のバックアップの詳細については、「」 SQL Server、「 [Azure Blob Storage サービスを使用したバックアップと復元](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6347-104">For information on SQL Server backup to the Azure Blob storage service, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="c6347-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c6347-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c6347-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c6347-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c6347-107">Security</span><span class="sxs-lookup"><span data-stu-id="c6347-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c6347-108">**デバイスからバックアップを復元する方法:**</span><span class="sxs-lookup"><span data-stu-id="c6347-108">**To restore a backup from a device, using:**</span></span>  
  
     [<span data-ttu-id="c6347-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c6347-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c6347-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c6347-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c6347-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="c6347-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c6347-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c6347-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c6347-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="c6347-113">Permissions</span></span>  
 <span data-ttu-id="c6347-114">復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6347-114">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="c6347-115">データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。</span><span class="sxs-lookup"><span data-stu-id="c6347-115">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="c6347-116">RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。</span><span class="sxs-lookup"><span data-stu-id="c6347-116">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="c6347-117">固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="c6347-117">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c6347-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c6347-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-backup-from-a-device"></a><span data-ttu-id="c6347-119">デバイスからバックアップを復元するには</span><span class="sxs-lookup"><span data-stu-id="c6347-119">To restore a backup from a device</span></span>  
  
1.  <span data-ttu-id="c6347-120">オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="c6347-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="c6347-121">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6347-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="c6347-122">データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6347-122">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="c6347-123">実行する復元操作の種類 ( **[データベース]** 、 **[ファイルとファイル グループ]** 、または **[トランザクション ログ]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6347-123">Click the type of restore operation you want (**Database**, **Files and Filegroups**, or **Transaction Log**).</span></span> <span data-ttu-id="c6347-124">対応する復元ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="c6347-124">This opens the corresponding restore dialog box.</span></span>  
  
5.  <span data-ttu-id="c6347-125">**[全般]** ページの **[復元用のソース]** セクションで、 **[デバイスから]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6347-125">On the **General** page, in the **Restore source** section, click **From device**.</span></span>  
  
6.  <span data-ttu-id="c6347-126">**[デバイスから]** ボックスの参照ボタン ([...]) をクリックします。 **[バックアップの指定]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="c6347-126">Click the browse button for the **From device** text box, which opens the **Specify Backup** dialog box.</span></span>  
  
7.  <span data-ttu-id="c6347-127">**[バックアップ メディア]** ボックスの一覧で、 **[バックアップ デバイス]** をクリックします。次に、 **[追加]** をクリックして **[バックアップ デバイスの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="c6347-127">In the **Backup media** text box, select **Backup Device**, and click the **Add** button to open the **Select Backup Device** dialog box.</span></span>  
  
8.  <span data-ttu-id="c6347-128">**[バックアップ デバイス]** ボックスで、復元操作に使用するデバイスを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6347-128">In the **Backup device** text box, select the device you want to use for the restore operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c6347-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c6347-129">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-backup-from-a-device"></a><span data-ttu-id="c6347-130">デバイスからバックアップを復元するには</span><span class="sxs-lookup"><span data-stu-id="c6347-130">To restore a backup from a device</span></span>  
  
1.  <span data-ttu-id="c6347-131">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="c6347-131">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c6347-132">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6347-132">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c6347-133">[RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントで、バックアップ操作に使用する論理バックアップ デバイスまたは物理バックアップ デバイスを、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="c6347-133">In the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify a logical or physical backup device to use for the backup operation.</span></span> <span data-ttu-id="c6347-134">この例は、物理名が `Z:\SQLServerBackups\AdventureWorks2012.bak`というディスク ファイルから復元します。</span><span class="sxs-lookup"><span data-stu-id="c6347-134">This example restores from a disk file that has the physical name `Z:\SQLServerBackups\AdventureWorks2012.bak`.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6347-135">参照</span><span class="sxs-lookup"><span data-stu-id="c6347-135">See Also</span></span>  
 <span data-ttu-id="c6347-136">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6347-136">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="c6347-137">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6347-137">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="c6347-138">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6347-138">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="c6347-139">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6347-139">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="c6347-140">[単純復旧モデルでのデータベース バックアップの復元 &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="c6347-140">[Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md) </span></span>  
 <span data-ttu-id="c6347-141">[データベースバックアップを復元する &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="c6347-141">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="c6347-142">[データベースの差分バックアップの復元 &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6347-142">[Restore a Differential Database Backup &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="c6347-143">[データベースを新しい場所に復元する &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6347-143">[Restore a Database to a New Location &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="c6347-144">[ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6347-144">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="c6347-145">[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6347-145">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="c6347-146">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c6347-146">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
  
