---
title: データベース スナップショットのスパース ファイルのサイズを表示する方法 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server database snapshots], sparse files
- space [SQL Server], sparse files
- sparse files [SQL Server]
- size [SQL Server], sparse files
- maximum sparse file size
- database snapshots [SQL Server], sparse files
- space [SQL Server], database snapshots
ms.assetid: 1867c5f8-d57c-46d3-933d-3642ab0a8e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: 424399b9915c8e7e26e1076fd2e553aafe06fcf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720001"
---
# <a name="view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql"></a><span data-ttu-id="7f751-102">データベース スナップショットのスパース ファイルのサイズを表示する方法 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7f751-102">View the Size of the Sparse File of a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="7f751-103">このトピックでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ファイルがスパース ファイルであることを確認する方法と、その実サイズおよび最大サイズを調べる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f751-103">This topic describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to verify that a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database file is a sparse file and to find out its actual and maximum sizes.</span></span> <span data-ttu-id="7f751-104">NTFS ファイル システムの機能であるスパース ファイルは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース スナップショットによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="7f751-104">Sparse files, which are a feature of the NTFS file system, are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshots.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f751-105">スパース ファイルは、データベース スナップショットの作成時に CREATE DATABASE ステートメント内のファイル名を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="7f751-105">During database snapshot creation, sparse files are created by using the file names in the CREATE DATABASE statement.</span></span> <span data-ttu-id="7f751-106">これらのファイル名は、 **sys.master_files** の **physical_name** 列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="7f751-106">These file names are stored in **sys.master_files** in the **physical_name** column.</span></span> <span data-ttu-id="7f751-107">ソース データベース内とスナップショット内のいずれであっても、 **sys.database_files** の **physical_name** 列には、ソース データベース ファイルの名前が必ず格納されます。</span><span class="sxs-lookup"><span data-stu-id="7f751-107">In **sys.database_files** (whether in the source database or in a snapshot), the **physical_name** column always contains the names of the source database files.</span></span>  
  
## <a name="verify-that-a-database-file-is-a-sparse-file"></a><span data-ttu-id="7f751-108">データベース ファイルがスパース ファイルであることを確認する</span><span class="sxs-lookup"><span data-stu-id="7f751-108">Verify that a Database File is a Sparse File</span></span>  
  
1.  <span data-ttu-id="7f751-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスで次の操作を実行する:</span><span class="sxs-lookup"><span data-stu-id="7f751-109">On the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
     <span data-ttu-id="7f751-110">データベース スナップショットの **sys.database_files** または **sys.master_files** から **is_sparse**列を選択します。</span><span class="sxs-lookup"><span data-stu-id="7f751-110">Select the **is_sparse** column from either **sys.database_files** in the database snapshot or from **sys.master_files**.</span></span> <span data-ttu-id="7f751-111">次に示すように、この値からファイルがスパース ファイルであるかどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="7f751-111">The value indicates whether the file is a sparse file, as follows:</span></span>  
  
     <span data-ttu-id="7f751-112">1 = ファイルはスパース ファイルです。</span><span class="sxs-lookup"><span data-stu-id="7f751-112">1 = File is a sparse file.</span></span>  
  
     <span data-ttu-id="7f751-113">0 = ファイルはスパース ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="7f751-113">0 = File is not a sparse file.</span></span>  
  
## <a name="find-out-the-actual-size-of-a-sparse-file"></a><span data-ttu-id="7f751-114">スパース ファイルの実際のサイズを調べる</span><span class="sxs-lookup"><span data-stu-id="7f751-114">Find Out the Actual Size of a Sparse File</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f751-115">スパース ファイルは 64 KB 単位で大きくなるので、ディスク上のスパース ファイルのサイズは常に 64 KB の倍数になります。</span><span class="sxs-lookup"><span data-stu-id="7f751-115">Sparse files grow in 64-kilobyte (KB) increments; thus, the size of a sparse file on disk is always a multiple of 64 KB.</span></span>  
  
 <span data-ttu-id="7f751-116">スナップショットの各スパースファイルが現在ディスクで使用しているバイト数を表示するには、 **size_on_disk_bytes** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql)動的管理ビューの [size_on_disk_bytes] 列に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="7f751-116">To view the number of bytes that each sparse file of a snapshot is currently using on disk, query the **size_on_disk_bytes** column of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][sys.dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql) dynamic management view.</span></span>  
  
 <span data-ttu-id="7f751-117">スパース ファイルが使用するディスク領域を表示するには、Microsoft Windows でファイルを右クリックして **[プロパティ]** をクリックし、 **[ディスク上のサイズ]** の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="7f751-117">To view the disk space used by a sparse file, right-click the file in Microsoft Windows, click **Properties**, and look at the **Size on disk** value.</span></span>  
  
## <a name="find-out-the-maximum-size-of-a-sparse-file"></a><span data-ttu-id="7f751-118">スパース ファイルの最大サイズを調べる</span><span class="sxs-lookup"><span data-stu-id="7f751-118">Find Out the Maximum Size of a Sparse File</span></span>  
 <span data-ttu-id="7f751-119">スパース ファイルの最大サイズは、スナップショット作成時点での対応するソース データベース ファイルのサイズです。</span><span class="sxs-lookup"><span data-stu-id="7f751-119">The maximum size to which a sparse can grow is the size of the corresponding source database file at the time of the snapshot creation.</span></span> <span data-ttu-id="7f751-120">このサイズを調べるには、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="7f751-120">To learn this size, you can use one of the following alternatives:</span></span>  
  
-   <span data-ttu-id="7f751-121">Windows コマンド プロンプトを使用する:</span><span class="sxs-lookup"><span data-stu-id="7f751-121">Using Windows Command Prompt:</span></span>  
  
    1.  <span data-ttu-id="7f751-122">Windows の **dir** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7f751-122">Use Windows **dir** commands.</span></span>  
  
    2.  <span data-ttu-id="7f751-123">スパース ファイルを選択し、ファイルの **[プロパティ]** ダイアログ ボックスを開き、 **[サイズ]** の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="7f751-123">Select the sparse file, open the file **Properties** dialog box in Windows, and look at the **Size** value.</span></span>  
  
-   <span data-ttu-id="7f751-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスで次の操作を実行する:</span><span class="sxs-lookup"><span data-stu-id="7f751-124">On the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
     <span data-ttu-id="7f751-125">データベース スナップショットの **sys.database_files** または **sys.master_files** から **size**列を選択します。</span><span class="sxs-lookup"><span data-stu-id="7f751-125">Select the **size** column from either **sys.database_files** in the database snapshot or from **sys.master_files**.</span></span> <span data-ttu-id="7f751-126">**size** 列の値には、スナップショットが使用できる最大領域 (SQL ページ数) が反映されます。この値は、Windows の **[サイズ]** フィールドに相当しますが、ファイル内の SQL ページ数で表されている点が異なります。バイト単位のサイズは次のように表されます。</span><span class="sxs-lookup"><span data-stu-id="7f751-126">The value of **size** column reflects the maximum space, in SQL pages, that the snapshot can ever use; this value is equivalent to the Windows **Size** field, except that it is represented in terms of the number of SQL pages in the file; the size in bytes is:</span></span>  
  
     <span data-ttu-id="7f751-127">( *number_of_pages* \* 8192)</span><span class="sxs-lookup"><span data-stu-id="7f751-127">( *number_of_pages* \* 8192)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f751-128">参照</span><span class="sxs-lookup"><span data-stu-id="7f751-128">See Also</span></span>  
 <span data-ttu-id="7f751-129">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7f751-129">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span></span>  
 <span data-ttu-id="7f751-130">[sys.fn_virtualfilestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f751-130">[sys.fn_virtualfilestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql) </span></span>  
 <span data-ttu-id="7f751-131">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7f751-131">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 [<span data-ttu-id="7f751-132">sys.master_files &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7f751-132">sys.master_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
  
