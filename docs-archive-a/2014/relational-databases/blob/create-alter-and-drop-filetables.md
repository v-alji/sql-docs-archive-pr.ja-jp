---
title: FileTable の作成、変更、および削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], altering
- FileTables [SQL Server], dropping
- FileTables [SQL Server], creating
ms.assetid: 47d69e37-8778-4630-809b-2261b5c41c2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a10e6333f6dd38a850a832b82a7cb7a0e0bf698
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632526"
---
# <a name="create-alter-and-drop-filetables"></a><span data-ttu-id="f589d-102">FileTable の作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="f589d-102">Create, Alter, and Drop FileTables</span></span>
  <span data-ttu-id="f589d-103">新しい FileTable の作成や、既存の FileTable の変更または削除を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f589d-103">Describes how to create a new FileTable, or alter or drop an existing FileTable.</span></span>  
  
##  <a name="creating-a-filetable"></a><a name="BasicsCreate"></a> <span data-ttu-id="f589d-104">FileTable の作成</span><span class="sxs-lookup"><span data-stu-id="f589d-104">Creating a FileTable</span></span>  
 <span data-ttu-id="f589d-105">FileTable は、定義済みおよび固定のスキーマがある特殊なユーザー テーブルです。</span><span class="sxs-lookup"><span data-stu-id="f589d-105">A FileTable is a specialized user table that has a pre-defined and fixed schema.</span></span> <span data-ttu-id="f589d-106">このスキーマは、FILESTREAM データ、ファイルとディレクトリの情報、およびファイルの属性を格納します。</span><span class="sxs-lookup"><span data-stu-id="f589d-106">This schema stores FILESTREAM data, file and directory information, and file attributes.</span></span> <span data-ttu-id="f589d-107">FileTable スキーマの詳細については、「 [FileTable Schema](filetable-schema.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f589d-107">For information about the FileTable schema, see [FileTable Schema](filetable-schema.md).</span></span>  
  
 <span data-ttu-id="f589d-108">Transact-SQL または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、新しい FileTable を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="f589d-108">You can create a new FileTable by using Transact-SQL or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f589d-109">FileTable には固定スキーマがあるため、列の一覧を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f589d-109">Since a FileTable has a fixed schema, you do not have to specify a list of columns.</span></span> <span data-ttu-id="f589d-110">FileTable を作成するため、簡単な構文を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="f589d-110">The simple syntax for creating a FileTable lets you specify:</span></span>  
  
-   <span data-ttu-id="f589d-111">ディレクトリ名。</span><span class="sxs-lookup"><span data-stu-id="f589d-111">A directory name.</span></span> <span data-ttu-id="f589d-112">FileTable フォルダー階層において、このテーブル レベルのディレクトリは、データベース レベルで指定されたデータベース ディレクトリの子になると同時に、テーブルに格納されるファイルまたはデータベースの親になります。</span><span class="sxs-lookup"><span data-stu-id="f589d-112">In the FileTable folder hierarchy, this table-level directory becomes the child of the database directory specified at the database level, and the parent of the files or directories stored in the table.</span></span>  
  
-   <span data-ttu-id="f589d-113">FileTable の **Name** 列のファイル名に対して使用される照合順序の名前。</span><span class="sxs-lookup"><span data-stu-id="f589d-113">The name of the collation to be used for file names in the **Name** column of the FileTable.</span></span>  
  
-   <span data-ttu-id="f589d-114">自動的に作成される 3 つの主キーと一意の制約で使用する名前。</span><span class="sxs-lookup"><span data-stu-id="f589d-114">The names to be used for the 3 primary key and unique constraints that are automatically created.</span></span>  
  
###  <a name="how-to-create-a-filetable"></a><a name="HowToCreate"></a> <span data-ttu-id="f589d-115">方法:FileTable を作成する</span><span class="sxs-lookup"><span data-stu-id="f589d-115">How To: Create a FileTable</span></span>  
 <span data-ttu-id="f589d-116">**Transact-SQL を使用して FileTable を作成する**</span><span class="sxs-lookup"><span data-stu-id="f589d-116">**Create a FileTable by Using Transact-SQL**</span></span>  
 <span data-ttu-id="f589d-117">FileTable を作成するには、**AS FileTable** オプションを指定して [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) ステートメントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f589d-117">Create a FileTable by calling the [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) statement with the **AS FileTable** option.</span></span> <span data-ttu-id="f589d-118">FileTable には固定スキーマがあるため、列の一覧を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f589d-118">Since a FileTable has a fixed schema, you do not have to specify a list of columns.</span></span> <span data-ttu-id="f589d-119">新しい FileTable には次の設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f589d-119">You can specify the following settings for the new FileTable:</span></span>  
  
1.  <span data-ttu-id="f589d-120">**FILETABLE_DIRECTORY**。</span><span class="sxs-lookup"><span data-stu-id="f589d-120">**FILETABLE_DIRECTORY**.</span></span> <span data-ttu-id="f589d-121">FileTable に格納されたすべてのファイルおよびディレクトリのルート ディレクトリとなるディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="f589d-121">Specifies the directory that serves as the root directory for all the files and directories stored in the FileTable.</span></span> <span data-ttu-id="f589d-122">この名前は、データベース内のすべての FileTable ディレクトリ名の中で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f589d-122">This name should be unique among all the FileTable directory names in the database.</span></span> <span data-ttu-id="f589d-123">一意性の比較では、現在の照合順序の設定とは関係なく、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="f589d-123">Comparison for uniqueness is case-insensitive, regardless of the current collation settings.</span></span>  
  
    -   <span data-ttu-id="f589d-124">この値は、 **nvarchar(255)** のデータ型であり、 **Latin1_General_CI_AS_KS_WS**の固定の照合順序を使用します。</span><span class="sxs-lookup"><span data-stu-id="f589d-124">This value has a data type of **nvarchar(255)** and uses a fixed collation of **Latin1_General_CI_AS_KS_WS**.</span></span>  
  
    -   <span data-ttu-id="f589d-125">指定するディレクトリ名は、ファイル システムの有効なディレクトリ名に関する要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f589d-125">The directory name that you provide must comply with the requirements of the file system for a valid directory name.</span></span>  
  
    -   <span data-ttu-id="f589d-126">この名前は、データベース内のすべての FileTable ディレクトリ名の中で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f589d-126">This name should be unique among all the FileTable directory names in the database.</span></span> <span data-ttu-id="f589d-127">一意性の比較では、現在の照合順序の設定とは関係なく、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="f589d-127">Comparison for uniqueness is case-insensitive, regardless of the current collation settings.</span></span>  
  
    -   <span data-ttu-id="f589d-128">FileTable を作成するときにディレクトリ名を指定しなかった場合は、FileTable そのものの名前がディレクトリ名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-128">If you do not provide a directory name when you create the FileTable, then the name of the FileTable itself is used as the directory name.</span></span>  
  
2.  <span data-ttu-id="f589d-129">**FILETABLE_COLLATE_FILENAME**。</span><span class="sxs-lookup"><span data-stu-id="f589d-129">**FILETABLE_COLLATE_FILENAME**.</span></span> <span data-ttu-id="f589d-130">FileTable の **Name** 列に適用される照合順序の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f589d-130">Specifies the name of the collation to be applied to the **Name** column in the FileTable.</span></span>  
  
    1.  <span data-ttu-id="f589d-131">指定した照合順序は、Windows のファイル名のセマンティクスに準拠するために、 **大文字と小文字を区別しない** 設定にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f589d-131">The specified collation must be **case-insensitive** to comply with Windows file naming semantics.</span></span>  
  
    2.  <span data-ttu-id="f589d-132">**FILETABLE_COLLATE_FILENAME**の値を指定しない場合、または、 **database_default**を指定した場合は、現在のデータベースの照合順序が列に継承されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-132">If you do not provide a value for **FILETABLE_COLLATE_FILENAME**, or you specify **database_default**, the column inherits the collation of the current database.</span></span> <span data-ttu-id="f589d-133">現在のデータベースの照合順序で大文字と小文字が区別される場合は、エラーが発生し、 **CREATE TABLE** 操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="f589d-133">If the current database collation is case-sensitive, an error is raised and the **CREATE TABLE** operation fails.</span></span>  
  
3.  <span data-ttu-id="f589d-134">自動的に作成される 3 つの主キーと一意の制約で使用する名前を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f589d-134">You can also specify the names to be used for the 3 primary key and unique constraints that are automatically created.</span></span> <span data-ttu-id="f589d-135">名前を指定しなかった場合、このトピックで後述するように、システムで名前が自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-135">If you do not provide names, then the system generates names as described later in this topic.</span></span>  
  
    -   <span data-ttu-id="f589d-136">**FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="f589d-136">**FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME**</span></span>  
  
    -   <span data-ttu-id="f589d-137">**FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="f589d-137">**FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME**</span></span>  
  
    -   <span data-ttu-id="f589d-138">**FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="f589d-138">**FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME**</span></span>  
  
 <span data-ttu-id="f589d-139">**使用例**</span><span class="sxs-lookup"><span data-stu-id="f589d-139">**Examples**</span></span>  
  
 <span data-ttu-id="f589d-140">次の例では、新しい FileTable を作成し、 **FILETABLE_DIRECTORY** と **FILETABLE_COLLATE_FILENAME**の両方に対してユーザー定義の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="f589d-140">The following example creates a new FileTable and specifies user-defined values for both **FILETABLE_DIRECTORY** and **FILETABLE_COLLATE_FILENAME**.</span></span>  
  
```sql  
CREATE TABLE DocumentStore AS FileTable  
    WITH (   
          FileTable_Directory = 'DocumentTable',  
          FileTable_Collate_Filename = database_default  
         );  
GO  
```  
  
 <span data-ttu-id="f589d-141">次の例も、新しい FileTable を作成するものです。</span><span class="sxs-lookup"><span data-stu-id="f589d-141">The following example also creates a new FileTable.</span></span> <span data-ttu-id="f589d-142">ユーザー定義の値が指定されていないため、 **FILETABLE_DIRECTORY** の値が FileTable の名前に、 **FILETABLE_COLLATE_FILENAME** の値が database_default になります。また、主キーと一意の制約にはシステムで生成された名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-142">Since user-defined values are not specified, the value of **FILETABLE_DIRECTORY** becomes the name of the FileTable, the value of **FILETABLE_COLLATE_FILENAME** becomes database_default, and the primary key and unique contraints receive system-generated names.</span></span>  
  
```sql  
CREATE TABLE DocumentStore AS FileTable;  
GO  
```  
  
 <span data-ttu-id="f589d-143">**SQL Server Management Studio を使用して FileTable を作成する**</span><span class="sxs-lookup"><span data-stu-id="f589d-143">**Create a FileTable by Using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="f589d-144">オブジェクト エクスプローラーで、選択したデータベースのオブジェクトを展開し、 **[テーブル]** フォルダーを右クリックして **[新しい FileTable]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f589d-144">In Object Explorer, expand the objects under the selected database, then right-click on the **Tables** folder, and then select **New FileTable**.</span></span>  
  
 <span data-ttu-id="f589d-145">このオプションを選択すると、新しいスクリプト ウィンドウが開き、FileTable を作成するためにカスタマイズして実行できる Transact-SQL スクリプト テンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-145">This option opens a new script window which contains a Transact-SQL script template that you can customize and run to create a FileTable.</span></span> <span data-ttu-id="f589d-146">**[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** オプションを使用すると、スクリプトを簡単にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="f589d-146">Use the **Specify Values for Template Parameters** option on the **Query** menu to customize the script easily.</span></span>  
  
###  <a name="requirements-and-restrictions-for-creating-a-filetable"></a><a name="ReqCreate"></a> <span data-ttu-id="f589d-147">FileTable を作成するための要件と制限</span><span class="sxs-lookup"><span data-stu-id="f589d-147">Requirements and Restrictions for Creating a FileTable</span></span>  
  
-   <span data-ttu-id="f589d-148">既存のテーブルは、変更して FileTable に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="f589d-148">You cannot alter an existing table to convert it into a FileTable.</span></span>  
  
-   <span data-ttu-id="f589d-149">データベース レベルで前もって指定する親ディレクトリには、null ではない値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f589d-149">The parent directory previously specified at the database level must have a non-null value.</span></span> <span data-ttu-id="f589d-150">データベースレベルのディレクトリを指定する方法については、「 [FileTable の前提条件の有効化](enable-the-prerequisites-for-filetable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f589d-150">For information about specifying the database-level directory, see [Enable the Prerequisites for FileTable](enable-the-prerequisites-for-filetable.md).</span></span>  
  
-   <span data-ttu-id="f589d-151">FileTable には、FILESTREAM 列が含まれているため、有効な FILESTREAM ファイル グループが必要です。</span><span class="sxs-lookup"><span data-stu-id="f589d-151">A FileTable requires a valid FILESTREAM filegroup, since a FileTable contains a FILESTREAM column.</span></span> <span data-ttu-id="f589d-152">必要に応じて、FileTable を作成する **CREATE TABLE** コマンドの一部として、FILESTREAM ファイル グループを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f589d-152">You can optionally specify a valid FILESTREAM filegroup as part of the **CREATE TABLE** command for creating a FileTable.</span></span> <span data-ttu-id="f589d-153">ファイル グループが指定されていない場合、FileTable はデータベースの既定の FILESTREAM ファイル グループを使用します。</span><span class="sxs-lookup"><span data-stu-id="f589d-153">If you do not specify a filegroup, then the FileTable uses the default FILESTREAM filegroup for the database.</span></span> <span data-ttu-id="f589d-154">データベースに FILESTREAM ファイル グループがない場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f589d-154">If the database does not have a FILESTREAM filegroup, then an error is raised.</span></span>  
  
-   <span data-ttu-id="f589d-155">**CREATE TABLE...AS FILETABLE** ステートメントの一部としてテーブルの制約を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="f589d-155">You cannot create a table constraint as part of a **CREATE TABLE...AS FILETABLE** statement.</span></span> <span data-ttu-id="f589d-156">ただし、制約を追加するには、後で **ALTER TABLE** ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f589d-156">However you can add the constraint later by using an **ALTER TABLE** statement.</span></span>  
  
-   <span data-ttu-id="f589d-157">**tempdb** データベースまたはその他のシステム データベースに FileTable を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="f589d-157">You cannot create a FileTable in the **tempdb** database or in any of the other system databases.</span></span>  
  
-   <span data-ttu-id="f589d-158">一時テーブルとして、FileTable を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="f589d-158">You cannot create a FileTable as a temporary table.</span></span>  
  
##  <a name="altering-a-filetable"></a><a name="BasicsAlter"></a> <span data-ttu-id="f589d-159">FileTable の変更</span><span class="sxs-lookup"><span data-stu-id="f589d-159">Altering a FileTable</span></span>  
 <span data-ttu-id="f589d-160">FileTable は、定義済みおよび固定のスキーマがあるため、その列を追加または変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="f589d-160">Since a FileTable has a pre-defined and fixed schema, you cannot add or change its columns.</span></span> <span data-ttu-id="f589d-161">ただし、カスタム インデックス、トリガー、制約、およびその他のオプションを FileTable に追加することはできます。</span><span class="sxs-lookup"><span data-stu-id="f589d-161">However, you can add custom indexes, triggers, constraints, and other options to a FileTable.</span></span>  
  
 <span data-ttu-id="f589d-162">ALTER TABLE ステートメントを使用して FileTable 名前空間 (システム定義の制約を含む) を有効または無効にする方法の詳細については、「 [FileTable の管理](manage-filetables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f589d-162">For information about using the ALTER TABLE statement to enable or disable the FileTable namespace, including the system-defined constraints, see [Manage FileTables](manage-filetables.md).</span></span>  
  
###  <a name="how-to-change-the-directory-for-a-filetable"></a><a name="HowToChange"></a> <span data-ttu-id="f589d-163">方法:FileTable のディレクトリを変更する</span><span class="sxs-lookup"><span data-stu-id="f589d-163">How To: Change the Directory for a FileTable</span></span>  
 <span data-ttu-id="f589d-164">**Transact-SQL を使用して FileTable のディレクトリを変更する**</span><span class="sxs-lookup"><span data-stu-id="f589d-164">**Change the Directory for a FileTable by Using Transact-SQL**</span></span>  
 <span data-ttu-id="f589d-165">ALTER TABLE ステートメントを呼び出し、有効な新しい値を **FILETABLE_DIRECTORY** SET オプションに指定します。</span><span class="sxs-lookup"><span data-stu-id="f589d-165">Call the ALTER TABLE statement and provide a valid new value for the **FILETABLE_DIRECTORY** SET option.</span></span>  
  
 <span data-ttu-id="f589d-166">**例**</span><span class="sxs-lookup"><span data-stu-id="f589d-166">**Example**</span></span>  
  
```sql  
ALTER TABLE filetable_name  
    SET ( FILETABLE_DIRECTORY = N'directory_name' );  
GO  
```  
  
 <span data-ttu-id="f589d-167">**SQL Server Management Studio を使用して FileTable のディレクトリを変更する**</span><span class="sxs-lookup"><span data-stu-id="f589d-167">**Change the Directory for a FileTable by Using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="f589d-168">オブジェクト エクスプローラーで、FileTable を右クリックし、 **[プロパティ]** をクリックして、 **[テーブルのプロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="f589d-168">In Object Explorer, right-click on the FileTable and select **Properties** to open the **Table Properties** dialog box.</span></span> <span data-ttu-id="f589d-169">**[FileTable]** ページで、 **[FileTable ディレクトリ名]** に新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="f589d-169">On the **FileTable** page, enter a new value for **FileTable directory name**.</span></span>  
  
###  <a name="requirements-and-restrictions-for-altering-a-filetable"></a><a name="ReqAlter"></a> <span data-ttu-id="f589d-170">FileTable を変更するための要件と制限</span><span class="sxs-lookup"><span data-stu-id="f589d-170">Requirements and Restrictions for Altering a FileTable</span></span>  
  
-   <span data-ttu-id="f589d-171">**FILETABLE_COLLATE_FILENAME**の値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="f589d-171">You cannot alter the value of **FILETABLE_COLLATE_FILENAME**.</span></span>  
  
-   <span data-ttu-id="f589d-172">FileTable のシステムで定義された列を変更、削除、または無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f589d-172">You cannot change, drop, or disable the system-defined columns of a FileTable.</span></span>  
  
-   <span data-ttu-id="f589d-173">新しいユーザー列、計算列、または保存される計算列を FileTable に追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="f589d-173">You cannot add new user columns, computed columns, or persisted computed columns to a FileTable.</span></span>  
  
##  <a name="dropping-a-filetable"></a><a name="BasicsDrop"></a> <span data-ttu-id="f589d-174">FileTable の削除</span><span class="sxs-lookup"><span data-stu-id="f589d-174">Dropping a FileTable</span></span>  
 <span data-ttu-id="f589d-175">FileTable を削除するには、[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) ステートメントの通常の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f589d-175">You can drop a FileTable by using the ordinary syntax for the [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="f589d-176">FileTable を削除すると、次のオブジェクトも削除されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-176">When you drop a FileTable, the following objects are also dropped:</span></span>  
  
-   <span data-ttu-id="f589d-177">FileTable のすべての列に加え、インデックス、制約、トリガーなどテーブルに関連付けられているすべてのオブジェクトが削除されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-177">All the columns of the FileTable and all the objects associated with the table, such as indexes, constraints, and triggers, are also dropped.</span></span>  
  
-   <span data-ttu-id="f589d-178">FileTable ディレクトリと、その下位にあったサブディレクトリも、データベースの FILESTREAM ファイルとディレクトリ階層から消失します。</span><span class="sxs-lookup"><span data-stu-id="f589d-178">The FileTable directory and the sub-directories that it contained disappear from the FILESTREAM file and directory hierarchy of the database.</span></span>  
  
 <span data-ttu-id="f589d-179">FileTable のファイルの名前空間内に開いているファイル ハンドルがある場合、DROP TABLE コマンドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="f589d-179">The DROP TABLE command fails if there are open file handles in the FileTable's file namespace.</span></span> <span data-ttu-id="f589d-180">開いているハンドルを閉じる方法の詳細については、「 [FileTable の管理](manage-filetables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f589d-180">For information about closing open handles, see [Manage FileTables](manage-filetables.md).</span></span>  
  
##  <a name="other-database-objects-are-created-when-you-create-a-filetable"></a><a name="BasicsOtherObjects"></a> <span data-ttu-id="f589d-181">FileTable を作成したときに作成されるその他のデータベース オブジェクト</span><span class="sxs-lookup"><span data-stu-id="f589d-181">Other Database Objects Are Created When You Create a FileTable</span></span>  
 <span data-ttu-id="f589d-182">新しい FileTable を作成すると、システム定義のインデックスと制約もいくつか作成されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-182">When you create a new FileTable, some system-defined indexes and constraints are also created.</span></span> <span data-ttu-id="f589d-183">これらのオブジェクトを変更または削除することはできません。これらは、FileTable 自体が削除されると一緒に削除されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-183">You cannot alter or drop these objects; they disappear only when the FileTable itself is dropped.</span></span> <span data-ttu-id="f589d-184">これらのオブジェクトの一覧を表示するには、カタログ ビュー [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql) に対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="f589d-184">To see the list of these objects, query the catalog view [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql).</span></span>  
  
```sql  
--View all objects for all filetables, unsorted  
SELECT * FROM sys.filetable_system_defined_objects;  
GO  
  
--View sorted list with friendly names  
SELECT OBJECT_NAME(parent_object_id) AS 'FileTable', OBJECT_NAME(object_id) AS 'System-defined Object'  
    FROM sys.filetable_system_defined_objects  
    ORDER BY FileTable, 'System-defined Object';  
GO  
```  
  
 <span data-ttu-id="f589d-185">**新しい FileTable を作成するときに作成されるインデックス**</span><span class="sxs-lookup"><span data-stu-id="f589d-185">**Indexes that are created when you create a new FileTable**</span></span>  
 <span data-ttu-id="f589d-186">新しい FileTable を作成すると、次に示すシステム定義のインデックスも作成されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-186">When you create a new FileTable, the following system-defined indexes are also created:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f589d-187">**[列]**</span><span class="sxs-lookup"><span data-stu-id="f589d-187">**Columns**</span></span>|<span data-ttu-id="f589d-188">**[インデックスの種類]**</span><span class="sxs-lookup"><span data-stu-id="f589d-188">**Index type**</span></span>|  
|<span data-ttu-id="f589d-189">[path_locator] ASC</span><span class="sxs-lookup"><span data-stu-id="f589d-189">[path_locator] ASC</span></span>|<span data-ttu-id="f589d-190">主キー、非クラスター化</span><span class="sxs-lookup"><span data-stu-id="f589d-190">Primary Key, nonclustered</span></span>|  
|<span data-ttu-id="f589d-191">[parent_path_locator] ASC、</span><span class="sxs-lookup"><span data-stu-id="f589d-191">[parent_path_locator] ASC,</span></span><br /><br /> <span data-ttu-id="f589d-192">[name] ASC</span><span class="sxs-lookup"><span data-stu-id="f589d-192">[name] ASC</span></span>|<span data-ttu-id="f589d-193">一意、非クラスター化</span><span class="sxs-lookup"><span data-stu-id="f589d-193">Unique, nonclustered</span></span>|  
|<span data-ttu-id="f589d-194">[stream_id] ASC</span><span class="sxs-lookup"><span data-stu-id="f589d-194">[stream_id] ASC</span></span>|<span data-ttu-id="f589d-195">一意、非クラスター化</span><span class="sxs-lookup"><span data-stu-id="f589d-195">Unique, nonclustered</span></span>|  
  
 <span data-ttu-id="f589d-196">**新しい FileTable を作成するときに作成される制約**</span><span class="sxs-lookup"><span data-stu-id="f589d-196">**Constraints that are created when you create a new FileTable**</span></span>  
 <span data-ttu-id="f589d-197">新しい FileTable を作成すると、次に示すシステム定義の制約も作成されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-197">When you create a new FileTable, the following system-defined constraints are also created:</span></span>  
  
|<span data-ttu-id="f589d-198">制約</span><span class="sxs-lookup"><span data-stu-id="f589d-198">Constraints</span></span>|<span data-ttu-id="f589d-199">強制</span><span class="sxs-lookup"><span data-stu-id="f589d-199">Enforces</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="f589d-200">次の列の既定の制約</span><span class="sxs-lookup"><span data-stu-id="f589d-200">Default constraints on the following columns:</span></span><br /><br /> <span data-ttu-id="f589d-201">**creation_time**</span><span class="sxs-lookup"><span data-stu-id="f589d-201">**creation_time**</span></span> <br /> <span data-ttu-id="f589d-202">**is_archive**</span><span class="sxs-lookup"><span data-stu-id="f589d-202">**is_archive**</span></span> <br /> <span data-ttu-id="f589d-203">**is_directory**</span><span class="sxs-lookup"><span data-stu-id="f589d-203">**is_directory**</span></span> <br /> <span data-ttu-id="f589d-204">**is_hidden**</span><span class="sxs-lookup"><span data-stu-id="f589d-204">**is_hidden**</span></span> <br /> <span data-ttu-id="f589d-205">**is_offline**</span><span class="sxs-lookup"><span data-stu-id="f589d-205">**is_offline**</span></span> <br /> <span data-ttu-id="f589d-206">**is_readonly**</span><span class="sxs-lookup"><span data-stu-id="f589d-206">**is_readonly**</span></span> <br /> <span data-ttu-id="f589d-207">**is_system**</span><span class="sxs-lookup"><span data-stu-id="f589d-207">**is_system**</span></span> <br /> <span data-ttu-id="f589d-208">**is_temporary**</span><span class="sxs-lookup"><span data-stu-id="f589d-208">**is_temporary**</span></span> <br /> <span data-ttu-id="f589d-209">**last_access_time**</span><span class="sxs-lookup"><span data-stu-id="f589d-209">**last_access_time**</span></span> <br /> <span data-ttu-id="f589d-210">**last_write_time**</span><span class="sxs-lookup"><span data-stu-id="f589d-210">**last_write_time**</span></span> <br /> <span data-ttu-id="f589d-211">**path_locator**</span><span class="sxs-lookup"><span data-stu-id="f589d-211">**path_locator**</span></span> <br /> <span data-ttu-id="f589d-212">**stream_id**</span><span class="sxs-lookup"><span data-stu-id="f589d-212">**stream_id**</span></span>|<span data-ttu-id="f589d-213">システム定義の既定の制約によって、指定した列に既定値が適用されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-213">The system-defined default constraints enforce default values for the specified columns.</span></span>|  
|<span data-ttu-id="f589d-214">CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="f589d-214">Check constraints</span></span>|<span data-ttu-id="f589d-215">システム定義の CHECK 制約によって、次の要件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="f589d-215">The system-defined check constraints enforce the following requirements:</span></span><br /><br /> <span data-ttu-id="f589d-216">有効なファイル名。</span><span class="sxs-lookup"><span data-stu-id="f589d-216">Valid filenames.</span></span><br /><br /> <span data-ttu-id="f589d-217">有効なファイル属性。</span><span class="sxs-lookup"><span data-stu-id="f589d-217">Valid file attributes.</span></span><br /><br /> <span data-ttu-id="f589d-218">親オブジェクトをディレクトリにする。</span><span class="sxs-lookup"><span data-stu-id="f589d-218">Parent object must be a directory.</span></span><br /><br /> <span data-ttu-id="f589d-219">名前空間の階層は、ファイル操作中にロックされる。</span><span class="sxs-lookup"><span data-stu-id="f589d-219">Namespace hierarchy is locked during file manipulation.</span></span>|  
  
 <span data-ttu-id="f589d-220">**システム定義の制約の名前付け規則**</span><span class="sxs-lookup"><span data-stu-id="f589d-220">**Naming convention for the system-defined constraints**</span></span>  
 <span data-ttu-id="f589d-221">上で説明したシステム定義の制約は、 **\<constraintType>_\<tablename>[\_\<columnname>]\_\<uniquifier>** という形式で名前が付けられます。ここで、</span><span class="sxs-lookup"><span data-stu-id="f589d-221">The system-defined constraints described above are named in the format **\<constraintType>_\<tablename>[\_\<columnname>]\_\<uniquifier>** where:</span></span>  
  
-   <span data-ttu-id="f589d-222">*<constraint_type>* は CK (CHECK 制約)、DF (DEFAULT 制約)、FK (外部キー)、PK (主キー)、または UQ (一意制約) です。</span><span class="sxs-lookup"><span data-stu-id="f589d-222">*<constraint_type>* is CK (check constraint), DF (default constraint), FK (foreign key), PK (primary key), or UQ (unique constraint).</span></span>  
  
-   <span data-ttu-id="f589d-223">*\<uniquifier>* は、名前を一意にするためにシステムによって生成された文字列です。</span><span class="sxs-lookup"><span data-stu-id="f589d-223">*\<uniquifier>* is a system-generated string to make the name unique.</span></span> <span data-ttu-id="f589d-224">この文字列には、通常、FileTable の名前と一意の識別子が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f589d-224">This string may contain the FileTable name and a unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f589d-225">参照</span><span class="sxs-lookup"><span data-stu-id="f589d-225">See Also</span></span>  
 [<span data-ttu-id="f589d-226">FileTable の管理</span><span class="sxs-lookup"><span data-stu-id="f589d-226">Manage FileTables</span></span>](manage-filetables.md)  
  
  
