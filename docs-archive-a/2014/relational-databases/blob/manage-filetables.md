---
title: FileTable の管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], security
- FileTables [SQL Server], managing access
ms.assetid: 93af982c-b4fe-4be0-8268-11f86dae27e1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a15a914c243f1fafd3b913d98113e984bf533086
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715406"
---
# <a name="manage-filetables"></a><span data-ttu-id="1147f-102">FileTable の管理</span><span class="sxs-lookup"><span data-stu-id="1147f-102">Manage FileTables</span></span>
  <span data-ttu-id="1147f-103">FileTable を管理するための一般的な管理タスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1147f-103">Describes common administrative tasks for managing FileTables.</span></span>  
  
##  <a name="how-to-get-a-list-of-filetables-and-related-objects"></a><a name="HowToEnumerate"></a> <span data-ttu-id="1147f-104">方法:FileTable と関連オブジェクトの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="1147f-104">How To: Get a List of FileTables and Related Objects</span></span>  
 <span data-ttu-id="1147f-105">FileTable の一覧を取得するには、次のいずれかのカタログ ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1147f-105">To get a list of FileTables, query one of the following catalog views:</span></span>  
  
-   [<span data-ttu-id="1147f-106">sys.filetables &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1147f-106">sys.filetables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-filetables-transact-sql)  
  
-   <span data-ttu-id="1147f-107">[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql) (**is_filetable** 列の値を確認)</span><span class="sxs-lookup"><span data-stu-id="1147f-107">[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql) (Check the value of the **is_filetable** column.)</span></span>  
  
```sql  
SELECT * FROM sys.filetables;  
GO  
  
SELECT * FROM sys.tables WHERE is_filetable = 1;  
GO  
```  
  
 <span data-ttu-id="1147f-108">関連付けられている FileTable の作成時に作成されたシステム定義オブジェクトの一覧を取得するには、カタログ ビュー [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql) に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1147f-108">To get a list of the system-defined objects that were created when the associated FileTables were created, query the catalog view [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql).</span></span>  
  
```sql  
SELECT object_id, OBJECT_NAME(object_id) AS 'Object Name'  
    FROM sys.filetable_system_defined_objects  
    WHERE object_id = filetable_object_id;  
GO  
```  
  
##  <a name="disabling-and-re-enabling-non-transactional-access-at-the-database-level"></a><a name="BasicsDisabling"></a> <span data-ttu-id="1147f-109">データベース レベルでの非トランザクション アクセスの無効化および再有効化</span><span class="sxs-lookup"><span data-stu-id="1147f-109">Disabling and Re-enabling Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="1147f-110">特定の管理タスクに必要な排他アクセスを取得するために、場合によっては一時的に非トランザクション アクセスを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1147f-110">To acquire the exclusive access that is required for certain administrative tasks, you may have to disable non-transactional access temporarily.</span></span>  
  
 <span data-ttu-id="1147f-111">**非トランザクション アクセスのレベルを変更するときの ALTER DATABASE ステートメントの動作**</span><span class="sxs-lookup"><span data-stu-id="1147f-111">**Behavior of the ALTER DATABASE statement when changing the level of non-transactional access**</span></span>  
  
-   <span data-ttu-id="1147f-112">非トランザクション アクセスが READ_ONLY または OFF に設定されている場合、ALTER DATABASE コマンドは、要求された操作と競合する開いたファイル ハンドルがある間はユーザーに制御を返しません。</span><span class="sxs-lookup"><span data-stu-id="1147f-112">When you set non-transactional access to READ_ONLY or OFF, the ALTER DATABASE command does not return control to the user as long as there are open file handles that conflict with the requested operation.</span></span> <span data-ttu-id="1147f-113">この操作と競合するファイル ハンドルには、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="1147f-113">The file handles that conflict with this operation include the following:</span></span>  
  
    -   <span data-ttu-id="1147f-114">アクセスを **NONE**に設定している場合は、すべての開いているファイル ハンドル。</span><span class="sxs-lookup"><span data-stu-id="1147f-114">When you are setting access to **NONE**, all open file handles.</span></span>  
  
    -   <span data-ttu-id="1147f-115">アクセスを **READ_ONLY**に設定している場合は、書き込みアクセスで開かれているすべてのファイル ハンドル。</span><span class="sxs-lookup"><span data-stu-id="1147f-115">When you are setting access to **READ_ONLY**, all file handles opened for write access.</span></span>  
  
     <span data-ttu-id="1147f-116">開いているファイル ハンドルを終了する方法の詳細については、このトピックの「 [FileTable に関連付けられた開いているファイル ハンドルの終了](#BasicsKilling) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1147f-116">For information about killing open file handles, see [Killing Open File Handles Associated with a FileTable](#BasicsKilling) in this topic.</span></span>  
  
     <span data-ttu-id="1147f-117">ALTER DATABASE コマンドが取り消されるかまたはタイムアウトによって終了した場合、トランザクション アクセスのレベルは変更されません。</span><span class="sxs-lookup"><span data-stu-id="1147f-117">If the ALTER DATABASE command is canceled or ends with a timeout, then the level of transactional access is not changed.</span></span>  
  
-   <span data-ttu-id="1147f-118">WITH \<termination> 句 (ROLLBACK AFTER integer [ SECONDS ] | ROLLBACK IMMEDIATE | NO_WAIT) を指定して ALTER DATABASE ステートメントを呼び出した場合、開いているすべての非トランザクション ファイル ハンドルが終了します。</span><span class="sxs-lookup"><span data-stu-id="1147f-118">If you call the ALTER DATABASE statement with a WITH \<termination> clause (ROLLBACK AFTER integer [ SECONDS ] | ROLLBACK IMMEDIATE | NO_WAIT), then all open non-transactional file handles are killed.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1147f-119">開いているファイル ハンドルを終了すると、保存されていないデータをユーザーが失う可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1147f-119">Killing open file handles may cause users to lose unsaved data.</span></span> <span data-ttu-id="1147f-120">この動作は、ファイル システム自体の動作と一致しています。</span><span class="sxs-lookup"><span data-stu-id="1147f-120">This behavior is consistent with the behavior of the file system itself.</span></span>  
  
 <span data-ttu-id="1147f-121">**非トランザクション アクセスを無効化した場合の影響**</span><span class="sxs-lookup"><span data-stu-id="1147f-121">**Effects of disabling non-transactional access**</span></span>  
  
 <span data-ttu-id="1147f-122">データベース レベルでの非トランザクション アクセスのレベルを変更した場合、データベース レベルのディレクトリの下の FileTable ディレクトリに次の影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="1147f-122">Changing the level of non-transactional access at the database level has the following effects on the FileTable directories under the database-level directory:</span></span>  
  
-   <span data-ttu-id="1147f-123">アクセスを **NONE**に設定した場合、すべての FileTable ディレクトリとそのコンテンツはアクセスも表示もできなくなります。</span><span class="sxs-lookup"><span data-stu-id="1147f-123">When you set access to **NONE**, then all the FileTable directories and their contents are no longer accessible or visible.</span></span>  
  
-   <span data-ttu-id="1147f-124">アクセスを **READ_ONLY**に設定した場合、すべての FileTable ディレクトリとそのコンテンツも読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="1147f-124">When you set access to **READ_ONLY**, then all the FileTable directories and their contents are also read-only.</span></span>  
  
 <span data-ttu-id="1147f-125">インスタンス レベルで FILESTREAM を無効化した場合、そのインスタンスのデータベース レベルのディレクトリと、その下の FileTable ディレクトリに、次の影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="1147f-125">Disabling FILESTREAM at the instance level has the following effects on the database-level directories on that instance, and the FileTable directories under them:</span></span>  
  
-   <span data-ttu-id="1147f-126">FILESTREAM がインスタンス レベルで無効化された場合、そのインスタンスのデータベース レベルのディレクトリはすべて表示されません。</span><span class="sxs-lookup"><span data-stu-id="1147f-126">None of the database-level directories on the instance are visible if FILESTREAM is disabled at the instance level.</span></span>  
  
###  <a name="how-to-disable-and-re-enable-non-transactional-access-at-the-database-level"></a><a name="HowToDisable"></a> <span data-ttu-id="1147f-127">方法:データベース レベルで非トランザクション アクセスを無効化および再有効化する</span><span class="sxs-lookup"><span data-stu-id="1147f-127">How To: Disable and Re-enable Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="1147f-128">詳細については、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1147f-128">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="1147f-129">**完全な非トランザクション アクセスを無効化するには**</span><span class="sxs-lookup"><span data-stu-id="1147f-129">**To disable full non-transactional access**</span></span>  
 <span data-ttu-id="1147f-130">**ALTER DATABASE** ステートメントを呼び出し、 **NON_TRANSACTED_ACCESS** の値を **READ_ONLY** または **OFF**に設定します。</span><span class="sxs-lookup"><span data-stu-id="1147f-130">Call the **ALTER DATABASE** statement and SET the value of **NON_TRANSACTED_ACCESS** to **READ_ONLY** or **OFF**.</span></span>  
  
```sql  
-- Disable write access.  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = READ_ONLY );  
GO  
  
-- Disable non-transactional access.  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = OFF );  
GO  
```  
  
 <span data-ttu-id="1147f-131">**完全な非トランザクション アクセスを再有効化するには**</span><span class="sxs-lookup"><span data-stu-id="1147f-131">**To re-enable full non-transactional access**</span></span>  
 <span data-ttu-id="1147f-132">**ALTER DATABASE** ステートメントを呼び出し、 **NON_TRANSACTED_ACCESS** の値を **FULL**に設定します。</span><span class="sxs-lookup"><span data-stu-id="1147f-132">Call the **ALTER DATABASE** statement and SET the value of **NON_TRANSACTED_ACCESS** to **FULL**.</span></span>  
  
```sql  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL );  
GO  
```  
  
###  <a name="how-to-ensure-the-visibility-of-the-filetables-in-a-database"></a><a name="visible"></a> <span data-ttu-id="1147f-133">方法:データベースの FileTable が必ず表示されるようにする</span><span class="sxs-lookup"><span data-stu-id="1147f-133">How to: Ensure the Visibility of the FileTables in a Database</span></span>  
 <span data-ttu-id="1147f-134">以下のすべての条件が満たされる場合、データベース レベルのディレクトリとその下の FileTable ディレクトリは表示状態になります。</span><span class="sxs-lookup"><span data-stu-id="1147f-134">A database-level directory and the FileTable directories under it are visible when all of these conditions are true:</span></span>  
  
1.  <span data-ttu-id="1147f-135">インスタンス レベルで FILESTREAM が有効になっている。</span><span class="sxs-lookup"><span data-stu-id="1147f-135">FILESTREAM is enabled at the instance level.</span></span>  
  
2.  <span data-ttu-id="1147f-136">データベース レベルで非トランザクション アクセスが有効になっている。</span><span class="sxs-lookup"><span data-stu-id="1147f-136">Non-transactional access is enabled at the database level.</span></span>  
  
3.  <span data-ttu-id="1147f-137">データベース レベルで有効なディレクトリが指定されている。</span><span class="sxs-lookup"><span data-stu-id="1147f-137">A valid directory has been specified at the database level.</span></span>  
  
##  <a name="disabling-and-re-enabling-the-filetable-namespace-at-the-table-level"></a><a name="BasicsEnabling"></a> <span data-ttu-id="1147f-138">テーブル レベルでの FileTable 名前空間の無効化および再有効化</span><span class="sxs-lookup"><span data-stu-id="1147f-138">Disabling and Re-enabling the FileTable Namespace at the Table Level</span></span>  
 <span data-ttu-id="1147f-139">FileTable 名前空間を無効にすると、FileTable に対して作成されたすべてのシステム定義制約およびトリガーが無効になります。</span><span class="sxs-lookup"><span data-stu-id="1147f-139">Disabling the FileTable namespace disables all the system-defined constraints and triggers that were created with the FileTable.</span></span> <span data-ttu-id="1147f-140">これは、FileTable セマンティクスの適用を行うことなく [!INCLUDE[tsql](../../includes/tsql-md.md)] 操作を使用して FileTable を大幅に再編成する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="1147f-140">This is useful in cases where a FileTable has to be reorganized on a large scale by using [!INCLUDE[tsql](../../includes/tsql-md.md)] operations without incurring the expense of enforcing FileTable semantics.</span></span> <span data-ttu-id="1147f-141">ただし、これらの操作によって FileTable の一貫性が損なわれ、FileTable 名前空間の再有効化が妨げられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1147f-141">However these operations can leave the FileTable in an inconsistent state, and can prevent the re-enabling of the FileTable namespace.</span></span>  
  
 <span data-ttu-id="1147f-142">FileTable 名前空間を無効にすると、次のような結果になります。</span><span class="sxs-lookup"><span data-stu-id="1147f-142">Disabling a FileTable namespace has the following results:</span></span>  
  
-   <span data-ttu-id="1147f-143">FileTable 列およびデータは、テーブルから物理的に削除されません。</span><span class="sxs-lookup"><span data-stu-id="1147f-143">FileTable columns and data are not physically dropped from the table.</span></span>  
  
-   <span data-ttu-id="1147f-144">FileTable ディレクトリと、それに含まれているファイルおよびディレクトリは、ファイル システムから消失し、ファイル I/O アクセスに使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="1147f-144">The FileTable directory and the files and directories that it contains disappear from the file system and are not available for file i/o access.</span></span>  
  
-   <span data-ttu-id="1147f-145">システム定義の FileTable 列を削除または再作成することはできませんが、これらの列は DML 操作で通常の列と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="1147f-145">System-defined FileTable columns cannot be dropped and recreated; otherwise, however, they behave like ordinary columns for DML operations.</span></span>  
  
-   <span data-ttu-id="1147f-146">開いているファイル ハンドルがあると、FileTable 制約を無効化できません。この操作には、テーブルのスキーマ ロックが必要になるためです。</span><span class="sxs-lookup"><span data-stu-id="1147f-146">Open file handles prevent the FileTable constraints from being disabled, since this operation requires a schema lock on the table.</span></span>  
  
-   <span data-ttu-id="1147f-147">FileTable 名前空間の無効化後、すべての FileTable セマンティクスの適用が、システム定義の制約およびトリガーも含めて、停止されます。</span><span class="sxs-lookup"><span data-stu-id="1147f-147">Enforcement of all the FileTable semantics, including system-defined constraints and triggers, stops after the FileTable namespace is disabled.</span></span>  
  
 <span data-ttu-id="1147f-148">FileTable 名前空間を再有効化すると、次のような結果になります。</span><span class="sxs-lookup"><span data-stu-id="1147f-148">Re-enabling a FileTable namespace has the following results:</span></span>  
  
-   <span data-ttu-id="1147f-149">FileTable の一貫性がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="1147f-149">The FileTable is checked for consistency.</span></span> <span data-ttu-id="1147f-150">不整合が見つかった場合は、エラーが発生し、FileTable は無効のままになります。それ以外の場合、FileTable は再有効化されます。</span><span class="sxs-lookup"><span data-stu-id="1147f-150">If inconsistencies are found, then an error is raised and the FileTable remains disabled; otherwise, the FileTable is re-enabled.</span></span>  
  
-   <span data-ttu-id="1147f-151">FileTable セマンティクスの適用が、システム定義の制約およびトリガーも含めて、復元されます。</span><span class="sxs-lookup"><span data-stu-id="1147f-151">The enforcement of FileTable semantics, including system-defined constraints and triggers, is restored.</span></span>  
  
-   <span data-ttu-id="1147f-152">FileTable ディレクトリと、それに含まれているファイルおよびディレクトリは、ファイル システムに表示され、ファイル I/O アクセスに使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1147f-152">The FileTable directory and the files and directories that it contains become visible in the file system and become available for file i/o access.</span></span>  
  
###  <a name="how-to-disable-and-re-enable-the-filetable-namespace-at-the-table-level"></a><a name="HowToEnableNS"></a> <span data-ttu-id="1147f-153">方法:テーブル レベルで FileTable 名前空間を無効化および再有効化する</span><span class="sxs-lookup"><span data-stu-id="1147f-153">How To: Disable and Re-enable the FileTable Namespace at the Table Level</span></span>  
 <span data-ttu-id="1147f-154">**{ ENABLE | DISABLE } FILETABLE_NAMESPACE** オプションを指定して ALTER TABLE ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1147f-154">Call the ALTER TABLE statement with the **{ ENABLE | DISABLE } FILETABLE_NAMESPACE** option.</span></span>  
  
 <span data-ttu-id="1147f-155">**FileTable 名前空間を無効にするには**</span><span class="sxs-lookup"><span data-stu-id="1147f-155">**To disable the FileTable namespace**</span></span>  
 ```sql  
ALTER TABLE filetable_name  
    DISABLE FILETABLE_NAMESPACE;  
GO  
```  
  
 <span data-ttu-id="1147f-156">**FileTable 名前空間を再有効化するには**</span><span class="sxs-lookup"><span data-stu-id="1147f-156">**To re-enable the FileTable namespace**</span></span>  
 ```sql  
ALTER TABLE filetable_name  
    ENABLE FILETABLE_NAMESPACE;  
GO  
```  
  
##  <a name="killing-open-file-handles-associated-with-a-filetable"></a><a name="BasicsKilling"></a> <span data-ttu-id="1147f-157">FileTable に関連付けられた開いているファイル ハンドルの終了</span><span class="sxs-lookup"><span data-stu-id="1147f-157">Killing Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="1147f-158">FileTable に格納されているファイルへの開いているハンドルにより、特定の管理タスクで必要となる排他アクセスが妨げられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1147f-158">Open handles to the files stored in a FileTable can prevent the exclusive access that is required for certain administrative tasks.</span></span> <span data-ttu-id="1147f-159">緊急のタスクを有効にするには、場合により 1 つまたは複数の FileTable に関連付けられている開いているファイル ハンドルを終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1147f-159">To enable urgent tasks, you may have to kill open file handles associated with one or more FileTables.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1147f-160">開いているファイル ハンドルを終了すると、保存されていないデータをユーザーが失う可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1147f-160">Killing open file handles may cause users to lose unsaved data.</span></span> <span data-ttu-id="1147f-161">この動作は、ファイル システム自体の動作と一致しています。</span><span class="sxs-lookup"><span data-stu-id="1147f-161">This behavior is consistent with the behavior of the file system itself.</span></span>  
  
###  <a name="how-to-get-a-list-of-open-file-handles-associated-with-a-filetable"></a><a name="HowToListOpen"></a> <span data-ttu-id="1147f-162">方法:FileTable に関連付けられた開いているファイル ハンドルの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="1147f-162">How To: Get a List of Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="1147f-163">カタログ ビュー [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql) に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1147f-163">Query the catalog view [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql).</span></span>  
  
```sql  
SELECT * FROM sys.dm_filestream_non_transacted_handles;  
GO  
```  
  
###  <a name="how-to-kill-open-file-handles-associated-with-a-filetable"></a><a name="HowToKill"></a> <span data-ttu-id="1147f-164">方法:FileTable に関連付けられた開いているファイル ハンドルを終了する</span><span class="sxs-lookup"><span data-stu-id="1147f-164">How To: Kill Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="1147f-165">データベースまたは FileTable のすべての開いているファイル ハンドルを終了するか、特定のハンドルを終了するための適切な引数を指定して、[sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles) ストアド プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1147f-165">Call the stored procedure [sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles) with the appropriate arguments to kill all open file handles in the database or in the FileTable, or to kill a specific handle.</span></span>  
  
```  
USE database_name;  
  
-- Kill all open handles in all the filetables in the database.  
EXEC sp_kill_filestream_non_transacted_handles;  
GO  
  
-- Kill all open handles in a single filetable.  
EXEC sp_kill_filestream_non_transacted_handles @table_name = 'filetable_name';  
GO  
  
-- Kill a single handle.  
EXEC sp_kill_filestream_non_transacted_handles @handle_id = integer_handle_id;  
GO  
```  
  
###  <a name="how-to-identify-the-locks-held-by-filetables"></a><a name="HowToIdentifyLocks"></a> <span data-ttu-id="1147f-166">方法:FileTable によって保持されているロックを識別する</span><span class="sxs-lookup"><span data-stu-id="1147f-166">How to: Identify the Locks Held by FileTables</span></span>  
 <span data-ttu-id="1147f-167">FileTable によって取得されるほとんどのロックは、アプリケーションによって開かれたファイルに対応します。</span><span class="sxs-lookup"><span data-stu-id="1147f-167">Most locks taken by FileTables correspond to files opened by applications.</span></span>  
  
 <span data-ttu-id="1147f-168">**開いているファイルおよび関連付けられているロックを識別するには**</span><span class="sxs-lookup"><span data-stu-id="1147f-168">**To identify open files and the associated locks**</span></span>  
 <span data-ttu-id="1147f-169">動的管理ビュー [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) の **request_owner_id** フィールドを [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql) の **fcb_id** フィールドと結合します。</span><span class="sxs-lookup"><span data-stu-id="1147f-169">Join the **request_owner_id** field in the dynamic management view [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) with the **fcb_id** field in [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql).</span></span> <span data-ttu-id="1147f-170">場合によっては、ロックが単一の開いているファイル ハンドルと対応しないこともあります。</span><span class="sxs-lookup"><span data-stu-id="1147f-170">In some cases, the lock does not correspond to a single open file handle.</span></span>  
  
```sql  
SELECT opened_file_name  
    FROM sys.dm_filestream_non_transacted_handles  
    WHERE fcb_id IN  
        ( SELECT request_owner_id FROM sys.dm_tran_locks );  
GO  
```  
  
##  <a name="filetable-security"></a><a name="BasicsSecurity"></a> <span data-ttu-id="1147f-171">FileTable セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1147f-171">FileTable Security</span></span>  
 <span data-ttu-id="1147f-172">FileTable に格納されているファイルとディレクトリは、SQL Server セキュリティのみによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="1147f-172">The files and directories stored in FileTables are secured by SQL Server security only.</span></span> <span data-ttu-id="1147f-173">テーブルおよび列ベースのセキュリティは、ファイル システム アクセスおよび [!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1147f-173">Table and column-based security is enforced for file system access as well as [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="1147f-174">Windows ファイル システム セキュリティ API および ACL 設定はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1147f-174">Windows file system security APIs and ACL settings are not supported.</span></span>  
  
 <span data-ttu-id="1147f-175">FILESTREAM ファイル グループおよびコンテナーに適用可能なセキュリティおよびアクセス許可は、FileTable にも適用されます。これは、ファイル データは FileTable の FILESTREAM 列として格納されるためです。</span><span class="sxs-lookup"><span data-stu-id="1147f-175">The security and access permissions that are applicable to FILESTREAM filegroups and containers also apply to FileTables, since the file data is stored as a FILESTREAM column in the FileTable.</span></span>  
  
 <span data-ttu-id="1147f-176">**FileTable セキュリティと Transact-SQL アクセス**</span><span class="sxs-lookup"><span data-stu-id="1147f-176">**FileTable Security and Transact-SQL Access**</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="1147f-177">FileTable のデータに対するアクセスは、他のすべてのテーブルと同様にセキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="1147f-177">access to data in FileTables is secured in the same way as any other table.</span></span> <span data-ttu-id="1147f-178">データに対するアクセスや変更を行う各操作に関して、適切なテーブルおよび列レベルのセキュリティ チェックが行われます。</span><span class="sxs-lookup"><span data-stu-id="1147f-178">Appropriate table and column-level security checks are done for every operation that accesses or changes the data.</span></span>  
  
 <span data-ttu-id="1147f-179">**FileTable セキュリティとファイル システム アクセス**</span><span class="sxs-lookup"><span data-stu-id="1147f-179">**FileTable Security and File System Access**</span></span>  
 <span data-ttu-id="1147f-180">ファイル システム API には、FileTable に格納されているファイルまたはディレクトリへのハンドルを開くための、FileTable の行全体に対する適切な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 権限 (つまり、テーブル レベルの権限) が必要です。</span><span class="sxs-lookup"><span data-stu-id="1147f-180">File system APIs require appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permissions on the entire row in the FileTable (that is, table-level permission) to open a handle to a file or directory stored in the FileTable.</span></span> <span data-ttu-id="1147f-181">FileTable の列に対する適切な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 権限がユーザーに与えられていない場合、ファイル システム アクセスは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="1147f-181">If the user does not have the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permission on any column in the FileTable, then file system access is denied.</span></span>  
  
##  <a name="backup-and-filetables"></a><a name="OtherBackup"></a> <span data-ttu-id="1147f-182">バックアップと FileTable</span><span class="sxs-lookup"><span data-stu-id="1147f-182">Backup and FileTables</span></span>  
 <span data-ttu-id="1147f-183">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して FileTable をバックアップすると、FILESTREAM データがデータベースの構造化データと共にバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="1147f-183">When you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to back up a FileTable, the FILESTREAM data is backed up with the structured data in the database.</span></span> <span data-ttu-id="1147f-184">FILESTREAM データをリレーショナル データと共にバックアップしない場合は、部分バックアップを使用して FILESTREAM ファイル グループを除外できます。</span><span class="sxs-lookup"><span data-stu-id="1147f-184">If you do not want to back up FILESTREAM data with relational data, you can use a partial backup to exclude FILESTREAM filegroups.</span></span>  
  
 <span data-ttu-id="1147f-185">**FileTable バックアップのトランザクションの整合性**</span><span class="sxs-lookup"><span data-stu-id="1147f-185">**Transactional Consistency of FileTable Backups**</span></span>  
  
 <span data-ttu-id="1147f-186">多くの管理ツールおよび操作 (バックアップ、ログ バックアップ、トランザクション レプリケーションなど) では、トランザクション ログを読み取ることにより、トランザクション的に一貫したデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="1147f-186">Many administrative tools and operations, (including backup, log backup, and transactional replication) read transactionally consistent data by reading the transaction logs.</span></span> <span data-ttu-id="1147f-187">このとき、トランザクションの一部として更新された任意の FILESTREAM データが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="1147f-187">At this time, they read any FILESTREAM data updated as part of a transaction.</span></span> <span data-ttu-id="1147f-188">非トランザクション アクセスがデータベース レベルで有効になっていない場合、これらのツールおよび操作は、完全なトランザクションの一貫性を保って動作します。</span><span class="sxs-lookup"><span data-stu-id="1147f-188">When non-transactional access is not enabled at the database level, these tools and operations work with full transactional consistency.</span></span>  
  
 <span data-ttu-id="1147f-189">ただし、完全な非トランザクション アクセスが有効である場合、ツールまたはプロセスによってトランザクション ログから読み取られたトランザクション以降に (非トランザクション更新を介して) 更新されたデータが FileTable に含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1147f-189">However, when full non-transactional access is enabled, then a FileTable could contain data that was updated more recently (through a non-transactional update) than the transaction that the tool or process is reading from the transaction log.</span></span> <span data-ttu-id="1147f-190">つまり、特定のトランザクションの "ある時点" への復元操作に、そのトランザクションよりも新しい FILESTREAM データが含められる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1147f-190">This means that a "point in time" restore operation to a specific transaction may contain FILESTREAM data that is more recent than that transaction.</span></span> <span data-ttu-id="1147f-191">これは、非トランザクション更新が FileTable で許可される場合に想定される動作です。</span><span class="sxs-lookup"><span data-stu-id="1147f-191">This is the expected behavior when non-transactional updates are allowed on FileTables.</span></span>  
  
##  <a name="sql-server-profiler-and-filetables"></a><a name="Monitor"></a> <span data-ttu-id="1147f-192">SQL Server Profiler と FileTables</span><span class="sxs-lookup"><span data-stu-id="1147f-192">SQL Server Profiler and FileTables</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1147f-193">Profiler は、FileTable に格納されているファイルに対するトレース出力内の Windows File Open および File Close 操作をキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="1147f-193">Profiler can capture the Windows File Open and File Close operations in trace output for files that are stored in a FileTable.</span></span>  
  
##  <a name="auditing-and-filetables"></a><a name="OtherAuditing"></a> <span data-ttu-id="1147f-194">監査と FileTable</span><span class="sxs-lookup"><span data-stu-id="1147f-194">Auditing and FileTables</span></span>  
 <span data-ttu-id="1147f-195">FileTable は、他のテーブルと同じように監査できます。</span><span class="sxs-lookup"><span data-stu-id="1147f-195">FileTable can be audited just like any other table.</span></span> <span data-ttu-id="1147f-196">ただし、Win32 アクセス パターンは、セット ベースの操作ではありません。</span><span class="sxs-lookup"><span data-stu-id="1147f-196">Howerver, Win32 access patterns are not set based operations.</span></span> <span data-ttu-id="1147f-197">ファイル システムの単一のアクションが複数の Transact-SQL DML 操作に変換されます。</span><span class="sxs-lookup"><span data-stu-id="1147f-197">A single action in the file system translates into multiple Transact-SQL DML operations.</span></span> <span data-ttu-id="1147f-198">たとえば、Microsoft Word でファイルを開く操作は、複数の操作 (開く操作、閉じる操作、作成、名前の変更、削除) および対応する Transact-SQL DML アクティビティに変換されます。</span><span class="sxs-lookup"><span data-stu-id="1147f-198">For example, opening a file in Microsoft Word translates into multiple open/close/create/rename/delete operations and corresponding Transact-SQL DML activities.</span></span> <span data-ttu-id="1147f-199">その結果、詳細な監査レコードが生成され、ファイル システム アクションとそれに対応する Transact-SQL DML 監査レコードの間でレコードを関連付けることが困難になります。</span><span class="sxs-lookup"><span data-stu-id="1147f-199">This results in verbose audit records where it is hard to correlate records between file system actions and corresponding Transact-SQL DML audit records.</span></span>  
  
##  <a name="dbcc-and-filetables"></a><a name="OtherDBCC"></a> <span data-ttu-id="1147f-200">DBCC と FileTable</span><span class="sxs-lookup"><span data-stu-id="1147f-200">DBCC and FileTables</span></span>  
 <span data-ttu-id="1147f-201">DBCC CHECKCONSTRAINTS を使用すると、システム定義の制約を含む FileTable に対する制約を検証できます。</span><span class="sxs-lookup"><span data-stu-id="1147f-201">You can use DBCC CHECKCONSTRAINTS to validate the constraints on a FileTable including system-defined constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1147f-202">参照</span><span class="sxs-lookup"><span data-stu-id="1147f-202">See Also</span></span>  
 <span data-ttu-id="1147f-203">[FileTable と他の SQL Server 機能の互換性](filetable-compatibility-with-other-sql-server-features.md) </span><span class="sxs-lookup"><span data-stu-id="1147f-203">[FileTable Compatibility with Other SQL Server Features](filetable-compatibility-with-other-sql-server-features.md) </span></span>  
 [<span data-ttu-id="1147f-204">FileTable DDL、関数、ストアド プロシージャ、およびビュー</span><span class="sxs-lookup"><span data-stu-id="1147f-204">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
  
  
