---
title: データベース ファイルとファイル グループ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], files
- filegroups [SQL Server]
- transaction logs [SQL Server], about
- transaction logs [SQL Server], files
- .mdf files
- data files [SQL Server]
- default filegroups
- files [SQL Server], about files and filegroups
- secondary files [SQL Server]
- log files [SQL Server]
- .ndf files
- files [SQL Server]
- .ldf files
- database files [SQL Server]
- databases [SQL Server], filegroups
- filegroups [SQL Server], types
- primary filegroups [SQL Server]
- user-defined filegroups [SQL Server]
- filegroups [SQL Server], about filegroups
- primary files [SQL Server]
- file types [SQL Server]
ms.assetid: 9ca11918-480d-4838-9198-cec221ef6ad0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91e22e536a91878609feedf2977ffa7d78a54d61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640078"
---
# <a name="database-files-and-filegroups"></a><span data-ttu-id="92782-102">データベース ファイルとファイル グループ</span><span class="sxs-lookup"><span data-stu-id="92782-102">Database Files and Filegroups</span></span>
  <span data-ttu-id="92782-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各データベースには、データ ファイルとログ ファイルという少なくとも 2 つのオペレーティング システム ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="92782-103">At a minimum, every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database has two operating system files: a data file and a log file.</span></span> <span data-ttu-id="92782-104">データ ファイルには、テーブル、インデックス、ストアド プロシージャ、およびビューなどのデータおよびオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="92782-104">Data files contain data and objects such as tables, indexes, stored procedures, and views.</span></span> <span data-ttu-id="92782-105">ログ ファイルには、データベース内のすべてのトランザクションを復旧するために必要な情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="92782-105">Log files contain the information that is required to recover all transactions in the database.</span></span> <span data-ttu-id="92782-106">データ ファイルは、割り当てと管理の目的でファイル グループにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="92782-106">Data files can be grouped together in filegroups for allocation and administration purposes.</span></span>  
  
## <a name="database-files"></a><span data-ttu-id="92782-107">データベース ファイル</span><span class="sxs-lookup"><span data-stu-id="92782-107">Database Files</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92782-108">データベースには、次の表で示すように 3 種類のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="92782-108">databases have three types of files, as shown in the following table.</span></span>  
  
|<span data-ttu-id="92782-109">ファイル</span><span class="sxs-lookup"><span data-stu-id="92782-109">File</span></span>|<span data-ttu-id="92782-110">説明</span><span class="sxs-lookup"><span data-stu-id="92782-110">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="92782-111">プライマリ</span><span class="sxs-lookup"><span data-stu-id="92782-111">Primary</span></span>|<span data-ttu-id="92782-112">プライマリ データ ファイルにはデータベースの起動情報が含まれており、データベース内の他のファイルを指し示します。</span><span class="sxs-lookup"><span data-stu-id="92782-112">The primary data file contains the startup information for the database and points to the other files in the database.</span></span> <span data-ttu-id="92782-113">ユーザー データおよびオブジェクトは、このファイルまたはセカンダリ データ ファイルに格納できます。</span><span class="sxs-lookup"><span data-stu-id="92782-113">User data and objects can be stored in this file or in secondary data files.</span></span> <span data-ttu-id="92782-114">各データベースには 1 つのプライマリ データ ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="92782-114">Every database has one primary data file.</span></span> <span data-ttu-id="92782-115">プライマリ データ ファイルに推奨されるファイル名拡張子は .mdf です。</span><span class="sxs-lookup"><span data-stu-id="92782-115">The recommended file name extension for primary data files is .mdf.</span></span>|  
|<span data-ttu-id="92782-116">セカンダリ</span><span class="sxs-lookup"><span data-stu-id="92782-116">Secondary</span></span>|<span data-ttu-id="92782-117">セカンダリ データ ファイルは省略可能です。また、ユーザー定義であり、ユーザー データが格納されます。</span><span class="sxs-lookup"><span data-stu-id="92782-117">Secondary data files are optional, are user-defined, and store user data.</span></span> <span data-ttu-id="92782-118">セカンダリ ファイルを使用すると、各ファイルを異なるディスク ドライブに配置することにより、複数のディスクにデータを分散できます。</span><span class="sxs-lookup"><span data-stu-id="92782-118">Secondary files can be used to spread data across multiple disks by putting each file on a different disk drive.</span></span> <span data-ttu-id="92782-119">また、データベースが 1 つの Windows ファイルの最大サイズを超えた場合には、セカンダリ データ ファイルを使用してデータベースを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="92782-119">Additionally, if a database exceeds the maximum size for a single Windows file, you can use secondary data files so the database can continue to grow.</span></span><br /><br /> <span data-ttu-id="92782-120">セカンダリ データ ファイルに推奨されるファイル名拡張子は .ndf です。</span><span class="sxs-lookup"><span data-stu-id="92782-120">The recommended file name extension for secondary data files is .ndf.</span></span>|  
|<span data-ttu-id="92782-121">トランザクション ログ</span><span class="sxs-lookup"><span data-stu-id="92782-121">Transaction Log</span></span>|<span data-ttu-id="92782-122">トランザクション ログ ファイルには、データベースの復旧に使用されるログ情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="92782-122">The transaction log files hold the log information that is used to recover the database.</span></span> <span data-ttu-id="92782-123">1 つのデータベースにトランザクション ログ ファイルが少なくとも 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="92782-123">There must be at least one log file for each database.</span></span> <span data-ttu-id="92782-124">トランザクション ログに推奨されるファイル名拡張子は .ldf です。</span><span class="sxs-lookup"><span data-stu-id="92782-124">The recommended file name extension for transaction logs is .ldf.</span></span>|  
  
 <span data-ttu-id="92782-125">たとえば、データとオブジェクトをすべて格納するプライマリ ファイルを 1 つとトランザクション ログ情報を格納するログ ファイルを 1 つ含む **Sales** という単純なデータベースを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="92782-125">For example, a simple database named **Sales** can be created that includes one primary file that contains all data and objects and a log file that contains the transaction log information.</span></span> <span data-ttu-id="92782-126">または、プライマリ ファイルを 1 つとセカンダリ ファイルを 5 つ含む **Orders** というより複雑なデータベースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="92782-126">Alternatively, a more complex database named **Orders** can be created that includes one primary file and five secondary files.</span></span> <span data-ttu-id="92782-127">データベース内のデータとオブジェクトは 6 つすべてのファイルに分散され、4 つのログ ファイルにトランザクション ログ情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="92782-127">The data and objects within the database spread across all six files, and the four log files contain the transaction log information.</span></span>  
  
 <span data-ttu-id="92782-128">既定では、データとトランザクション ログは同一のドライブおよびパス上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="92782-128">By default, the data and transaction logs are put on the same drive and path.</span></span> <span data-ttu-id="92782-129">これは、単一のディスク システムを処理するために行われますが、</span><span class="sxs-lookup"><span data-stu-id="92782-129">This is done to handle single-disk systems.</span></span> <span data-ttu-id="92782-130">実稼働環境では最適ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="92782-130">However, this may not be optimal for production environments.</span></span> <span data-ttu-id="92782-131">そのため、データとログ ファイルは別のディスクに配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="92782-131">We recommend that you put data and log files on separate disks.</span></span>  
  
## <a name="filegroups"></a><span data-ttu-id="92782-132">ファイル グループ</span><span class="sxs-lookup"><span data-stu-id="92782-132">Filegroups</span></span>  
 <span data-ttu-id="92782-133">各データベースには、1 つのプライマリ ファイル グループがあります。</span><span class="sxs-lookup"><span data-stu-id="92782-133">Every database has a primary filegroup.</span></span> <span data-ttu-id="92782-134">プライマリ ファイル グループには、プライマリ データ ファイル、および他のファイル グループに配置されていないセカンダリ ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="92782-134">This filegroup contains the primary data file and any secondary files that are not put into other filegroups.</span></span> <span data-ttu-id="92782-135">ユーザー定義のファイル グループを作成して、データベースの管理、データの割り当て、および配置をしやすくするために、データ ファイルをグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="92782-135">User-defined filegroups can be created to group data files together for administrative, data allocation, and placement purposes.</span></span>  
  
 <span data-ttu-id="92782-136">たとえば、3 つのディスク ドライブ上に 1 つずつ、合計 3 つのファイル (Data1.ndf、Data2.ndf、Data3.ndf) を作成し、これらのファイルをファイル グループ **fgroup1**にまとめます。</span><span class="sxs-lookup"><span data-stu-id="92782-136">For example, three files, Data1.ndf, Data2.ndf, and Data3.ndf, can be created on three disk drives, respectively, and assigned to the filegroup **fgroup1**.</span></span> <span data-ttu-id="92782-137">次に、ファイル グループ **fgroup1**上にテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="92782-137">A table can then be created specifically on the filegroup **fgroup1**.</span></span> <span data-ttu-id="92782-138">このテーブル内にあるデータに対するクエリが 3 つのディスクにわたって分散されるため、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="92782-138">Queries for data from the table will be spread across the three disks; this will improve performance.</span></span> <span data-ttu-id="92782-139">RAID (Redundant Array of Independent Disks) ストライプ セットにファイルを 1 つ作成しても、同じくらいパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="92782-139">The same performance improvement can be accomplished by using a single file created on a RAID (redundant array of independent disks) stripe set.</span></span> <span data-ttu-id="92782-140">ただし、ファイルとファイル グループを使用すれば、新しいファイルを新しいディスクに容易に追加できます。</span><span class="sxs-lookup"><span data-stu-id="92782-140">However, files and filegroups let you easily add new files to new disks.</span></span>  
  
 <span data-ttu-id="92782-141">すべてのデータ ファイルは、次の表に一覧表示されているファイル グループに格納されます。</span><span class="sxs-lookup"><span data-stu-id="92782-141">All data files are stored in the filegroups listed in the following table.</span></span>  
  
|<span data-ttu-id="92782-142">[ファイル グループ]</span><span class="sxs-lookup"><span data-stu-id="92782-142">Filegroup</span></span>|<span data-ttu-id="92782-143">説明</span><span class="sxs-lookup"><span data-stu-id="92782-143">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92782-144">プライマリ</span><span class="sxs-lookup"><span data-stu-id="92782-144">Primary</span></span>|<span data-ttu-id="92782-145">プライマリ ファイルが含まれているファイル グループ。</span><span class="sxs-lookup"><span data-stu-id="92782-145">The filegroup that contains the primary file.</span></span> <span data-ttu-id="92782-146">すべてのシステム テーブルがプライマリ ファイル グループに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="92782-146">All system tables are allocated to the primary filegroup.</span></span>|  
|<span data-ttu-id="92782-147">ユーザー定義</span><span class="sxs-lookup"><span data-stu-id="92782-147">User-defined</span></span>|<span data-ttu-id="92782-148">ユーザーがデータベースを最初に作成したとき、または後で変更したときに、ユーザーが特別に作成したファイル グループ。</span><span class="sxs-lookup"><span data-stu-id="92782-148">Any filegroup that is specifically created by the user when the user first creates or later modifies the database.</span></span>|  
  
### <a name="default-filegroup"></a><span data-ttu-id="92782-149">既定のファイル グループ</span><span class="sxs-lookup"><span data-stu-id="92782-149">Default Filegroup</span></span>  
 <span data-ttu-id="92782-150">所属させるファイル グループを指定せずにデータベース内にオブジェクトを作成すると、そのオブジェクトは既定のファイル グループに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="92782-150">When objects are created in the database without specifying which filegroup they belong to, they are assigned to the default filegroup.</span></span> <span data-ttu-id="92782-151">どのような場合でも、必ず 1 つのファイル グループが既定のファイル グループとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="92782-151">At any time, exactly one filegroup is designated as the default filegroup.</span></span> <span data-ttu-id="92782-152">既定のファイル グループ内のファイルは、他のファイル グループに割り当てられない新しいオブジェクトを十分に格納できる大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="92782-152">The files in the default filegroup must be large enough to hold any new objects not allocated to other filegroups.</span></span>  
  
 <span data-ttu-id="92782-153">PRIMARY ファイル グループは、ALTER DATABASE ステートメントを使用して変更しない限り、既定のファイル グループです。</span><span class="sxs-lookup"><span data-stu-id="92782-153">The PRIMARY filegroup is the default filegroup unless it is changed by using the ALTER DATABASE statement.</span></span> <span data-ttu-id="92782-154">システム オブジェクトとシステム テーブルは、変更後の既定のファイル グループではなく、引き続き PRIMARY ファイル グループに格納されます。</span><span class="sxs-lookup"><span data-stu-id="92782-154">Allocation for the system objects and tables remains within the PRIMARY filegroup, not the new default filegroup.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="92782-155">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="92782-155">Related Content</span></span>  
 [<span data-ttu-id="92782-156">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92782-156">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
 [<span data-ttu-id="92782-157">ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="92782-157">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
 [<span data-ttu-id="92782-158">データベースのデタッチとアタッチ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="92782-158">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
