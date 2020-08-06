---
title: 論理バックアップ デバイスのプロパティと内容の表示 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- displaying backup content
- viewing backup content
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
- backing up databases [SQL Server], properties
- displaying backup properties
- backup devices [SQL Server], viewing information
- viewing backup properties
- database backups [SQL Server], properties
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f2bdf41e3dbda079e3627ff7a7c1c3c78103b728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718284"
---
# <a name="view-the-properties-and-contents-of-a-logical-backup-device-sql-server"></a><span data-ttu-id="87778-102">論理バックアップ デバイスのプロパティと内容の表示 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="87778-102">View the Properties and Contents of a Logical Backup Device (SQL Server)</span></span>
  <span data-ttu-id="87778-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]の論理バックアップ デバイスのプロパティと内容を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="87778-103">This topic describes how to view the properties and contents of a logical backup device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="87778-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="87778-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="87778-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="87778-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="87778-106">Security</span><span class="sxs-lookup"><span data-stu-id="87778-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="87778-107">**論理バックアップ デバイスのプロパティと内容を表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="87778-107">**To view the properties and contents of a logical backup device, using:**</span></span>  
  
     [<span data-ttu-id="87778-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="87778-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="87778-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87778-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="87778-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="87778-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="87778-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="87778-111">Security</span></span>  
 <span data-ttu-id="87778-112">セキュリティについては、「[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87778-112">For information about security, see [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="87778-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="87778-113">Permissions</span></span>  
 <span data-ttu-id="87778-114">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、バックアップ セットやバックアップ デバイスに関する情報の取得には CREATE DATABASE 権限が必要になります。</span><span class="sxs-lookup"><span data-stu-id="87778-114">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="87778-115">詳細については、「[GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87778-115">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="87778-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="87778-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a><span data-ttu-id="87778-117">論理バックアップ デバイスのプロパティと内容を表示するには</span><span class="sxs-lookup"><span data-stu-id="87778-117">To view the properties and contents of a logical backup device</span></span>  
  
1.  <span data-ttu-id="87778-118">オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="87778-118">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="87778-119">**[サーバー オブジェクト]** を展開し、 **[バックアップ デバイス]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="87778-119">Expand **Server Objects**, and expand **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="87778-120">デバイスをクリックし、 **[プロパティ]** を右クリックして **[バックアップ デバイス]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="87778-120">Click the device and right-click **Properties**, which opens the **Backup Device** dialog box.</span></span>  
  
4.  <span data-ttu-id="87778-121">**[全般]** ページにデバイス名とバックアップ先が表示されます。これはテープ ドライブまたはファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="87778-121">The **General** page displays the device name and destination, which is either a tape device or file path.</span></span>  
  
5.  <span data-ttu-id="87778-122">**[ページの選択]** ペインで **[メディアの内容]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87778-122">In the **Select a Page** pane, click **Media Contents**.</span></span>  
  
6.  <span data-ttu-id="87778-123">右側のペインに次のプロパティ パネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="87778-123">The right-hand pane displays in the following properties panels:</span></span>  
  
    -   <span data-ttu-id="87778-124">**メディア**</span><span class="sxs-lookup"><span data-stu-id="87778-124">**Media**</span></span>  
  
         <span data-ttu-id="87778-125">メディアのシーケンス情報 (メディア シーケンス番号、ファミリ シーケンス番号、ミラー識別子など) とメディアの作成日時。</span><span class="sxs-lookup"><span data-stu-id="87778-125">Media sequence information (the media sequence number, the family sequence number, and the mirror identifier, if any) and the media creation date and time.</span></span>  
  
    -   <span data-ttu-id="87778-126">**[メディア セット]**</span><span class="sxs-lookup"><span data-stu-id="87778-126">**Media set**</span></span>  
  
         <span data-ttu-id="87778-127">メディア セットの情報 (メディア セットの名前および説明) とメディア セット内のファミリ数。</span><span class="sxs-lookup"><span data-stu-id="87778-127">Media set information: the media set name and description, if any, and the number of families in the media set.</span></span>  
  
7.  <span data-ttu-id="87778-128">**[バックアップ セット]** グリッドには、メディア セットの内容に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="87778-128">The **Backup sets** grid displays information about the contents of the media set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87778-129">詳細については、「 [[バックアップ デバイス] ([メディアの内容] ページ)](backup-device-media-contents-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87778-129">For more information, see [Media Contents Page](backup-device-media-contents-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="87778-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="87778-130">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a><span data-ttu-id="87778-131">論理バックアップ デバイスのプロパティと内容を表示するには</span><span class="sxs-lookup"><span data-stu-id="87778-131">To view the properties and contents of a logical backup device</span></span>  
  
1.  <span data-ttu-id="87778-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="87778-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="87778-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87778-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="87778-134">[RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="87778-134">Use the [RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) statement.</span></span> <span data-ttu-id="87778-135">この例は、 `AdvWrks2008R2Backup` 論理バックアップ デバイスに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="87778-135">This example returns information about the `AdvWrks2008R2Backup` logical backup device.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="87778-136">参照</span><span class="sxs-lookup"><span data-stu-id="87778-136">See Also</span></span>  
 <span data-ttu-id="87778-137">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87778-137">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="87778-138">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87778-138">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="87778-139">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87778-139">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="87778-140">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87778-140">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="87778-141">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87778-141">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 <span data-ttu-id="87778-142">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87778-142">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 [<span data-ttu-id="87778-143">バックアップ デバイス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="87778-143">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
