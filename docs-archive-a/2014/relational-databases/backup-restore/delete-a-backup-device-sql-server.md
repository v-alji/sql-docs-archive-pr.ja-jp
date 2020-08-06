---
title: バックアップ デバイスの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], deleting devices
- backup devices [SQL Server], deleting
- deleting backup devices
- removing backup devices
- backing up databases [SQL Server], backup devices
ms.assetid: 7be62480-ed6a-4262-a071-1feba73b1c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8734e587a8ecde315fb17120511455a59e38901
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640100"
---
# <a name="delete-a-backup-device-sql-server"></a><span data-ttu-id="48980-102">バックアップ デバイスの削除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="48980-102">Delete a Backup Device (SQL Server)</span></span>
  <span data-ttu-id="48980-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でバックアップ デバイスを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="48980-103">This topic describes how to delete a backup device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="48980-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="48980-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="48980-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="48980-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="48980-106">Security</span><span class="sxs-lookup"><span data-stu-id="48980-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="48980-107">**バックアップ デバイスを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="48980-107">**To delete a backup device, using:**</span></span>  
  
     [<span data-ttu-id="48980-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="48980-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="48980-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="48980-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="48980-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="48980-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="48980-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="48980-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="48980-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="48980-112">Permissions</span></span>  
 <span data-ttu-id="48980-113">**diskadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="48980-113">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="48980-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="48980-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-backup-device"></a><span data-ttu-id="48980-115">バックアップ デバイスを削除するには</span><span class="sxs-lookup"><span data-stu-id="48980-115">To delete a backup device</span></span>  
  
1.  <span data-ttu-id="48980-116">適切な [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスへの接続後、オブジェクト エクスプローラーでサーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="48980-116">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="48980-117">**[サーバー オブジェクト]** を展開し、 **[バックアップ デバイス]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="48980-117">Expand **Server Objects**, and then expand **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="48980-118">削除するデバイスを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48980-118">Right-click the device you want, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="48980-119">**[オブジェクトの削除]** ダイアログ ボックスで、 **[オブジェクト名]** 列に正しいデバイス名が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="48980-119">In the **Delete Object** dialog box, verify that the correct device name appears in the **Object Name** column.</span></span>  
  
5.  <span data-ttu-id="48980-120">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48980-120">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="48980-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="48980-121">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-backup-device"></a><span data-ttu-id="48980-122">バックアップ デバイスを削除するには</span><span class="sxs-lookup"><span data-stu-id="48980-122">To delete a backup device</span></span>  
  
1.  <span data-ttu-id="48980-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="48980-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="48980-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48980-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="48980-125">次の例をコピーし、クエリに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="48980-125">Copy and paste the following example into the query.</span></span> <span data-ttu-id="48980-126">この例では、 [sp_dropdevice](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) を使用して、バックアップ デバイスを削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="48980-126">This example shows how to use [sp_dropdevice](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) to delete a backup device.</span></span> <span data-ttu-id="48980-127">1 つ目の例を実行して、 `mybackupdisk` バックアップ デバイス と物理名 `c:\backup\backup1.bak`を作成します。</span><span class="sxs-lookup"><span data-stu-id="48980-127">Execute the first example to create the `mybackupdisk` backup device and the physical name `c:\backup\backup1.bak`.</span></span> <span data-ttu-id="48980-128">`sp_dropdevice` を実行して、`mybackupdisk` バックアップ デバイスを削除します。</span><span class="sxs-lookup"><span data-stu-id="48980-128">Execute `sp_dropdevice` to delete the `mybackupdisk` backup device.</span></span> <span data-ttu-id="48980-129">`delfile` パラメーターは物理名を削除します。</span><span class="sxs-lookup"><span data-stu-id="48980-129">The `delfile` parameter deletes the physical name.</span></span>  
  
```sql  
--Define a backup device and physical name.   
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mybackupdisk', 'c:\backup\backup1.bak' ;  
GO  
--Delete the backup device and the physical name.  
USE AdventureWorks2012 ;  
GO  
EXEC sp_dropdevice ' mybackupdisk ', 'delfile' ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="48980-130">参照</span><span class="sxs-lookup"><span data-stu-id="48980-130">See Also</span></span>  
 <span data-ttu-id="48980-131">[論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="48980-131">[View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span></span>  
 <span data-ttu-id="48980-132">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="48980-132">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="48980-133">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="48980-133">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="48980-134">[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="48980-134">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="48980-135">sp_addumpdevice &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="48980-135">sp_addumpdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
  
