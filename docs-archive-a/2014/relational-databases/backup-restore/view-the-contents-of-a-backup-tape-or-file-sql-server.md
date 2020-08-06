---
title: バックアップ テープまたはバックアップ ファイルの内容の表示 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- displaying backup content
- viewing backup content
- tape backup devices, viewing contents
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
ms.assetid: cd6674a2-ca55-4b5a-a971-878ba001821e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 044519b64d41fbbdfc9302ce24369ab282727f67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718303"
---
# <a name="view-the-contents-of-a-backup-tape-or-file-sql-server"></a><span data-ttu-id="b1d91-102">バックアップ テープまたはバックアップ ファイルの内容の表示 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b1d91-102">View the Contents of a Backup Tape or File (SQL Server)</span></span>
  <span data-ttu-id="b1d91-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]のバックアップ テープまたはバックアップ ファイルの内容を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1d91-103">This topic describes how to view the content of a backup tape or file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1d91-104">テープ バックアップ デバイスは、将来のバージョンの SQL Server でサポートされなくなる予定です。</span><span class="sxs-lookup"><span data-stu-id="b1d91-104">Support for tape backup devices will be removed in a future version of SQL Server.</span></span> <span data-ttu-id="b1d91-105">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b1d91-105">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="b1d91-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b1d91-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b1d91-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="b1d91-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b1d91-108">Security</span><span class="sxs-lookup"><span data-stu-id="b1d91-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b1d91-109">**バックアップ テープまたはバックアップ ファイルの内容を表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="b1d91-109">**To view the content of a backup tape or file, using:**</span></span>  
  
     [<span data-ttu-id="b1d91-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b1d91-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b1d91-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b1d91-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b1d91-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="b1d91-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b1d91-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b1d91-113">Security</span></span>  
 <span data-ttu-id="b1d91-114">セキュリティについては、「[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1d91-114">For information about security, see [RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b1d91-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="b1d91-115">Permissions</span></span>  
 <span data-ttu-id="b1d91-116">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、バックアップ セットやバックアップ デバイスに関する情報の取得には CREATE DATABASE 権限が必要になります。</span><span class="sxs-lookup"><span data-stu-id="b1d91-116">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="b1d91-117">詳細については、「[GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1d91-117">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b1d91-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b1d91-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a><span data-ttu-id="b1d91-119">バックアップ テープまたはバックアップ ファイルの内容を表示するには</span><span class="sxs-lookup"><span data-stu-id="b1d91-119">To view the content of a backup tape or file</span></span>  
  
1.  <span data-ttu-id="b1d91-120">オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="b1d91-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="b1d91-121">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="b1d91-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="b1d91-122">バックアップするデータベースを右クリックし、 **[タスク]** をポイントして、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d91-122">Right-click the database you want to backup, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="b1d91-123">**[データベースのバックアップ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1d91-123">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="b1d91-124">**[全般]** ページの **[バックアップ先]** セクションで、 **[ディスク]** または **[テープ]** のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d91-124">In the **Destination** section of the **General** page, click either **Disk** or **Tape**.</span></span> <span data-ttu-id="b1d91-125">**[バックアップ先]** ボックスの一覧で、ディスク ファイルまたはテープを検索します。</span><span class="sxs-lookup"><span data-stu-id="b1d91-125">In the **Back up to** list box, look for the disk file or tape you want.</span></span>  
  
     <span data-ttu-id="b1d91-126">ディスク ファイルまたはテープがボックスの一覧に表示されない場合、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d91-126">If the disk file or tape is not displayed in the list-box, click **Add**.</span></span> <span data-ttu-id="b1d91-127">ファイル名またはテープ ドライブを選択します。</span><span class="sxs-lookup"><span data-stu-id="b1d91-127">Select a file name or tape drive.</span></span> <span data-ttu-id="b1d91-128">**[バックアップ先]** ボックスの一覧に追加するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d91-128">To add it to the **Back up to** list-box, click **OK**.</span></span>  
  
5.  <span data-ttu-id="b1d91-129">**[バックアップ先]** ボックスの一覧で、表示するディスクまたはテープ ドライブのパスを選択し、 **[コンテンツ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d91-129">In the **Back up to** list-box, select the path of the disk or tape drive you want to view, and click **Contents**.</span></span> <span data-ttu-id="b1d91-130">これにより、 **[デバイス コンテンツ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="b1d91-130">This opens the **Device Contents** dialog box.</span></span>  
  
6.  <span data-ttu-id="b1d91-131">選択したテープまたはファイル上にあるメディア セットやバックアップ セットに関する情報が、右側のペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b1d91-131">The right-hand pane displays information about the media set and backup sets on the selected tape or file.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b1d91-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b1d91-132">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a><span data-ttu-id="b1d91-133">バックアップ テープまたはバックアップ ファイルの内容を表示するには</span><span class="sxs-lookup"><span data-stu-id="b1d91-133">To view the content of a backup tape or file</span></span>  
  
1.  <span data-ttu-id="b1d91-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="b1d91-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b1d91-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1d91-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b1d91-136">[RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="b1d91-136">Use the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span> <span data-ttu-id="b1d91-137">この例は、 `AdventureWorks2012-FullBackup.bak`というファイルに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="b1d91-137">This example returns information about the file named `AdventureWorks2012-FullBackup.bak`.</span></span>  
  
```sql  
USE AdventureWorks2012;  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks2012-FullBackup.bak' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1d91-138">参照</span><span class="sxs-lookup"><span data-stu-id="b1d91-138">See Also</span></span>  
 <span data-ttu-id="b1d91-139">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1d91-139">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="b1d91-140">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1d91-140">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="b1d91-141">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1d91-141">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="b1d91-142">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1d91-142">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="b1d91-143">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1d91-143">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 <span data-ttu-id="b1d91-144">[バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b1d91-144">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="b1d91-145">[ディスク ファイルの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b1d91-145">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 [<span data-ttu-id="b1d91-146">テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b1d91-146">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
