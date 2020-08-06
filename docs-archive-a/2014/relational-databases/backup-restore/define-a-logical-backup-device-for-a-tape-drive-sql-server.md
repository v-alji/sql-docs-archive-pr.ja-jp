---
title: テープ ドライブの論理バックアップ デバイスの定義 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- tape backup devices, creating
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8728df2cc0b5907e51da84ed9e77d897a1718d36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742334"
---
# <a name="define-a-logical-backup-device-for-a-tape-drive-sql-server"></a><span data-ttu-id="e0cf7-102">テープ ドライブの論理バックアップ デバイスの定義 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e0cf7-102">Define a Logical Backup Device for a Tape Drive (SQL Server)</span></span>
  <span data-ttu-id="e0cf7-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でテープ ドライブの論理バックアップ デバイスを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-103">This topic describes how to define a logical backup device for a tape drive in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e0cf7-104">論理バックアップ デバイスとは、特定の物理バックアップ デバイス (ディスク ファイルまたはテープ ドライブ) を示すユーザー定義名です。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-104">A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span>  <span data-ttu-id="e0cf7-105">物理デバイスは、後で、つまりバックアップがバックアップ デバイスに書き込まれたときに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-105">The initialization of the physical device occurs later, when a backup is written to the backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0cf7-106">テープ バックアップ デバイスは、将来のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でサポートされなくなる予定です。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-106">Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e0cf7-107">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-107">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="e0cf7-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e0cf7-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e0cf7-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e0cf7-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e0cf7-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e0cf7-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e0cf7-111">Security</span><span class="sxs-lookup"><span data-stu-id="e0cf7-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e0cf7-112">**テープ ドライブの論理バックアップ デバイスを定義する方法:**</span><span class="sxs-lookup"><span data-stu-id="e0cf7-112">**To define a logical backup device for a tape drive, using:**</span></span>  
  
     [<span data-ttu-id="e0cf7-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e0cf7-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e0cf7-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e0cf7-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e0cf7-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="e0cf7-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e0cf7-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e0cf7-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e0cf7-117">テープ ドライブまたはドライブは、Microsoft Windows オペレーティング システムによってサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-117">The tape drive or drives must be supported by the Microsoft Windows operating system.</span></span>  
  
-   <span data-ttu-id="e0cf7-118">テープ デバイスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスが動作しているコンピューターに物理的に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-118">The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e0cf7-119">リモートのテープ デバイスへのバックアップはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-119">Backing up to remote tape devices is not supported.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e0cf7-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e0cf7-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e0cf7-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="e0cf7-121">Permissions</span></span>  
 <span data-ttu-id="e0cf7-122">**diskadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-122">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="e0cf7-123">ディスクに対する書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-123">Requires permission to write to the disk.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e0cf7-124">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e0cf7-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a><span data-ttu-id="e0cf7-125">テープ ドライブの論理バックアップ デバイスを定義するには</span><span class="sxs-lookup"><span data-stu-id="e0cf7-125">To define a logical backup device for a tape drive</span></span>  
  
1.  <span data-ttu-id="e0cf7-126">オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-126">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="e0cf7-127">**[サーバー オブジェクト]** を展開し、 **[バックアップ デバイス]** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-127">Expand **Server Objects**, and then right-click **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="e0cf7-128">**[新しいバックアップ デバイス]** をクリックし、 **[バックアップ デバイス]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-128">Click **New Backup Device**, which opens the **Backup Device** dialog box.</span></span>  
  
4.  <span data-ttu-id="e0cf7-129">デバイス名を入力します。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-129">Enter a device name.</span></span>  
  
5.  <span data-ttu-id="e0cf7-130">バックアップ先として **[テープ]** をクリックし、まだ別のバックアップ デバイスに関連付けられていないテープ ドライブを選択します。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-130">For the destination, click **Tape** and select a tape drive that is not already associated with another backup device.</span></span> <span data-ttu-id="e0cf7-131">使用できるテープ ドライブがない場合、 **[テープ]** オプションはアクティブになりません。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-131">If no such tape drives are available, the **Tape** option is inactive.</span></span>  
  
6.  <span data-ttu-id="e0cf7-132">新しいデバイスを定義するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-132">To define the new device, click **OK**.</span></span>  
  
 <span data-ttu-id="e0cf7-133">この新しいデバイスにバックアップするには、このデバイスを **[データベースのバックアップ]** ダイアログ ボックス ( **[全般]** ) の **[バックアップ先]** フィールドに追加します。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-133">To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box.</span></span> <span data-ttu-id="e0cf7-134">詳細については、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-134">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e0cf7-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e0cf7-135">Using Transact-SQL</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a><span data-ttu-id="e0cf7-136">テープ ドライブの論理バックアップ デバイスを定義するには</span><span class="sxs-lookup"><span data-stu-id="e0cf7-136">To define a logical backup device for a tape drive</span></span>  
  
1.  <span data-ttu-id="e0cf7-137">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-137">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e0cf7-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e0cf7-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e0cf7-140">この例では、 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) を使用して、テープの論理バックアップ デバイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-140">This example shows how to use [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) to define a logical backup device for a tape.</span></span> <span data-ttu-id="e0cf7-141">この例では、 `tapedump1`というテープ バックアップ デバイスを物理名 `\\.\tape0`で追加します。</span><span class="sxs-lookup"><span data-stu-id="e0cf7-141">The example adds the tape backup device named `tapedump1`, with the physical name `\\.\tape0`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0cf7-142">参照</span><span class="sxs-lookup"><span data-stu-id="e0cf7-142">See Also</span></span>  
 <span data-ttu-id="e0cf7-143">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0cf7-143">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="e0cf7-144">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0cf7-144">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="e0cf7-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0cf7-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="e0cf7-146">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e0cf7-146">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span></span>  
 <span data-ttu-id="e0cf7-147">[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e0cf7-147">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="e0cf7-148">[ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e0cf7-148">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 [<span data-ttu-id="e0cf7-149">論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0cf7-149">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
