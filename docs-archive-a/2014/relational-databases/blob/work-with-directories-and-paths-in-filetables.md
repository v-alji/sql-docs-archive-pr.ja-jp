---
title: FileTable 内のディレクトリとパスの操作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], directories
ms.assetid: f1e45900-bea0-4f6f-924e-c11e1f98ab62
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4641159e894b764cbee4d7f02085f3ceb8e6d87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712030"
---
# <a name="work-with-directories-and-paths-in-filetables"></a><span data-ttu-id="04517-102">FileTable 内のディレクトリとパスの操作</span><span class="sxs-lookup"><span data-stu-id="04517-102">Work with Directories and Paths in FileTables</span></span>
  <span data-ttu-id="04517-103">FileTable 内でファイルが格納されるディレクトリ構造について説明します。</span><span class="sxs-lookup"><span data-stu-id="04517-103">Describes the directory structure in which the files are stored in FileTables.</span></span>  
  
##  <a name="how-to-work-with-directories-and-paths-in-filetables"></a><a name="HowToDirectories"></a> <span data-ttu-id="04517-104">方法:FileTable 内のディレクトリとパスの操作</span><span class="sxs-lookup"><span data-stu-id="04517-104">How To: Work with Directories and Paths in FileTables</span></span>  
 <span data-ttu-id="04517-105">次の 3 つの関数を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で FileTable ディレクトリを操作することができます。</span><span class="sxs-lookup"><span data-stu-id="04517-105">You can use the following 3 functions to work with FileTable directories in [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
|<span data-ttu-id="04517-106">目的</span><span class="sxs-lookup"><span data-stu-id="04517-106">To get this result</span></span>|<span data-ttu-id="04517-107">使用する関数</span><span class="sxs-lookup"><span data-stu-id="04517-107">Use this function</span></span>|  
|------------------------|-----------------------|  
|<span data-ttu-id="04517-108">特定の FileTable または現在のデータベースの、ルート レベルの UNC パスを取得する。</span><span class="sxs-lookup"><span data-stu-id="04517-108">Get the root-level UNC path for a specific FileTable or for the current database.</span></span>|[<span data-ttu-id="04517-109">FileTableRootPath &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04517-109">FileTableRootPath &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/filetablerootpath-transact-sql)|  
|<span data-ttu-id="04517-110">FileTable 内のファイルまたはディレクトリの絶対 UNC パスまたは相対 UNC パスを取得する。</span><span class="sxs-lookup"><span data-stu-id="04517-110">Get an absolute or relative UNC path for a file or directory in a FileTable.</span></span>|[<span data-ttu-id="04517-111">GetFileNamespacePath &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04517-111">GetFileNamespacePath &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)|  
|<span data-ttu-id="04517-112">パスを指定して、FileTable 内の指定されたファイルまたはディレクトリのパス ロケーター ID 値を取得する。</span><span class="sxs-lookup"><span data-stu-id="04517-112">Get the path locator ID value for the specified file or directory in a FileTable, by providing the path.</span></span>|[<span data-ttu-id="04517-113">GetPathLocator &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04517-113">GetPathLocator &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/getpathlocator-transact-sql)|  
  
##  <a name="how-to-use-relative-paths-for-portable-code"></a><a name="BestPracticeRelativePaths"></a> <span data-ttu-id="04517-114">方法:相対パスを使用して移植可能なコードを実現する</span><span class="sxs-lookup"><span data-stu-id="04517-114">How to: Use Relative Paths for Portable Code</span></span>  
 <span data-ttu-id="04517-115">コードとアプリケーションが現在のコンピューターとデータベースから切り離された状態を維持するには、絶対ファイル パスに依存したコードを記述しないでください。</span><span class="sxs-lookup"><span data-stu-id="04517-115">To keep code and applications independent of the current computer and database, avoid writing code that relies on absolute file paths.</span></span> <span data-ttu-id="04517-116">代わりに、以下の例に示すように [FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql) 関数および [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)関数を併用して、実行時にファイルの完全なパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="04517-116">Instead, get the complete path for a file at run time by using the [FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql) and [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)) functions together, as shown in the following example.</span></span> <span data-ttu-id="04517-117">既定では、`GetFileNamespacePath` 関数はデータベースのルート パスにあるファイルの相対パスを返します。</span><span class="sxs-lookup"><span data-stu-id="04517-117">By default, the `GetFileNamespacePath` function returns the relative path of the file under the root path for the database.</span></span>  
  
```sql  
USE database_name;  
DECLARE @root nvarchar(100);  
DECLARE @fullpath nvarchar(1000);  
  
SELECT @root = FileTableRootPath();  
SELECT @fullpath = @root + file_stream.GetFileNamespacePath()  
    FROM filetable_name  
    WHERE name = N'document_name';  
  
PRINT @fullpath;  
GO  
```  
  
##  <a name="important-restrictions"></a><a name="restrictions"></a> <span data-ttu-id="04517-118">重要な制限</span><span class="sxs-lookup"><span data-stu-id="04517-118">Important restrictions</span></span>  
  
###  <a name="nesting-level"></a><a name="nesting"></a> <span data-ttu-id="04517-119">入れ子のレベル</span><span class="sxs-lookup"><span data-stu-id="04517-119">Nesting level</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="04517-120">FileTable ディレクトリ内には、15 レベルを超えるサブディレクトリを格納できません。</span><span class="sxs-lookup"><span data-stu-id="04517-120">You cannot store more than 15 levels of subdirectories in the FileTable directory.</span></span> <span data-ttu-id="04517-121">15 レベルのサブディレクトリを格納した場合、最も深いレベルにファイルを置くことはできません。そのファイルが、さらに深いレベルを表すことになるためです。</span><span class="sxs-lookup"><span data-stu-id="04517-121">When you store 15 levels of subdirectories, then the lowest level cannot contain files, since these files would represent an additional level.</span></span>  
  
###  <a name="length-of-full-path-name"></a><a name="fqnlength"></a> <span data-ttu-id="04517-122">完全なパス名の長さ</span><span class="sxs-lookup"><span data-stu-id="04517-122">Length of full path name</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="04517-123">NTFS ファイル システムは、Windows シェルおよび大部分の Windows API の上限である 260 文字よりも長いパス名をサポートします。</span><span class="sxs-lookup"><span data-stu-id="04517-123">The NTFS file system supports path names that are much longer than the 260-character limit of the Windows shell and most Windows APIs.</span></span> <span data-ttu-id="04517-124">そのため、Transact-SQL を使用して、完全なパス名が 260 文字を超えているために Windows エクスプローラーや他の多くの Windows アプリケーションで表示したり開いたりできないファイルを、FileTable のファイル階層内に作成できます。</span><span class="sxs-lookup"><span data-stu-id="04517-124">Therefore it is possible to create files in the file hierarchy of a FileTable by using Transact-SQL that you cannot view or open with Windows Explorer or many other Windows applications, because the full path name exceeds 260 characters.</span></span> <span data-ttu-id="04517-125">ただし、Transact-SQL を使用してこれらのファイルに引き続きアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="04517-125">However you can continue to access these files by using Transact-SQL.</span></span>  
  
##  <a name="the-full-path-to-an-item-stored-in-a-filetable"></a><a name="fullpath"></a> <span data-ttu-id="04517-126">FileTable に格納されているアイテムへの完全なパス</span><span class="sxs-lookup"><span data-stu-id="04517-126">The full path to an item stored in a FileTable</span></span>  
 <span data-ttu-id="04517-127">FileTable 内のファイルまたはディレクトリへの完全なパスには、次の要素が先頭に付きます。</span><span class="sxs-lookup"><span data-stu-id="04517-127">The full path to a file or directory stored in a FileTable begins with the following elements:</span></span>  
  
1.  <span data-ttu-id="04517-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス レベルでの FILESTREAM ファイル I/O アクセスが有効になっている共有。</span><span class="sxs-lookup"><span data-stu-id="04517-128">The share enabled for FILESTREAM file I/O access at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance level.</span></span>  
  
2.  <span data-ttu-id="04517-129">データベース レベルで指定された **DIRECTORY_NAME** 。</span><span class="sxs-lookup"><span data-stu-id="04517-129">The **DIRECTORY_NAME** specified at the database level.</span></span>  
  
3.  <span data-ttu-id="04517-130">FileTable レベルで指定された **FILETABLE_DIRECTORY** 。</span><span class="sxs-lookup"><span data-stu-id="04517-130">The **FILETABLE_DIRECTORY** specified at the FileTable level.</span></span>  
  
 <span data-ttu-id="04517-131">以上を組み合わせた階層は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="04517-131">The resulting hierarchy looks like this:</span></span>  
  
 `\\<machine>\<instance-level FILESTREAM share>\<database-level directory>\<FileTable directory>\`  
  
 <span data-ttu-id="04517-132">このディレクトリ階層は、FileTable のファイル名前空間のルートを構成します。</span><span class="sxs-lookup"><span data-stu-id="04517-132">This directory hierarchy forms the root of the FileTable's file namespace.</span></span> <span data-ttu-id="04517-133">このディレクトリ階層の下に、FileTable の FILESTREAM データがファイルとして格納されます。また、サブディレクトリとしても格納され、ファイルおよびサブディレクトリを格納することができます。</span><span class="sxs-lookup"><span data-stu-id="04517-133">Under this directory hierarchy, the FILESTREAM data for the FileTable is stored as files, and as subdirectories which can also contain files and subdirectories.</span></span>  
  
 <span data-ttu-id="04517-134">インスタンス レベルの FILESTREAM 共有の下に作成されたディレクトリ階層は仮想ディレクトリ階層であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="04517-134">It is important to keep in mind that the directory hierarchy created under the instance-level FILESTREAM share is a virtual directory hierarchy.</span></span> <span data-ttu-id="04517-135">階層は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納され、NTFS ファイル システム内には物理的に表示されません。</span><span class="sxs-lookup"><span data-stu-id="04517-135">This hierarchy is stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and is not represented physically in the NTFS file system.</span></span> <span data-ttu-id="04517-136">FILESTREAM 共有の下にあるファイルおよびディレクトリ、および FILESTREAM 共有に含まれる FileTables 内のファイルおよびディレクトリにアクセスするすべての操作は、ファイル システムに埋め込まれた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントによってインターセプトされ、処理されます。</span><span class="sxs-lookup"><span data-stu-id="04517-136">All operations that access files and directories under the FILESTREAM share and in the FileTables that it contains are intercepted and handled by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component embedded in the file system.</span></span>  
  
##  <a name="the-semantics-of-the-root-directories-at-the-instance-database-and-filetable-levels"></a><a name="roots"></a> <span data-ttu-id="04517-137">インスタンス レベル、データベース レベル、および FileTable レベルのルート ディレクトリのセマンティクス</span><span class="sxs-lookup"><span data-stu-id="04517-137">The semantics of the root directories at the instance, database, and FileTable levels</span></span>  
 <span data-ttu-id="04517-138">このディレクトリ階層は次のセマンティクスに従います。</span><span class="sxs-lookup"><span data-stu-id="04517-138">This directory hierarchy observes the following semantics:</span></span>  
  
-   <span data-ttu-id="04517-139">インスタンス レベルの FILESTREAM 共有は管理者によって構成され、サーバーのプロパティとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="04517-139">The instance-level FILESTREAM share is configured by an administrator and stored as a property of the server.</span></span> <span data-ttu-id="04517-140">この共有の名前は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="04517-140">You can rename this share by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="04517-141">名前変更の操作は、サーバーを再起動するまで有効になりません。</span><span class="sxs-lookup"><span data-stu-id="04517-141">A renaming operation does not take effect until the server is restarted.</span></span>  
  
-   <span data-ttu-id="04517-142">新しいデータベースを作成した場合、データベース レベルの **DIRECTORY_NAME** は既定で null です。</span><span class="sxs-lookup"><span data-stu-id="04517-142">The database-level **DIRECTORY_NAME** is null by default when you create a new database.</span></span> <span data-ttu-id="04517-143">管理者は **ALTER DATABASE** ステートメントを使用して、この名前を設定または変更することができます。</span><span class="sxs-lookup"><span data-stu-id="04517-143">An administrator can set or change this name by using the **ALTER DATABASE** statement.</span></span> <span data-ttu-id="04517-144">名前は、インスタンス内で一意であることが必要です (大文字と小文字は区別されません)。</span><span class="sxs-lookup"><span data-stu-id="04517-144">The name must be unique (in a case-insensitive comparison) in that instance.</span></span>  
  
-   <span data-ttu-id="04517-145">通常、 **FILETABLE_DIRECTORY** 名は、FileTable を作成する際に **CREATE TABLE** ステートメントの中で指定します。</span><span class="sxs-lookup"><span data-stu-id="04517-145">You typically provide the **FILETABLE_DIRECTORY** name as part of the **CREATE TABLE** statement when you create a FileTable.</span></span> <span data-ttu-id="04517-146">この名前は、 **ALTER TABLE** コマンドを使用して変更することができます。</span><span class="sxs-lookup"><span data-stu-id="04517-146">You can change this name by using the **ALTER TABLE** command.</span></span>  
  
-   <span data-ttu-id="04517-147">ファイル I/O 操作でこれらのルート ディレクトリの名前を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="04517-147">You cannot rename these root directories through file I/O operations.</span></span>  
  
-   <span data-ttu-id="04517-148">排他的なファイル ハンドルを使用してこれらのルート ディレクトリを開くことはできません。</span><span class="sxs-lookup"><span data-stu-id="04517-148">You cannot open these root directories with exclusive file handles.</span></span>  
  
##  <a name="the-is_directory-column-in-the-filetable-schema"></a><a name="is_directory"></a> <span data-ttu-id="04517-149">FileTable スキーマの is_directory 列</span><span class="sxs-lookup"><span data-stu-id="04517-149">The is_directory column in the FileTable schema</span></span>  
 <span data-ttu-id="04517-150">次の表に、 **is_directory** 列と、FileTable の FILESTREAM データを格納する **file_stream** 列との間のやり取りを示します。</span><span class="sxs-lookup"><span data-stu-id="04517-150">The following table describes the interaction between the **is_directory** column and the **file_stream** column that contains the FILESTREAM data in a FileTable.</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="04517-151">*is_directory* **value**</span><span class="sxs-lookup"><span data-stu-id="04517-151">*is_directory* **value**</span></span>|<span data-ttu-id="04517-152">*file_stream* **value**</span><span class="sxs-lookup"><span data-stu-id="04517-152">*file_stream* **value**</span></span>|<span data-ttu-id="04517-153">**動作**</span><span class="sxs-lookup"><span data-stu-id="04517-153">**Behavior**</span></span>|  
|<span data-ttu-id="04517-154">FALSE</span><span class="sxs-lookup"><span data-stu-id="04517-154">FALSE</span></span>|<span data-ttu-id="04517-155">NULL</span><span class="sxs-lookup"><span data-stu-id="04517-155">NULL</span></span>|<span data-ttu-id="04517-156">これは、システム定義の制約によってキャッチされる無効な組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="04517-156">This is an invalid combination that will be caught by a system-defined constraint.</span></span>|  
|<span data-ttu-id="04517-157">FALSE</span><span class="sxs-lookup"><span data-stu-id="04517-157">FALSE</span></span>|\<value>|<span data-ttu-id="04517-158">アイテムはファイルを表します。</span><span class="sxs-lookup"><span data-stu-id="04517-158">The item represents a file.</span></span>|  
|<span data-ttu-id="04517-159">TRUE</span><span class="sxs-lookup"><span data-stu-id="04517-159">TRUE</span></span>|<span data-ttu-id="04517-160">NULL</span><span class="sxs-lookup"><span data-stu-id="04517-160">NULL</span></span>|<span data-ttu-id="04517-161">アイテムはディレクトリを表します。</span><span class="sxs-lookup"><span data-stu-id="04517-161">The item represents a directory.</span></span>|  
|<span data-ttu-id="04517-162">TRUE</span><span class="sxs-lookup"><span data-stu-id="04517-162">TRUE</span></span>|\<value>|<span data-ttu-id="04517-163">これは、システム定義の制約によってキャッチされる無効な組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="04517-163">This is an invalid combination that will be caught by a system-defined constraint.</span></span>|  
  
##  <a name="using-virtual-network-names-vnns-with-alwayson-availability-groups"></a><a name="alwayson"></a> <span data-ttu-id="04517-164">AlwaysOn 可用性グループでの仮想ネットワーク名 (VNN) の使用</span><span class="sxs-lookup"><span data-stu-id="04517-164">Using Virtual Network Names (VNNs) with AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="04517-165">FILESTREAM データまたは FileTable データを格納するデータベースが AlwaysOn 可用性グループに属する場合、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="04517-165">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="04517-166">FILESTREAM および FileTable 関数は、コンピューター名ではなく仮想ネットワーク名 (VNN) のやり取りを行います。</span><span class="sxs-lookup"><span data-stu-id="04517-166">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="04517-167">関数の詳細については、「[Filestream および FileTable 関数 &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04517-167">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="04517-168">ファイル システム API を介した FILESTREAM または FileTable データへのすべてのアクセスでは、コンピューター名ではなく VNN を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04517-168">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span> <span data-ttu-id="04517-169">詳細については、「[FILESTREAM および FileTable と AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04517-169">For more information, see [FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04517-170">参照</span><span class="sxs-lookup"><span data-stu-id="04517-170">See Also</span></span>  
 <span data-ttu-id="04517-171">[FileTable の前提条件の有効化](enable-the-prerequisites-for-filetable.md) </span><span class="sxs-lookup"><span data-stu-id="04517-171">[Enable the Prerequisites for FileTable](enable-the-prerequisites-for-filetable.md) </span></span>  
 <span data-ttu-id="04517-172">[FileTable の作成、変更、および削除](create-alter-and-drop-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="04517-172">[Create, Alter, and Drop FileTables](create-alter-and-drop-filetables.md) </span></span>  
 <span data-ttu-id="04517-173">[Transact SQL を使用した FileTable へのアクセス](access-filetables-with-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="04517-173">[Access FileTables with Transact-SQL](access-filetables-with-transact-sql.md) </span></span>  
 [<span data-ttu-id="04517-174">ファイル I/O API を使用した FileTable へのアクセス</span><span class="sxs-lookup"><span data-stu-id="04517-174">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
  
  
