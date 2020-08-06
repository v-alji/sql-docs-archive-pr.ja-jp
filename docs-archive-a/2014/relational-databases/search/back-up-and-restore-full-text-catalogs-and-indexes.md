---
title: フルテキスト カタログとフルテキスト インデックスのバックアップおよび復元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], backing up
- full-text search [SQL Server], back up and restore
- recovery [full-text search]
- backups [SQL Server], full-text indexes
- full-text indexes [SQL Server], restoring
- restore operations [full-text search]
ms.assetid: 6a4080d9-e43f-4b7b-a1da-bebf654c1194
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c0df49c03325da375427c6566799f374fcc9dd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644408"
---
# <a name="back-up-and-restore-full-text-catalogs-and-indexes"></a><span data-ttu-id="78948-102">フルテキスト カタログとフルテキスト インデックスのバックアップおよび復元</span><span class="sxs-lookup"><span data-stu-id="78948-102">Back Up and Restore Full-Text Catalogs and Indexes</span></span>
  <span data-ttu-id="78948-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で作成されたフルテキスト インデックスのバックアップと復元を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="78948-103">This topic explains how to back up and restore full-text indexes created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="78948-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、フルテキスト カタログは論理的概念であり、ファイル グループ内には存在しません。</span><span class="sxs-lookup"><span data-stu-id="78948-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the full-text catalog is a logical concept and does not reside in a filegroup.</span></span> <span data-ttu-id="78948-105">そのため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でフルテキスト カタログをバックアップするには、カタログに属しているフルテキスト インデックスが含まれるファイル グループをすべて特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78948-105">Therefore, to back up a full-text catalog in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must identify every filegroup that contains a full-text index that belongs to the catalog.</span></span> <span data-ttu-id="78948-106">そのうえで、これらのファイルのグループを 1 つずつバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78948-106">Then you must back up those filegroups, one by one.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="78948-107">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースをアップグレードする場合は、フルテキスト カタログをインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="78948-107">It is possible to import full-text catalogs when upgrading a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database.</span></span> <span data-ttu-id="78948-108">インポートした各フルテキスト カタログは、自身のファイル グループのデータベース ファイルです。</span><span class="sxs-lookup"><span data-stu-id="78948-108">Each imported full-text catalog is a database file in its own filegroup.</span></span> <span data-ttu-id="78948-109">インポートされたカタログをバックアップするには、単にそのファイル グループをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="78948-109">To back up an imported catalog, simply back up its filegroup.</span></span> <span data-ttu-id="78948-110">詳細については、 [オンライン ブックの「](https://go.microsoft.com/fwlink/?LinkID=121052)フルテキスト カタログのバックアップと復元 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78948-110">For more information, see [Backing Up and Restoring Full-Text Catalogs](https://go.microsoft.com/fwlink/?LinkID=121052), in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Books Online.</span></span>  
  
##  <a name="backing-up-the-full-text-indexes-of-a-full-text-catalog"></a><a name="backingup"></a> <span data-ttu-id="78948-111">フルテキスト カタログのフルテキスト インデックスのバックアップ</span><span class="sxs-lookup"><span data-stu-id="78948-111">Backing Up the Full-Text Indexes of a Full-Text Catalog</span></span>  
  
###  <a name="finding-the-full-text-indexes-of-a-full-text-catalog"></a><a name="Find_FTIs_of_a_Catalog"></a> <span data-ttu-id="78948-112">フルテキスト カタログのフルテキスト インデックスの検索</span><span class="sxs-lookup"><span data-stu-id="78948-112">Finding the Full-Text Indexes of a Full-Text Catalog</span></span>  
 <span data-ttu-id="78948-113">次の [SELECT](/sql/t-sql/queries/select-transact-sql) ステートメントを使用して、フルテキスト インデックスのプロパティを取得できます。このステートメントでは、 [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql) カタログ ビューおよび [sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql) カタログ ビューから列を選択します。</span><span class="sxs-lookup"><span data-stu-id="78948-113">You can retrieve the properties of the full-text indexes by using the following [SELECT](/sql/t-sql/queries/select-transact-sql) statement, which selects columns from the [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql) and [sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql) catalog views.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @TableID int;  
SET @TableID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product'));  
SELECT object_name(@TableID), i.is_enabled, i.change_tracking_state,   
   i.has_crawl_completed, i.crawl_type, c.name as fulltext_catalog_name   
   FROM sys.fulltext_indexes i, sys.fulltext_catalogs c   
   WHERE i.fulltext_catalog_id = c.fulltext_catalog_id;  
GO  
```  
  

  
###  <a name="finding-the-filegroup-or-file-that-contains-a-full-text-index"></a><a name="Find_FG_of_FTI"></a> <span data-ttu-id="78948-114">フルテキスト インデックスが含まれるファイル グループまたはファイルの検索</span><span class="sxs-lookup"><span data-stu-id="78948-114">Finding the Filegroup or File That Contains a Full-Text Index</span></span>  
 <span data-ttu-id="78948-115">フルテキスト インデックスが作成されたら、次の場所のいずれかに配置されます。</span><span class="sxs-lookup"><span data-stu-id="78948-115">When a full-text index is created, it is placed in one of the following locations:</span></span>  
  
-   <span data-ttu-id="78948-116">ユーザー指定のファイル グループ。</span><span class="sxs-lookup"><span data-stu-id="78948-116">A user-specified filegroup.</span></span>  
  
-   <span data-ttu-id="78948-117">非パーティション テーブルの場合、ベース テーブルまたはベース ビューと同じファイル グループ。</span><span class="sxs-lookup"><span data-stu-id="78948-117">The same filegroup as base table or view, for a nonpartitioned table.</span></span>  
  
-   <span data-ttu-id="78948-118">パーティション テーブルの場合、プライマリ ファイル グループ。</span><span class="sxs-lookup"><span data-stu-id="78948-118">The primary filegroup, for a partitioned table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78948-119">フルテキスト インデックスの作成の詳細については。「[フルテキスト インデックスの作成と管理](create-and-manage-full-text-indexes.md)」および「[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78948-119">For information about creating a full-text index, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) and [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="78948-120">テーブルまたはビューでフルテキスト インデックスのファイル グループを検索するには、次のクエリを使用します。ここで、 *object_name* はテーブルまたはビューの名前です。</span><span class="sxs-lookup"><span data-stu-id="78948-120">To find the filegroup of full-text index on a table or view, use the following query, where *object_name* is the name of the table or view:</span></span>  
  
```  
SELECT name FROM sys.filegroups f, sys.fulltext_indexes i   
   WHERE f.data_space_id = i.data_space_id   
      and i.object_id = object_id('object_name');  
GO  
  
```  
  

  
###  <a name="backing-up-the-filegroups-that-contain-full-text-indexes"></a><a name="Back_up_FTIs_of_FTC"></a> <span data-ttu-id="78948-121">フルテキスト インデックスを含んだファイル グループのバックアップ</span><span class="sxs-lookup"><span data-stu-id="78948-121">Backing Up the Filegroups That Contain Full-Text Indexes</span></span>  
 <span data-ttu-id="78948-122">フルテキスト カタログのインデックスが含まれるファイル グループを検索したら、各ファイル グループをバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78948-122">After you find the filegroups that contain the indexes of a full-text catalog, you need back up each of the filegroups.</span></span> <span data-ttu-id="78948-123">バックアップの処理中に、フルテキスト カタログを削除したり、追加したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="78948-123">During the backup process, full-text catalogs may not be dropped or added.</span></span>  
  
 <span data-ttu-id="78948-124">ファイル グループの最初のバックアップは、ファイルの完全バックアップである必要があります。</span><span class="sxs-lookup"><span data-stu-id="78948-124">The first backup of a filegroup must be a full file backup.</span></span> <span data-ttu-id="78948-125">ファイル グループの完全バックアップを作成した後は、その完全バックアップに基づいたファイルの差分バックアップを 1 つ以上作成して、ファイル グループの変更内容のみをバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="78948-125">After you have created a full file backup for a filegroup, you could back up only the changes in a filegroup by creating a series of one or more differential file backups that are based on the full file backup.</span></span>  
  
 <span data-ttu-id="78948-126">**ファイルおよびファイル グループをバックアップするには**</span><span class="sxs-lookup"><span data-stu-id="78948-126">**To back up files and filegroups**</span></span>  
  
-   [<span data-ttu-id="78948-127">ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="78948-127">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="78948-128">BACKUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="78948-128">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  

  
##  <a name="restoring-a-full-text-index"></a><a name="Restore_FTI"></a> <span data-ttu-id="78948-129">フルテキスト インデックスの復元</span><span class="sxs-lookup"><span data-stu-id="78948-129">Restoring a Full-Text Index</span></span>  
 <span data-ttu-id="78948-130">バックアップされたファイル グループを復元すると、フルテキスト インデックス ファイルがファイル グループのその他のファイルと共に復元されます。</span><span class="sxs-lookup"><span data-stu-id="78948-130">Restoring a backed-up filegroup restores the full-text index files, as well as the other files in the filegroup.</span></span> <span data-ttu-id="78948-131">既定では、ファイル グループはファイル グループがバックアップされたディスク位置に復元されます。</span><span class="sxs-lookup"><span data-stu-id="78948-131">By default, the filegroup is restored to the disk location on which the filegroup was backed up.</span></span>  
  
 <span data-ttu-id="78948-132">バックアップが作成されたときに、フルテキスト インデックスが設定されたテーブルがオンラインで、インデックスを作成中だった場合は、復元後に作成が再開されます。</span><span class="sxs-lookup"><span data-stu-id="78948-132">If a full-text indexed table was online and a population was running when the backup was created, the population is resumed after the restore.</span></span>  
  
 <span data-ttu-id="78948-133">**ファイル グループを復元するには**</span><span class="sxs-lookup"><span data-stu-id="78948-133">**To restore a filegroup**</span></span>  
  
-   [<span data-ttu-id="78948-134">ファイルおよびファイル グループの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="78948-134">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="78948-135">既存のファイルにファイルとファイル グループを復元する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="78948-135">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="78948-136">新しい場所へのファイルの復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="78948-136">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="78948-137">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="78948-137">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  

  
## <a name="see-also"></a><span data-ttu-id="78948-138">参照</span><span class="sxs-lookup"><span data-stu-id="78948-138">See Also</span></span>  
 <span data-ttu-id="78948-139">[サーバー インスタンスでのフルテキスト検索の管理と監視](manage-and-monitor-full-text-search-for-a-server-instance.md) </span><span class="sxs-lookup"><span data-stu-id="78948-139">[Manage and Monitor Full-Text Search for a Server Instance](manage-and-monitor-full-text-search-for-a-server-instance.md) </span></span>  
 [<span data-ttu-id="78948-140">フルテキスト検索のアップグレード</span><span class="sxs-lookup"><span data-stu-id="78948-140">Upgrade Full-Text Search</span></span>](upgrade-full-text-search.md)  
  
  
