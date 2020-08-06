---
title: Transact SQL を使用した FileTable へのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], accessing files with T-SQL
ms.assetid: 3c4a5ffb-c521-4696-99cb-2b03cffc9c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c47751ef34747e1b3742accf5040846ecde074f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736408"
---
# <a name="access-filetables-with-transact-sql"></a><span data-ttu-id="00fcb-102">Transact SQL を使用した FileTable へのアクセス</span><span class="sxs-lookup"><span data-stu-id="00fcb-102">Access FileTables with Transact-SQL</span></span>
  <span data-ttu-id="00fcb-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] データ操作言語 (DML) コマンドによる FileTable の操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="00fcb-103">Describes how [!INCLUDE[tsql](../../includes/tsql-md.md)] data manipulation language (DML) commands work with FileTables.</span></span>  
  
##  <a name="insert-operations-on-filetables"></a><a name="BasicsInsert"></a> <span data-ttu-id="00fcb-104">FileTable での INSERT 操作</span><span class="sxs-lookup"><span data-stu-id="00fcb-104">INSERT Operations on FileTables</span></span>  
 <span data-ttu-id="00fcb-105">FileTable で **INSERT** 操作を行う場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="00fcb-105">The following considerations apply to **INSERT** Operations on FileTables:</span></span>  
  
-   <span data-ttu-id="00fcb-106">ファイル属性のすべての列には NOT NULL 制約があります。</span><span class="sxs-lookup"><span data-stu-id="00fcb-106">All the file attribute columns have NOT NULL constraints.</span></span> <span data-ttu-id="00fcb-107">明示的に値が設定されなかった場合は、適切な既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-107">If values are not explicitly set, then appropriate default values are supplied.</span></span>  
  
-   <span data-ttu-id="00fcb-108">INSERT ステートメントで **name**、 **path_locator**、 **parent_path_locator**、またはファイル属性を設定する場合、システム定義の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-108">System-defined constraints are enforced if the INSERT statement sets the **name**, **path_locator**, **parent_path_locator**, or file attributes.</span></span>  
  
-   <span data-ttu-id="00fcb-109">アプリケーションは、[GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) 関数にファイル システム パスを渡すことで、ファイルまたはディレクトリの **path_locator** を取得できます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-109">The application can obtain the **path_locator** for a file or directory by providing the file system path to the [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) function.</span></span>  
  
##  <a name="update-operations-on-filetables"></a><a name="BasicsUpdate"></a> <span data-ttu-id="00fcb-110">FileTable での UPDATE 操作</span><span class="sxs-lookup"><span data-stu-id="00fcb-110">UPDATE Operations on FileTables</span></span>  
 <span data-ttu-id="00fcb-111">FileTable で **UPDATE** 操作を行う場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="00fcb-111">The following considerations apply to **UPDATE** operations on FileTables:</span></span>  
  
-   <span data-ttu-id="00fcb-112">すべてのユーザー定義データの更新が許可されます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-112">Updates to any user-defined data are allowed.</span></span>  
  
-   <span data-ttu-id="00fcb-113">INSERT ステートメントで **name**、 **path_locator**、 **parent_path_locator**、またはファイル属性を設定する場合、システム定義の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-113">System-defined constraints are enforced if the INSERT statement sets the **name**, **path_locator**, **parent_path_locator**, or file attributes.</span></span>  
  
-   <span data-ttu-id="00fcb-114">**file_stream** 列の FILESTREAM データは、他の列 (timestamps を含む) に一切影響を及ぼさずに更新することができます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-114">Updates can be made to the FILESTREAM data in the **file_stream** column without affecting any of the other columns, including the timestamps.</span></span>  
  
##  <a name="delete-operations-on-filetables"></a><a name="BasicsDelete"></a> <span data-ttu-id="00fcb-115">FileTable での DELETE 操作</span><span class="sxs-lookup"><span data-stu-id="00fcb-115">DELETE Operations on FileTables</span></span>  
 <span data-ttu-id="00fcb-116">FileTable で **DELETE** 操作を行う場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="00fcb-116">The following considerations apply to **DELETE** operations on FileTables:</span></span>  
  
-   <span data-ttu-id="00fcb-117">行を削除すると、対応するファイルまたはディレクトリがファイル システムから削除されます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-117">Deleting a row also removes the corresponding file or directory from the file system.</span></span>  
  
-   <span data-ttu-id="00fcb-118">対応するディレクトリに他のファイルまたはディレクトリが存在する場合、行の削除は失敗します。</span><span class="sxs-lookup"><span data-stu-id="00fcb-118">Deleting a row fails if the row corresponds to a directory that contains other files or directories.</span></span>  
  
##  <a name="constraints-that-are-enforced-for-dml-operations-on-filetables"></a><a name="BasicsConstraints"></a> <span data-ttu-id="00fcb-119">DML での FileTable の操作の制約</span><span class="sxs-lookup"><span data-stu-id="00fcb-119">Constraints That Are Enforced for DML Operations on FileTables</span></span>  
 <span data-ttu-id="00fcb-120">システム定義の制約は、ファイル名前空間階層構造の整合性が DML アクションによって損なわれることのないように制御します。</span><span class="sxs-lookup"><span data-stu-id="00fcb-120">System-defined constraints ensure that DML actions do not compromise the integrity of the file namespace hierarchy.</span></span> <span data-ttu-id="00fcb-121">適用される制約は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="00fcb-121">The constraints that are enforced include the following:</span></span>  
  
-   <span data-ttu-id="00fcb-122">ファイルまたはディレクトリの **name** を設定または変更する場合:</span><span class="sxs-lookup"><span data-stu-id="00fcb-122">When you set or change the **name** of the file or directory:</span></span>  
  
    -   <span data-ttu-id="00fcb-123">ファイルおよびディレクトリに対する Windows の名前付け規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-123">Windows file and directory naming conventions are enforced.</span></span>  
  
    -   <span data-ttu-id="00fcb-124">親ディレクトリ内での名前の一意性が強制されます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-124">The uniqueness of the name in the parent directory is enforced.</span></span>  
  
-   <span data-ttu-id="00fcb-125">**path_locator** あるいは **parent_path_locator**を設定または変更することによってファイル (またはディレクトリ) の場所を設定または変更した場合:</span><span class="sxs-lookup"><span data-stu-id="00fcb-125">When you set or change the location of a file or directory by setting or changing the **path_locator** or **parent_path_locator**:</span></span>  
  
    -   <span data-ttu-id="00fcb-126">一意性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-126">Uniqueness is enforced.</span></span>  
  
    -   <span data-ttu-id="00fcb-127">ディレクトリおよびファイルの階層ツリーの一貫性が強制されます ( **path_locator** 値と **parent_path_locator** 値の一貫性を含む)。</span><span class="sxs-lookup"><span data-stu-id="00fcb-127">The consistency of the hierarchical tree of directories and files is enforced, including the consistency of **path_locator** and **parent_path_locator** values.</span></span>  
  
-   <span data-ttu-id="00fcb-128">**file_stream** 列が null の場合、 **is_directory** の値を true に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="00fcb-128">The value of **is_directory** cannot be set to true when the **file_stream** column is not null.</span></span> <span data-ttu-id="00fcb-129">**file_stream** 列のデータは、その行がディレクトリではなくファイルを表していることを示します。</span><span class="sxs-lookup"><span data-stu-id="00fcb-129">Data in the **file_stream** column indicates that the row represents a file and not a directory.</span></span>  
  
-   <span data-ttu-id="00fcb-130">ファイル属性列は NULL にできません。</span><span class="sxs-lookup"><span data-stu-id="00fcb-130">File attribute columns cannot be null.</span></span> <span data-ttu-id="00fcb-131">NOT NULL 制約が既定値で適用されます。</span><span class="sxs-lookup"><span data-stu-id="00fcb-131">NOT NULL constraints are enforced with default values.</span></span>  
  
-   <span data-ttu-id="00fcb-132">**last_access_time** の値が **last_write_time** や **creation_time**よりも前に来ることはできません。</span><span class="sxs-lookup"><span data-stu-id="00fcb-132">The value of **last_access_time** cannot be earlier than **last_write_time** and **creation_time**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00fcb-133">参照</span><span class="sxs-lookup"><span data-stu-id="00fcb-133">See Also</span></span>  
 <span data-ttu-id="00fcb-134">[FileTable へのファイルの読み込み](load-files-into-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="00fcb-134">[Load Files into FileTables](load-files-into-filetables.md) </span></span>  
 <span data-ttu-id="00fcb-135">[Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="00fcb-135">[Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md) </span></span>  
 <span data-ttu-id="00fcb-136">[ファイル I/O API を使用した FileTable へのアクセス](access-filetables-with-file-input-output-apis.md) </span><span class="sxs-lookup"><span data-stu-id="00fcb-136">[Access FileTables with File Input-Output APIs](access-filetables-with-file-input-output-apis.md) </span></span>  
 [<span data-ttu-id="00fcb-137">FileTable DDL、関数、ストアド プロシージャ、およびビュー</span><span class="sxs-lookup"><span data-stu-id="00fcb-137">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
  
  
