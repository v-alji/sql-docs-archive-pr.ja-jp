---
title: バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], viewing backup sets
- viewing backup set information
- backup sets [SQL Server], viewing files in
- displaying backup set information
- transaction log backups [SQL Server], viewing backup sets
- backing up [SQL Server], viewing backup sets
ms.assetid: abb6420c-f809-426e-aeb4-d0a74989cf39
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7dbcb14a658b49aba6f5f2ebe3425a2ab5759efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718302"
---
# <a name="view-the-data-and-log-files-in-a-backup-set-sql-server"></a><span data-ttu-id="28a5e-102">バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="28a5e-102">View the Data and Log Files in a Backup Set (SQL Server)</span></span>
  <span data-ttu-id="28a5e-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、バックアップ セットに含まれているデータ ファイルおよびログ ファイルを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28a5e-103">This topic describes how to view the data and log files in a backup set in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="28a5e-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="28a5e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="28a5e-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="28a5e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="28a5e-106">Security</span><span class="sxs-lookup"><span data-stu-id="28a5e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="28a5e-107">**バックアップ セットに含まれているデータ ファイルおよびログ ファイルを表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="28a5e-107">**To view the data and log files in a backup set, using:**</span></span>  
  
     [<span data-ttu-id="28a5e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="28a5e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="28a5e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="28a5e-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="28a5e-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="28a5e-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="28a5e-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="28a5e-111">Security</span></span>  
 <span data-ttu-id="28a5e-112">セキュリティについては、「[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a5e-112">For information about security, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="28a5e-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="28a5e-113">Permissions</span></span>  
 <span data-ttu-id="28a5e-114">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、バックアップ セットやバックアップ デバイスに関する情報の取得には CREATE DATABASE 権限が必要になります。</span><span class="sxs-lookup"><span data-stu-id="28a5e-114">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="28a5e-115">詳細については、「[GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a5e-115">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="28a5e-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="28a5e-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a><span data-ttu-id="28a5e-117">バックアップ セットに含まれているデータ ファイルおよびログ ファイルを表示するには</span><span class="sxs-lookup"><span data-stu-id="28a5e-117">To view the data and log files in a backup set</span></span>  
  
1.  <span data-ttu-id="28a5e-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]で適切な オブジェクト エクスプローラーのインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="28a5e-118">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="28a5e-119">**[データベース]** を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="28a5e-119">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="28a5e-120">データベースを右クリックし、 **[プロパティ]** をクリックすると、 **[データベースのプロパティ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="28a5e-120">Right-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="28a5e-121">**[ページの選択]** ペインの **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28a5e-121">In the **Select a Page** pane, click **Files**.</span></span>  
  
5.  <span data-ttu-id="28a5e-122">**[データベース ファイル]** グリッドでデータとログ ファイルの一覧およびプロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="28a5e-122">Look in the **Database files** grid for a list of the data and log files and their properties.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="28a5e-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="28a5e-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a><span data-ttu-id="28a5e-124">バックアップ セットに含まれているデータ ファイルおよびログ ファイルを表示するには</span><span class="sxs-lookup"><span data-stu-id="28a5e-124">To view the data and log files in a backup set</span></span>  
  
1.  <span data-ttu-id="28a5e-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="28a5e-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="28a5e-126">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28a5e-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="28a5e-127">[RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="28a5e-127">Use the [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) statement.</span></span> <span data-ttu-id="28a5e-128">この例は、`FILE=2`バックアップ デバイスで 2 番目のバックアップ セット ( `AdventureWorksBackups` ) に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="28a5e-128">This example returns information about the second backup set (`FILE=2`) on the `AdventureWorksBackups` backup device.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="28a5e-129">参照</span><span class="sxs-lookup"><span data-stu-id="28a5e-129">See Also</span></span>  
 <span data-ttu-id="28a5e-130">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="28a5e-130">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="28a5e-131">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="28a5e-131">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="28a5e-132">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="28a5e-132">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="28a5e-133">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="28a5e-133">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="28a5e-134">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="28a5e-134">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 [<span data-ttu-id="28a5e-135">バックアップ デバイス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="28a5e-135">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
