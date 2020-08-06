---
title: ディスク ファイルの論理バックアップ デバイスの定義 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8aa92296da81f984f260deace887c15f13443b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742341"
---
# <a name="define-a-logical-backup-device-for-a-disk-file-sql-server"></a><span data-ttu-id="a0e48-102">ディスク ファイルの論理バックアップ デバイスの定義 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a0e48-102">Define a Logical Backup Device for a Disk File (SQL Server)</span></span>
  <span data-ttu-id="a0e48-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でディスク ファイルの論理バックアップ デバイスを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0e48-103">This topic describes how to define a logical backup device for a disk file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a0e48-104">論理バックアップ デバイスとは、特定の物理バックアップ デバイス (ディスク ファイルまたはテープ ドライブ) を示すユーザー定義名です。</span><span class="sxs-lookup"><span data-stu-id="a0e48-104">A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span>  <span data-ttu-id="a0e48-105">物理デバイスは、後で、つまりバックアップがバックアップ デバイスに書き込まれたときに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="a0e48-105">The initialization of the physical device occurs later, when a backup is written to the backup device.</span></span>  
  
 <span data-ttu-id="a0e48-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a0e48-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a0e48-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a0e48-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a0e48-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a0e48-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a0e48-109">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="a0e48-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a0e48-110">Security</span><span class="sxs-lookup"><span data-stu-id="a0e48-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a0e48-111">**ディスク ファイルの論理バックアップ デバイスを定義する方法:**</span><span class="sxs-lookup"><span data-stu-id="a0e48-111">**To define a logical backup device for a disk file, using:**</span></span>  
  
     [<span data-ttu-id="a0e48-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a0e48-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a0e48-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a0e48-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a0e48-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="a0e48-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a0e48-115">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a0e48-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a0e48-116">論理デバイス名は、サーバー インスタンス上のすべての論理バックアップ デバイスで一意になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0e48-116">The logical device name must be unique among all the logical backup devices on the server instance.</span></span> <span data-ttu-id="a0e48-117">既存の論理デバイス名を表示するには、 [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) カタログ ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="a0e48-117">To view the existing logical device names, query the [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) catalog view.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a0e48-118">推奨事項</span><span class="sxs-lookup"><span data-stu-id="a0e48-118">Recommendations</span></span>  
  
-   <span data-ttu-id="a0e48-119">バックアップ ディスクには、データベースのデータ ディスクやログ ディスクとは別のディスクを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a0e48-119">We recommend that a backup disk be a different disk than the database data and log disks.</span></span> <span data-ttu-id="a0e48-120">これは、データ ディスクやログ ディスクで障害が発生した場合に確実にバックアップにアクセスできるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="a0e48-120">This is necessary to make sure that you can access the backups if the data or log disk fails.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a0e48-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a0e48-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a0e48-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="a0e48-122">Permissions</span></span>  
 <span data-ttu-id="a0e48-123">**diskadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="a0e48-123">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="a0e48-124">ディスクに対する書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a0e48-124">Requires permission to write to the disk.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a0e48-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a0e48-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-disk-file"></a><span data-ttu-id="a0e48-126">ディスク ファイルの論理バックアップ デバイスを定義するには</span><span class="sxs-lookup"><span data-stu-id="a0e48-126">To define a logical backup device for a disk file</span></span>  
  
1.  <span data-ttu-id="a0e48-127">オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a0e48-127">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="a0e48-128">**[サーバー オブジェクト]** を展開し、 **[バックアップ デバイス]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="a0e48-128">Expand **Server Objects**, and right-click **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="a0e48-129">**[新しいバックアップ デバイス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0e48-129">Click **New Backup Device**.</span></span> <span data-ttu-id="a0e48-130">**[バックアップ デバイス]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="a0e48-130">The **Backup Device** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="a0e48-131">デバイス名を入力します。</span><span class="sxs-lookup"><span data-stu-id="a0e48-131">Enter a device name.</span></span>  
  
5.  <span data-ttu-id="a0e48-132">バックアップ先として、 **[ファイル]** をクリックし、ファイルの完全なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0e48-132">For the destination, click **File** and specify the full path of the file.</span></span>  
  
6.  <span data-ttu-id="a0e48-133">新しいデバイスを定義するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0e48-133">To define the new device, click **OK**.</span></span>  
  
 <span data-ttu-id="a0e48-134">この新しいデバイスにバックアップするには、このデバイスを **[データベースのバックアップ]** ダイアログ ボックス ( **[全般]** ) の **[バックアップ先]** フィールドに追加します。</span><span class="sxs-lookup"><span data-stu-id="a0e48-134">To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box.</span></span> <span data-ttu-id="a0e48-135">詳細については、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0e48-135">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a0e48-136">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a0e48-136">Using Transact-SQL</span></span>  
  
#### <a name="to-define-a-logical-backup-for-a-disk-file"></a><span data-ttu-id="a0e48-137">ディスク ファイルの論理バックアップを定義するには</span><span class="sxs-lookup"><span data-stu-id="a0e48-137">To define a logical backup for a disk file</span></span>  
  
1.  <span data-ttu-id="a0e48-138">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="a0e48-138">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a0e48-139">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0e48-139">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a0e48-140">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0e48-140">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a0e48-141">この例では、 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) を使用して、ディスク ファイルの論理バックアップ デバイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="a0e48-141">This example shows how to use [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) to define a logical backup device for a disk file.</span></span> <span data-ttu-id="a0e48-142">この例では、 `mydiskdump`という物理名を持つ、 `c:\dump\dump1.bak`というディスク バックアップ デバイスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a0e48-142">The example adds the disk backup device named `mydiskdump`, with the physical name `c:\dump\dump1.bak`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0e48-143">参照</span><span class="sxs-lookup"><span data-stu-id="a0e48-143">See Also</span></span>  
 <span data-ttu-id="a0e48-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0e48-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="a0e48-145">[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a0e48-145">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="a0e48-146">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0e48-146">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="a0e48-147">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0e48-147">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="a0e48-148">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0e48-148">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span></span>  
 <span data-ttu-id="a0e48-149">[テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a0e48-149">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="a0e48-150">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a0e48-150">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
