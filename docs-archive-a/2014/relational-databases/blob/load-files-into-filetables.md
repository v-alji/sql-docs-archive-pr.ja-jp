---
title: FileTable へのファイルの読み込み | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], migrating files
- FileTables [SQL Server], bulk loading
- FileTables [SQL Server], loading files
ms.assetid: dc842a10-0586-4b0f-9775-5ca0ecc761d9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 43ea31523da2dfa8b387f68ce4f7c7f07868dd6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740057"
---
# <a name="load-files-into-filetables"></a><span data-ttu-id="9133a-102">FileTable へのファイルの読み込み</span><span class="sxs-lookup"><span data-stu-id="9133a-102">Load Files into FileTables</span></span>
  <span data-ttu-id="9133a-103">FileTable にファイルを読み込むまたは移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9133a-103">Describes how to load or migrate files into FileTables.</span></span>  
  
##  <a name="loading-or-migrating-files-into-a-filetable"></a><a name="BasicsLoadNew"></a> <span data-ttu-id="9133a-104">FileTable へのファイルの読み込みまたは移行</span><span class="sxs-lookup"><span data-stu-id="9133a-104">Loading or Migrating Files into a FileTable</span></span>  
 <span data-ttu-id="9133a-105">FileTable へのファイルの読み込みや移行の方法は、ファイルが現在格納されている場所によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9133a-105">The method that you choose for loading or migrating files into a FileTable depends on where the files are currently stored.</span></span>  
  
|<span data-ttu-id="9133a-106">ファイルの現在の場所</span><span class="sxs-lookup"><span data-stu-id="9133a-106">Current location of files</span></span>|<span data-ttu-id="9133a-107">移行のオプション</span><span class="sxs-lookup"><span data-stu-id="9133a-107">Options for migration</span></span>|  
|-------------------------------|---------------------------|  
|<span data-ttu-id="9133a-108">ファイルは現在、ファイル システム内に格納されている。</span><span class="sxs-lookup"><span data-stu-id="9133a-108">Files are currently stored in the file system.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9133a-109">にはファイルに関する情報がありません。</span><span class="sxs-lookup"><span data-stu-id="9133a-109">has no knowledge of the files.</span></span>|<span data-ttu-id="9133a-110">FileTable は Windows ファイル システムにおいてフォルダーとして表示されるため、ファイルの移動またはコピーに使用できる任意の方法で、ファイルを新しい FileTable に簡単に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="9133a-110">Since a FileTable appears as a folder in the Windows file system, you can easily load files into a new FileTable by using any of the available methods for moving or copying files.</span></span> <span data-ttu-id="9133a-111">これらの方法には、Windows エクスプローラー、コマンド ライン オプション (xcopy、robocopy)、およびカスタム スクリプトまたはアプリケーションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9133a-111">These methods include Windows Explorer, command line options including xcopy and robocopy, and custom scripts or applications.</span></span><br /><br /> <span data-ttu-id="9133a-112">既存のフォルダーを FileTable に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="9133a-112">You cannot convert an existing folder to a FileTable.</span></span>|  
|<span data-ttu-id="9133a-113">ファイルは現在、ファイル システム内に格納されている。</span><span class="sxs-lookup"><span data-stu-id="9133a-113">Files are currently stored in the file system.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9133a-114">には、ファイルへのポインターが格納されたメタデータのテーブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9133a-114">contains a table of metadata that contains pointers to the files.</span></span>|<span data-ttu-id="9133a-115">まず、前の項目で示したいずれかの方法を使用して、ファイルを移動またはコピーします。</span><span class="sxs-lookup"><span data-stu-id="9133a-115">The first step is to move or copy the files by using one of the methods mentioned above.</span></span><br /><br /> <span data-ttu-id="9133a-116">次に、ファイルの新しい場所を指すように既存のメタデータのテーブルを更新します。</span><span class="sxs-lookup"><span data-stu-id="9133a-116">The second step is to update the existing table of metadata to point to the new location of the files.</span></span><br /><br /> <span data-ttu-id="9133a-117">詳細については、このトピックの「 [例: ファイルをファイル システムから FileTable に移行する](#HowToMigrateFiles) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9133a-117">For more information, see [Example: Migrating Files from the File System into a FileTable](#HowToMigrateFiles) in this topic.</span></span>|  
  
###  <a name="how-to-load-files-into-a-filetable"></a><a name="HowToLoadNew"></a> <span data-ttu-id="9133a-118">方法:FileTable にファイルを読み込む</span><span class="sxs-lookup"><span data-stu-id="9133a-118">How To: Load Files into a FileTable</span></span>  
 <span data-ttu-id="9133a-119">ファイルを FileTable に読み込むには、次の方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9133a-119">The methods that you can use to load files into a FileTable include the following:</span></span>  
  
-   <span data-ttu-id="9133a-120">Windows エクスプローラーで、基になるフォルダーから新しい FileTable フォルダーにファイルをドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="9133a-120">Drag and drop files from the source folders to the new FileTable folder in Windows Explorer.</span></span>  
  
-   <span data-ttu-id="9133a-121">コマンド プロンプト、バッチ ファイル、またはスクリプトでコマンド ライン オプション (MOVE、COPY、XCOPY、ROBOCOPY など) を使用します。</span><span class="sxs-lookup"><span data-stu-id="9133a-121">Use command line options such as MOVE, COPY, XCOPY, or ROBOCOPY from the command prompt or in a batch file or script.</span></span>  
  
-   <span data-ttu-id="9133a-122">**System.IO** 名前空間のメソッドを使用してファイルの移動またはコピーを実行するカスタム アプリケーションを C# または Visual Basic.NET で作成します。</span><span class="sxs-lookup"><span data-stu-id="9133a-122">Write a custom application in C# or Visual Basic.NET that uses methods from the **System.IO** namespace to move or copy the files.</span></span>  
  
###  <a name="example-migrating-files-from-the-file-system-into-a-filetable"></a><a name="HowToMigrateFiles"></a> <span data-ttu-id="9133a-123">例: ファイルをファイル システムから FileTable に移行する</span><span class="sxs-lookup"><span data-stu-id="9133a-123">Example: Migrating Files from the File System into a FileTable</span></span>  
 <span data-ttu-id="9133a-124">このシナリオでは、ファイルはファイル システムに格納されていて、このファイルへのポインターを含むメタデータのテーブルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に配置されています。</span><span class="sxs-lookup"><span data-stu-id="9133a-124">In this scenario, your files are stored in the file system, and you have a table of metadata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains pointers to the files.</span></span> <span data-ttu-id="9133a-125">ここでは、ファイルを FileTable に移動した後、メタデータ内の各ファイルの元の UNC パスを FileTable の UNC パスに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9133a-125">You want to move the files into a FileTable, and then replace the original UNC path for each file in the metadata with the FileTable UNC path.</span></span> <span data-ttu-id="9133a-126">この操作を行うには、[GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="9133a-126">The [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) function helps you to achieve this goal.</span></span>  
  
 <span data-ttu-id="9133a-127">この例では、 `PhotoMetadata` 写真に関するデータを含む、既存のデータベーステーブルがあるとします。</span><span class="sxs-lookup"><span data-stu-id="9133a-127">For this example, assume that there is an existing database table, `PhotoMetadata`, which contains data about photographs.</span></span> <span data-ttu-id="9133a-128">このテーブルには、.jpg ファイルへの実際の UNC パスを含む `varchar`(512) 型の `UNCPath` 列があります。</span><span class="sxs-lookup"><span data-stu-id="9133a-128">This table has a column `UNCPath` of type `varchar`(512) which contains the actual UNC path to a .jpg file.</span></span>  
  
 <span data-ttu-id="9133a-129">画像ファイルをファイル システムから FileTable に移行するには、次の操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9133a-129">To migrate the image files from the file system into a FileTable, you have to do the following:</span></span>  
  
1.  <span data-ttu-id="9133a-130">ファイルを格納する新しい FileTable を作成します。</span><span class="sxs-lookup"><span data-stu-id="9133a-130">Create a new FileTable to hold the files.</span></span> <span data-ttu-id="9133a-131">この例では、`dbo.PhotoTable` というテーブル名を使用しますが、テーブルを作成するコードは示されていません。</span><span class="sxs-lookup"><span data-stu-id="9133a-131">This example uses the table name, `dbo.PhotoTable`, but does not show the code to create the table.</span></span>  
  
2.  <span data-ttu-id="9133a-132">xcopy または同様のツールを使用して、ディレクトリ構造を保ったまま .jpg ファイルを FileTable のルート ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="9133a-132">Use xcopy or a similar tool to copy the .jpg files, with their directory structure, into the root directory of the FileTable.</span></span>  
  
3.  <span data-ttu-id="9133a-133">次のようなコードを使用して、`PhotoMetadata` テーブル内のメタデータを修正します。</span><span class="sxs-lookup"><span data-stu-id="9133a-133">Fix the metadata in the `PhotoMetadata` table, by using code similar to the following:</span></span>  
  
```sql  
--  Add a path locator column to the PhotoMetadata table.  
ALTER TABLE PhotoMetadata ADD pathlocator hierarchyid;  
  
-- Get the root path of the Photo directory on the File Server.  
DECLARE @UNCPathRoot varchar(100) = '\\RemoteShare\Photographs';  
  
-- Get the root path of the FileTable.  
DECLARE @FileTableRoot varchar(1000);  
SELECT @FileTableRoot = FileTableRootPath('dbo.PhotoTable');  
  
-- Update the PhotoMetadata table.  
  
-- Replace the File Server UNC path with the FileTable path.  
UPDATE PhotoMetadata  
    SET UNCPath = REPLACE(UNCPath, @UNCPathRoot, @FileTableRoot);  
  
-- Update the pathlocator column to contain the pathlocator IDs from the FileTable.  
UPDATE PhotoMetadata  
    SET pathlocator = GetPathLocator(UNCPath);  
```  
  
##  <a name="bulk-loading-files-into-a-filetable"></a><a name="BasicsBulkLoad"></a> <span data-ttu-id="9133a-134">FileTable へのファイルの一括読み込み</span><span class="sxs-lookup"><span data-stu-id="9133a-134">Bulk Loading Files into a FileTable</span></span>  
 <span data-ttu-id="9133a-135">FileTable の一括操作は通常のテーブルの動作と同じですが、次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="9133a-135">A FileTable behaves like a normal table for bulk operations, with the following qualifications.</span></span>  
  
 <span data-ttu-id="9133a-136">FileTable には、ファイル/ディレクトリ名前空間の整合性を確保するためにシステムによって定義された制約があります。</span><span class="sxs-lookup"><span data-stu-id="9133a-136">A FileTable has system-defined constraints which ensure that the integrity of the file and directory namespace is maintained.</span></span> <span data-ttu-id="9133a-137">これらの制約は、FileTable に一括で読み込まれるデータに対しても検証されます。</span><span class="sxs-lookup"><span data-stu-id="9133a-137">These constraints have to be verified on the data bulk loaded into the FileTable.</span></span> <span data-ttu-id="9133a-138">一部の一括挿入操作ではテーブル制約の無視が許可されるため、次の要件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9133a-138">Since some bulk insert operations allow table constraints to be ignored, the following requirements are enforced.</span></span>  
  
-   <span data-ttu-id="9133a-139">制約が適用される一括読み込み操作は、FileTable でも他のテーブルに対する操作と同じように実行できます。</span><span class="sxs-lookup"><span data-stu-id="9133a-139">Bulk loading operations that enforce constraints can be run against a FileTable as against any other table.</span></span> <span data-ttu-id="9133a-140">このカテゴリには以下の操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9133a-140">This category includes the following operations:</span></span>  
  
    -   <span data-ttu-id="9133a-141">CHECK_CONSTRAINTS 句を含む bcp</span><span class="sxs-lookup"><span data-stu-id="9133a-141">bcp with CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="9133a-142">CHECK_CONSTRAINTS 句を含む BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="9133a-142">BULK INSERT with CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="9133a-143">INSERT INTO ... IGNORE_CONSTRAINTS 句を含まない SELECT \* FROM OPENROWSET(BULK ...)。</span><span class="sxs-lookup"><span data-stu-id="9133a-143">INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...) without IGNORE_CONSTRAINTS clause.</span></span>  
  
-   <span data-ttu-id="9133a-144">FileTable のシステム定義の制約が無効化されない限り、制約が適用されない一括読み込み操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="9133a-144">Bulk loading operations that do not enforce constraints fail unless the FileTable system-defined constraints have been disabled.</span></span> <span data-ttu-id="9133a-145">このカテゴリには以下の操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9133a-145">This category includes the following operations:</span></span>  
  
    -   <span data-ttu-id="9133a-146">CHECK_CONSTRAINTS 句を含まない bcp</span><span class="sxs-lookup"><span data-stu-id="9133a-146">bcp without CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="9133a-147">CHECK_CONSTRAINTS 句を含まない BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="9133a-147">BULK INSERT without CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="9133a-148">INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...) (IGNORE_CONSTRAINTS 句を含む)。</span><span class="sxs-lookup"><span data-stu-id="9133a-148">INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...) with IGNORE_CONSTRAINTS clause.</span></span>  
  
###  <a name="how-to-bulk-load-files-into-a-filetable"></a><a name="HowToBulkLoad"></a> <span data-ttu-id="9133a-149">方法:FileTable へのファイルの一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="9133a-149">How To: Bulk Load Files into a FileTable</span></span>  
 <span data-ttu-id="9133a-150">ファイルを FileTable に一括読み込みするには、次の方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9133a-150">You can use various methods to bulk load files into a FileTable:</span></span>  
  
-   <span data-ttu-id="9133a-151">**bcp**</span><span class="sxs-lookup"><span data-stu-id="9133a-151">**bcp**</span></span>  
  
    -   <span data-ttu-id="9133a-152">**CHECK_CONSTRAINTS** 句を指定して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9133a-152">Call with the **CHECK_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="9133a-153">FileTable 名前空間を無効にし、 **CHECK_CONSTRAINTS** 句を指定せずに呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9133a-153">Disable the FileTable namespace and call without the **CHECK_CONSTRAINTS** clause.</span></span> <span data-ttu-id="9133a-154">次に、FileTable 名前空間を再有効化します。</span><span class="sxs-lookup"><span data-stu-id="9133a-154">Then re-enable the FileTable namespace.</span></span>  
  
-   <span data-ttu-id="9133a-155">**BULK INSERT**</span><span class="sxs-lookup"><span data-stu-id="9133a-155">**BULK INSERT**</span></span>  
  
    -   <span data-ttu-id="9133a-156">**CHECK_CONSTRAINTS** 句を指定して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9133a-156">Call with the **CHECK_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="9133a-157">FileTable 名前空間を無効にし、 **CHECK_CONSTRAINTS** 句を指定せずに呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9133a-157">Disable the FileTable namespace and call without the **CHECK_CONSTRAINTS** clause.</span></span> <span data-ttu-id="9133a-158">次に、FileTable 名前空間を再有効化します。</span><span class="sxs-lookup"><span data-stu-id="9133a-158">Then re-enable the FileTable namespace.</span></span>  
  
-   <span data-ttu-id="9133a-159">**INSERT INTO ...SELECT \* FROM OPENROWSET(BULK ...)**</span><span class="sxs-lookup"><span data-stu-id="9133a-159">**INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...)**</span></span>  
  
    -   <span data-ttu-id="9133a-160">**IGNORE_CONSTRAINTS** 句を指定して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9133a-160">Call with the **IGNORE_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="9133a-161">FileTable 名前空間を無効にし、 **IGNORE_CONSTRAINTS** 句を指定せずに呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9133a-161">Disable the FileTable namespace and call without the **IGNORE_CONSTRAINTS** clause.</span></span> <span data-ttu-id="9133a-162">次に、FileTable 名前空間を再有効化します。</span><span class="sxs-lookup"><span data-stu-id="9133a-162">Then re-enable the FileTable namespace.</span></span>  
  
 <span data-ttu-id="9133a-163">FileTable 制約の無効化の詳細については、「 [FileTable の管理](manage-filetables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9133a-163">For information about disabling the FileTable constraints, see [Manage FileTables](manage-filetables.md).</span></span>  
  
###  <a name="how-to-disable-filetable-constraints-for-bulk-loading"></a><a name="disabling"></a> <span data-ttu-id="9133a-164">方法:一括読み込みのための FileTable の制約を無効化する</span><span class="sxs-lookup"><span data-stu-id="9133a-164">How To: Disable FileTable Constraints for Bulk Loading</span></span>  
 <span data-ttu-id="9133a-165">システム定義の制約を一時的に無効化すると、制約の適用というオーバーヘッドなしで、FileTable へのファイルの一括読み込みを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9133a-165">To bulk load files into a FileTable without the overhead of enforcing the system-defined constraints, you can temporarily disable the constraints.</span></span> <span data-ttu-id="9133a-166">詳細については、「 [FileTable の管理](manage-filetables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9133a-166">For more information, see [Manage FileTables](manage-filetables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9133a-167">参照</span><span class="sxs-lookup"><span data-stu-id="9133a-167">See Also</span></span>  
 <span data-ttu-id="9133a-168">[Transact SQL を使用した FileTable へのアクセス](access-filetables-with-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="9133a-168">[Access FileTables with Transact-SQL](access-filetables-with-transact-sql.md) </span></span>  
 [<span data-ttu-id="9133a-169">ファイル I/O API を使用した FileTable へのアクセス</span><span class="sxs-lookup"><span data-stu-id="9133a-169">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
  
  
