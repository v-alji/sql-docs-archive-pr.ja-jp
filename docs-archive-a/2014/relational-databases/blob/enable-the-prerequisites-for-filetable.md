---
title: FileTable の前提条件の有効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], prerequisites
ms.assetid: 6286468c-9dc9-4eda-9961-071d2a36ebd6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5d5d2c5dab7909ec5403911d482823f488cdd809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631103"
---
# <a name="enable-the-prerequisites-for-filetable"></a><span data-ttu-id="52111-102">FileTable の前提条件の有効化</span><span class="sxs-lookup"><span data-stu-id="52111-102">Enable the Prerequisites for FileTable</span></span>
  <span data-ttu-id="52111-103">FileTable を作成および使用するための前提条件を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="52111-103">Describes how to enable the prerequisites for creating and using FileTables.</span></span>  
  
##  <a name="enabling-the-prerequisites-for-filetable"></a><a name="EnablePrereq"></a> <span data-ttu-id="52111-104">FileTable の前提条件の有効化</span><span class="sxs-lookup"><span data-stu-id="52111-104">Enabling the Prerequisites for FileTable</span></span>  
 <span data-ttu-id="52111-105">FileTable を作成および使用するための前提条件を有効にするには、次の項目を有効にします。</span><span class="sxs-lookup"><span data-stu-id="52111-105">To enable the prerequisites for creating and using FileTables, enable the following items:</span></span>  
  
-   <span data-ttu-id="52111-106">**インスタンス レベル:**</span><span class="sxs-lookup"><span data-stu-id="52111-106">**At the instance level:**</span></span>  
  
    -   [<span data-ttu-id="52111-107">インスタンス レベルでの FILESTREAM の有効化</span><span class="sxs-lookup"><span data-stu-id="52111-107">Enabling FILESTREAM at the Instance Level</span></span>](#BasicsFilestream)  
  
-   <span data-ttu-id="52111-108">**データベース レベル:**</span><span class="sxs-lookup"><span data-stu-id="52111-108">**At the database level:**</span></span>  
  
    -   [<span data-ttu-id="52111-109">データベース レベルでの FILESTREAM ファイル グループの指定</span><span class="sxs-lookup"><span data-stu-id="52111-109">Providing a FILESTREAM Filegroup at the Database Level</span></span>](#filegroup)  
  
    -   [<span data-ttu-id="52111-110">データベース レベルでの非トランザクション アクセスの有効化</span><span class="sxs-lookup"><span data-stu-id="52111-110">Enabling Non-Transactional Access at the Database Level</span></span>](#BasicsNTAccess)  
  
    -   [<span data-ttu-id="52111-111">データベース レベルでの FileTable のディレクトリ指定</span><span class="sxs-lookup"><span data-stu-id="52111-111">Specifying a Directory for FileTables at the Database Level</span></span>](#BasicsDirectory)  
  
##  <a name="enabling-filestream-at-the-instance-level"></a><a name="BasicsFilestream"></a> <span data-ttu-id="52111-112">インスタンス レベルでの FILESTREAM の有効化</span><span class="sxs-lookup"><span data-stu-id="52111-112">Enabling FILESTREAM at the Instance Level</span></span>  
 <span data-ttu-id="52111-113">FileTable は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の FILESTREAM 機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="52111-113">FileTables extend the capabilities of the FILESTREAM feature of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="52111-114">したがって、FileTable を作成および使用するには、ファイル I/O アクセス用の FILESTREAM を Windows レベルおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで事前に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52111-114">Therefore you have to enable FILESTREAM for file I/O access at the Windows level and on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you can create and use FileTables.</span></span>  
  
###  <a name="how-to-enable-filestream-at-the-instance-level"></a><a name="HowToFilestream"></a> <span data-ttu-id="52111-115">方法:インスタンス レベルで FILESTREAM を有効にする</span><span class="sxs-lookup"><span data-stu-id="52111-115">How To: Enable FILESTREAM at the Instance Level</span></span>  
 <span data-ttu-id="52111-116">FILESTREAM を有効にする方法の詳細については、「 [FILESTREAM の有効化と構成](enable-and-configure-filestream.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="52111-116">For information about how to enable FILESTREAM, see [Enable and Configure FILESTREAM](enable-and-configure-filestream.md).</span></span>  
  
 <span data-ttu-id="52111-117">`sp_configure` を呼び出し、FILESTREAM をインスタンス レベルで有効にするには、filestream_access_level オプションを 2 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52111-117">When you call `sp_configure` to enable FILESTREAM at the instance level, you have to set the filestream_access_level option to 2.</span></span> <span data-ttu-id="52111-118">詳細については、「 [filestream access level サーバー構成オプション](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52111-118">For more information, see [filestream access level Server Configuration Option](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).</span></span>  
  
###  <a name="how-to-allow-filestream-through-the-firewall"></a><a name="firewall"></a> <span data-ttu-id="52111-119">方法:FILESTREAM がファイアウォールを通過できるようにする</span><span class="sxs-lookup"><span data-stu-id="52111-119">How To: Allow FILESTREAM through the Firewall</span></span>  
 <span data-ttu-id="52111-120">FILESTREAM がファイアウォールを通過できるようにする方法については、「 [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="52111-120">For information about how to allow FILESTREAM through the firewall, see [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md).</span></span>  
  
##  <a name="providing-a-filestream-filegroup-at-the-database-level"></a><a name="filegroup"></a> <span data-ttu-id="52111-121">データベース レベルでの FILESTREAM ファイル グループの指定</span><span class="sxs-lookup"><span data-stu-id="52111-121">Providing a FILESTREAM Filegroup at the Database Level</span></span>  
 <span data-ttu-id="52111-122">データベースに FileTable を作成するには、データベースに FILESTREAM ファイル グループが必要です。</span><span class="sxs-lookup"><span data-stu-id="52111-122">Before you can create FileTables in a database, the database must have a FILESTREAM filegroup.</span></span> <span data-ttu-id="52111-123">この前提条件の詳細については、「 [FILESTREAM が有効なデータベースを作成する方法](create-a-filestream-enabled-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52111-123">For more information about this prerequisite, see [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
##  <a name="enabling-non-transactional-access-at-the-database-level"></a><a name="BasicsNTAccess"></a> <span data-ttu-id="52111-124">データベース レベルでの非トランザクション アクセスの有効化</span><span class="sxs-lookup"><span data-stu-id="52111-124">Enabling Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="52111-125">FileTable は、Windows アプリケーションがトランザクションを必要とすることなく FILESTREAM データに対する Windows ファイル ハンドルを取得することを可能にします。</span><span class="sxs-lookup"><span data-stu-id="52111-125">FileTables let Windows applications obtain a Windows file handle to FILESTREAM data without requiring a transaction.</span></span> <span data-ttu-id="52111-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納されているファイルに対するこの非トランザクション アクセスを可能にするには、FileTable を格納するデータベースごとに、データベース レベルで非トランザクション アクセスのレベルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52111-126">To allow this non-transactional access to files stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you have to specify the desired level of non-transactional access at the database level for each database that will contain FileTables.</span></span>  
  
###  <a name="how-to-check-whether-non-transactional-access-is-enabled-on-databases"></a><a name="HowToCheckAccess"></a> <span data-ttu-id="52111-127">方法:データベースで非トランザクション アクセスが有効かどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="52111-127">How To: Check Whether Non-Transactional Access Is Enabled on Databases</span></span>  
 <span data-ttu-id="52111-128">カタログ ビュー [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) に対してクエリを実行し、**non_transacted_access** 列と **non_transacted_access_desc** 列をチェックします。</span><span class="sxs-lookup"><span data-stu-id="52111-128">Query the catalog view [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) and check the **non_transacted_access** and **non_transacted_access_desc** columns.</span></span>  
  
```sql  
SELECT DB_NAME(database_id), non_transacted_access, non_transacted_access_desc  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="how-to-enable-non-transactional-access-at-the-database-level"></a><a name="HowToNTAccess"></a> <span data-ttu-id="52111-129">方法:データベース レベルで非トランザクション アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="52111-129">How To: Enable Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="52111-130">使用できる非トランザクション アクセスのレベルは、FULL、READ_ONLY、および OFF です。</span><span class="sxs-lookup"><span data-stu-id="52111-130">The available levels of non-transactional access are FULL, READ_ONLY, and OFF.</span></span>  
  
 <span data-ttu-id="52111-131">**Transact-SQL を使用して非トランザクション アクセスのレベルを指定する**</span><span class="sxs-lookup"><span data-stu-id="52111-131">**Specify the level of non-transactional access by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="52111-132">**新しいデータベースを作成**するときに、**NON_TRANSACTED_ACCESS** FILESTREAM オプションを使用して [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="52111-132">When you **create a new database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **NON_TRANSACTED_ACCESS** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
-   <span data-ttu-id="52111-133">**既存のデータベースを変更**するときに、**NON_TRANSACTED_ACCESS** FILESTREAM オプションを使用して [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="52111-133">When you **alter an existing database**, call the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement with the **NON_TRANSACTED_ACCESS** FILESTREAM option.</span></span>  
  
    ```sql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
 <span data-ttu-id="52111-134">**SQL Server Management Studio を使用して非トランザクション アクセスのレベルを指定する**</span><span class="sxs-lookup"><span data-stu-id="52111-134">**Specify the level of non-transactional access by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="52111-135">**[データベースのプロパティ]** ダイアログ ボックスの **[オプション]** ページの **[FILESTREAM 非トランザクション アクセス]** ボックスで、非トランザクション アクセスのレベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="52111-135">You can specify the level of non-transactional access in the **FILESTREAM Non-transacted Access** field of the **Options** page of the **Database Properties** dialog box.</span></span> <span data-ttu-id="52111-136">このダイアログ ボックスの詳細については、「[[データベースのプロパティ] &#40;[オプション] ページ&#41;](../databases/database-properties-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52111-136">For more information about this dialog box, see [Database Properties &#40;Options Page&#41;](../databases/database-properties-options-page.md).</span></span>  
  
##  <a name="specifying-a-directory-for-filetables-at-the-database-level"></a><a name="BasicsDirectory"></a> <span data-ttu-id="52111-137">データベース レベルでの FileTable のディレクトリ指定</span><span class="sxs-lookup"><span data-stu-id="52111-137">Specifying a Directory for FileTables at the Database Level</span></span>  
 <span data-ttu-id="52111-138">ファイルに対する非トランザクション アクセスをデータベース レベルで有効にする場合、必要に応じて **DIRECTORY_NAME** オプションを使用してディレクトリ名も指定できます。</span><span class="sxs-lookup"><span data-stu-id="52111-138">When you enable non-transactional access to files at the database level, you can optionally provide a directory name at the same time by using the **DIRECTORY_NAME** option.</span></span> <span data-ttu-id="52111-139">非トランザクション アクセスを有効にしたときにディレクトリ名を指定しなかった場合は、データベースに FileTable を作成する前にディレクトリ名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52111-139">If you do not provide a directory name when you enable non-transactional access, then you have to provide it later before you can create FileTables in the database.</span></span>  
  
 <span data-ttu-id="52111-140">FileTable フォルダー階層において、このデータベース レベルのディレクトリは、インスタンス レベルで FILESTREAM に対して指定された共有名の子になると同時に、データベースに作成された FileTable の親になります。</span><span class="sxs-lookup"><span data-stu-id="52111-140">In the FileTable folder hierarchy, this database-level directory becomes the child of the share name specified for FILESTREAM at the instance level, and the parent of the FileTables created in the database.</span></span> <span data-ttu-id="52111-141">詳しくは、「 [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="52111-141">For more information, see [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md).</span></span>  
  
###  <a name="how-to-specify-a-directory-for-filetables-at-the-database-level"></a><a name="HowToDirectory"></a> <span data-ttu-id="52111-142">方法:データベース レベルで FileTable のディレクトリを指定する</span><span class="sxs-lookup"><span data-stu-id="52111-142">How To: Specify a Directory for FileTables at the Database Level</span></span>  
 <span data-ttu-id="52111-143">指定する名前は、データベース レベルで存在するディレクトリに対して一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="52111-143">The name that you specify must be unique across the instance for database-level directories.</span></span>  
  
 <span data-ttu-id="52111-144">**Transact-SQL を使用して FileTable のディレクトリを指定する**</span><span class="sxs-lookup"><span data-stu-id="52111-144">**Specify a directory for FileTables by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="52111-145">**新しいデータベースを作成**するときに、**DIRECTORY_NAME** FILESTREAM オプションを使用して [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="52111-145">When you **create a new database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="52111-146">**既存のデータベースを変更**するときに、**DIRECTORY_NAME** FILESTREAM オプションを使用して [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="52111-146">When you **alter an existing database**, call the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span> <span data-ttu-id="52111-147">これらのオプションを使用してディレクトリ名を変更するとき、データベースを排他的にロックして、開いているファイル ハンドルがないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52111-147">When you use these options to change the directory name, the database must be exclusively locked, with no open file handles.</span></span>  
  
    ```sql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="52111-148">**データベースをアタッチ**するときに、**FOR ATTACH** オプションおよび **DIRECTORY_NAME** FILESTREAM オプションを使用して [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="52111-148">When you **attach a database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **FOR ATTACH** option and with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        FOR ATTACH WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="52111-149">**データベースを復元**するときに、**DIRECTORY_NAME** FILESTREAM オプションを使用して [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="52111-149">When you **restore a database**, call the [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    RESTORE DATABASE database_name  
        WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
 <span data-ttu-id="52111-150">**SQL Server Management Studio を使用して、FileTable のディレクトリを指定する**</span><span class="sxs-lookup"><span data-stu-id="52111-150">**Specify a directory for FileTables by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="52111-151">**[データベースのプロパティ]** ダイアログ ボックスの **[オプション]** ページの **[FILESTREAM ディレクトリ名]** ボックスで、ディレクトリ名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="52111-151">You can specify a directory name in the **FILESTREAM Directory Name** field of the **Options** page of the **Database Properties** dialog box.</span></span> <span data-ttu-id="52111-152">このダイアログ ボックスの詳細については、「[[データベースのプロパティ] &#40;[オプション] ページ&#41;](../databases/database-properties-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52111-152">For more information about this dialog box, see [Database Properties &#40;Options Page&#41;](../databases/database-properties-options-page.md).</span></span>  
  
###  <a name="how-to-view-existing-directory-names-for-the-instance"></a><a name="viewnames"></a> <span data-ttu-id="52111-153">方法:インスタンスの既存のディレクトリ名を表示する</span><span class="sxs-lookup"><span data-stu-id="52111-153">How to: View Existing Directory Names for the Instance</span></span>  
 <span data-ttu-id="52111-154">インスタンスの既存のディレクトリ名の一覧を表示するには、[ys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) カタログ ビューに対するクエリを実行し、**filestream_database_directory_name** 列を確認します。</span><span class="sxs-lookup"><span data-stu-id="52111-154">To view the list of existing directory names for the instance, query the catalog view [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) and check the **filestream_database_directory_name** column.</span></span>  
  
```sql  
SELECT DB_NAME ( database_id ), directory_name  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="requirements-and-restrictions-for-the-database-level-directory"></a><a name="ReqDirectory"></a> <span data-ttu-id="52111-155">データベース レベルのディレクトリの要件と制限</span><span class="sxs-lookup"><span data-stu-id="52111-155">Requirements and Restrictions for the Database-Level Directory</span></span>  
  
-   <span data-ttu-id="52111-156">**CREATE DATABASE** または **ALTER DATABASE** を呼び出すとき、 **DIRECTORY_NAME**をオプションで設定できます。</span><span class="sxs-lookup"><span data-stu-id="52111-156">Setting the **DIRECTORY_NAME** is optional when you call **CREATE DATABASE** or **ALTER DATABASE**.</span></span> <span data-ttu-id="52111-157">**DIRECTORY_NAME**の値を指定しなかった場合、ディレクトリ名は null のままになります。</span><span class="sxs-lookup"><span data-stu-id="52111-157">If you do not specify a value for **DIRECTORY_NAME**, then the directory name remains null.</span></span> <span data-ttu-id="52111-158">ただし、データベース レベルで **DIRECTORY_NAME** の値を指定しないと、データベースに FileTable を作成できません。</span><span class="sxs-lookup"><span data-stu-id="52111-158">However you cannot create FileTables in the database until you specify a value for **DIRECTORY_NAME** at the database level.</span></span>  
  
-   <span data-ttu-id="52111-159">指定するディレクトリ名は、ファイル システムの有効なディレクトリ名に関する要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="52111-159">The directory name that you provide must comply with the requirements of the file system for a valid directory name.</span></span>  
  
-   <span data-ttu-id="52111-160">データベースに FileTable が含まれている場合、 **DIRECTORY_NAME** を再度 null 値に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="52111-160">When the database contains FileTables, you cannot set the **DIRECTORY_NAME** back to a null value.</span></span>  
  
-   <span data-ttu-id="52111-161">データベースをアタッチまたは復元するときに、対象のインスタンスに既に存在する **DIRECTORY_NAME** の値が新しいデータベースにある場合、操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="52111-161">When you attach or restore a database, the operation fails if the new database has a value for **DIRECTORY_NAME** that already exists in the target instance.</span></span> <span data-ttu-id="52111-162">**CREATE DATABASE FOR ATTACH** または **RESTORE DATABASE** を呼び出すときは、 **DIRECTORY_NAME**に対して一意の値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="52111-162">Specify a unique value for **DIRECTORY_NAME** when you call **CREATE DATABASE FOR ATTACH** or **RESTORE DATABASE**.</span></span>  
  
-   <span data-ttu-id="52111-163">既存のデータベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードした場合、 **DIRECTORY_NAME** の値は null になります。</span><span class="sxs-lookup"><span data-stu-id="52111-163">When you upgrade an existing database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the value of **DIRECTORY_NAME** is null.</span></span>  
  
-   <span data-ttu-id="52111-164">非トランザクション アクセスをデータベース レベルで有効または無効にするとき、ディレクトリ名が指定されているかどうか、またはディレクトリ名が一意であるかどうかのチェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="52111-164">When you enable or disable non-transactional access at the database level, the operation does not check whether the directory name has been specified or whether it is unique.</span></span>  
  
-   <span data-ttu-id="52111-165">FileTable に対して有効化されていたデータベースを削除すると、データベース レベルのディレクトリとそれ以下のすべての FileTable のすべてのディレクトリ構造が削除されます。</span><span class="sxs-lookup"><span data-stu-id="52111-165">When you drop a database that was enabled for FileTables, the database-level directory and all the directory stuctures of all the FileTables under it are removed.</span></span>  
  
  
