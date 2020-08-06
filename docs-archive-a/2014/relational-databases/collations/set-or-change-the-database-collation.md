---
title: データベースの照合順序の設定または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], database
- database collations [SQL Server]
ms.assetid: 1379605c-1242-4ac8-ab1b-e2a2b5b1f895
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d7f7c3e3ddba7ba0ea9701993dbe0fad3a8d975
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645660"
---
# <a name="set-or-change-the-database-collation"></a><span data-ttu-id="f6182-102">データベースの照合順序の設定または変更</span><span class="sxs-lookup"><span data-stu-id="f6182-102">Set or Change the Database Collation</span></span>
  <span data-ttu-id="f6182-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でデータベースの照合順序を設定および変更する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f6182-103">This topic describes how set and change the database collation in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f6182-104">照合順序を指定しない場合、サーバーの照合順序が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f6182-104">If no collation is specified, the server collation is used.</span></span>  
  
 <span data-ttu-id="f6182-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f6182-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f6182-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f6182-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f6182-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f6182-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f6182-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="f6182-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="f6182-109">Security</span><span class="sxs-lookup"><span data-stu-id="f6182-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f6182-110">**データベースの照合順序を設定または変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="f6182-110">**To set or change the database collation, using:**</span></span>  
  
     [<span data-ttu-id="f6182-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6182-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f6182-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6182-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f6182-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="f6182-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f6182-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f6182-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f6182-115">Windows Unicode 専用の照合順序は、COLLATE 句で `nchar`、`nvarchar`、および `ntext` の各データ型を列レベルと式レベルのデータに適用する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f6182-115">Windows Unicode-only collations can only be used with the COLLATE clause to apply collations to the `nchar`, `nvarchar`, and `ntext` data types on column level and expression-level data.</span></span> <span data-ttu-id="f6182-116">データベースまたはサーバー インスタンスの照合順序を変更するために、COLLATE 句で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f6182-116">They cannot be used with the COLLATE clause to change the collation of a database or server instance.</span></span>  
  
-   <span data-ttu-id="f6182-117">指定した照合順序、または参照先のオブジェクトで使用される照合順序で、Windows でサポートされていないコード ページが使用されていると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] でエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f6182-117">If the specified collation or the collation used by the referenced object uses a code page that is not supported by Windows, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] displays an error.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f6182-118">推奨事項</span><span class="sxs-lookup"><span data-stu-id="f6182-118">Recommendations</span></span>  
  
-   <span data-ttu-id="f6182-119">サポートされる照合順序名は、「 [Windows 照合順序名 &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) 」と「 [SQL Server 照合順序名 &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)」で確認できます。または、 [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) システム関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f6182-119">You can find the supported collation names in [Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) and [SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql); or you can use the [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) system function.</span></span>  
  
-   <span data-ttu-id="f6182-120">データベースの照合順序を変更すると、次の変更が行われます。</span><span class="sxs-lookup"><span data-stu-id="f6182-120">When you change the database collation, you change the following:</span></span>  
  
    -   <span data-ttu-id="f6182-121">システム テーブル内の `char` 型、`varchar` 型、`text` 型、`nchar` 型、`nvarchar` 型、または `ntext` 型の列はすべて、新しい照合順序に変更されます。</span><span class="sxs-lookup"><span data-stu-id="f6182-121">Any `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` columns in system tables are changed to the new collation.</span></span>  
  
    -   <span data-ttu-id="f6182-122">ストアド プロージャおよびユーザー定義関数で使用されている `char` 型、`varchar` 型、`text` 型、`nchar` 型、`nvarchar` 型、または `ntext` 型の既存のパラメーターおよびスカラー値の戻り値はすべて、新しい照合順序に変更されます。</span><span class="sxs-lookup"><span data-stu-id="f6182-122">All existing `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` parameters and scalar return values for stored procedures and user-defined functions are changed to the new collation.</span></span>  
  
    -   <span data-ttu-id="f6182-123">`char` 型、`varchar` 型、`text` 型、`nchar` 型、`nvarchar` 型、または `ntext` 型のシステム データ型およびこれらを基にしたユーザー定義データ型はすべて、新しい既定の照合順序に変更されます。</span><span class="sxs-lookup"><span data-stu-id="f6182-123">The `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` system data types, and all user-defined data types based on these system data types, are changed to the new default collation.</span></span>  
  
-   <span data-ttu-id="f6182-124">ユーザー データベースに作成する新しいオブジェクトの照合順序は、 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) ステートメントの COLLATE 句を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="f6182-124">You can change the collation of any new objects that are created in a user database by using the COLLATE clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="f6182-125">このステートメントを実行しても、既存のユーザー定義テーブルの列の照合順序は変わりません。</span><span class="sxs-lookup"><span data-stu-id="f6182-125">This statement does not change the collation of the columns in any existing user-defined tables.</span></span> <span data-ttu-id="f6182-126">[ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)の COLLATE 句で変更することができます。</span><span class="sxs-lookup"><span data-stu-id="f6182-126">These can be changed by using the COLLATE clause of [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f6182-127">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f6182-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f6182-128">Permissions</span><span class="sxs-lookup"><span data-stu-id="f6182-128">Permissions</span></span>  
 <span data-ttu-id="f6182-129">CREATE DATABASE</span><span class="sxs-lookup"><span data-stu-id="f6182-129">CREATE DATABASE</span></span>  
 <span data-ttu-id="f6182-130">**Master**データベースの create database 権限、または CREATE any database 権限または ALTER any database 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f6182-130">Requires CREATE DATABASE permission in the **master** database, or requires CREATE ANY DATABASE, or ALTER ANY DATABASE permission.</span></span>  
  
 <span data-ttu-id="f6182-131">ALTER DATABASE</span><span class="sxs-lookup"><span data-stu-id="f6182-131">ALTER DATABASE</span></span>  
 <span data-ttu-id="f6182-132">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f6182-132">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f6182-133">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f6182-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-or-change-the-database-collation"></a><span data-ttu-id="f6182-134">データベースの照合順序を設定または変更するには</span><span class="sxs-lookup"><span data-stu-id="f6182-134">To set or change the database collation</span></span>  
  
1.  <span data-ttu-id="f6182-135">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続して、そのインスタンスを展開します。次に、 **[データベース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="f6182-135">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="f6182-136">新しいデータベースを作成する場合は、 **[データベース]** を右クリックし、 **[新しいデータベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6182-136">If you are creating a new database, right-click **Databases** and then click **New Database**.</span></span> <span data-ttu-id="f6182-137">既定の照合順序を使用しない場合は、 **[オプション]** ページをクリックし、 **[照合順序]** ボックスの一覧から照合順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="f6182-137">If you do not want the default collation, click the **Options** page, and select a collation from the **Collation** drop-down list.</span></span>  
  
     <span data-ttu-id="f6182-138">データベースが既に存在する場合は、使用するデータベースを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6182-138">Alternatively, if the database already exists, right-click the database that you want and click **Properties**.</span></span> <span data-ttu-id="f6182-139">**[オプション]** ページをクリックし、 **[照合順序]** ボックスの一覧から照合順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="f6182-139">Click the **Options** page, and select a collation from the **Collation** drop-down list.</span></span>  
  
3.  <span data-ttu-id="f6182-140">終了したら **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6182-140">After you are finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f6182-141">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f6182-141">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-database-collation"></a><span data-ttu-id="f6182-142">データベースの照合順序を設定するには</span><span class="sxs-lookup"><span data-stu-id="f6182-142">To set the database collation</span></span>  
  
1.  <span data-ttu-id="f6182-143">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="f6182-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f6182-144">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6182-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f6182-145">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6182-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f6182-146">この例は、 [COLLATE](/sql/t-sql/statements/collations) 句を使用して照合順序名を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f6182-146">This example shows how to use the [COLLATE](/sql/t-sql/statements/collations) clause to specify a collation name.</span></span> <span data-ttu-id="f6182-147">この例は、 `MyOptionsTest` 照合順序を使用する `Latin1_General_100_CS_AS_SC` を作成します。</span><span class="sxs-lookup"><span data-stu-id="f6182-147">The example creates the database `MyOptionsTest` that uses the `Latin1_General_100_CS_AS_SC` collation.</span></span> <span data-ttu-id="f6182-148">データベースを作成したら、 `SELECT` ステートメントを実行して設定を検証します。</span><span class="sxs-lookup"><span data-stu-id="f6182-148">After you create the database, execute the `SELECT` statement to verify the setting.</span></span>  
  
```sql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE Latin1_General_100_CS_AS_SC;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
#### <a name="to-change-the-database-collation"></a><span data-ttu-id="f6182-149">データベースの照合順序を変更するには</span><span class="sxs-lookup"><span data-stu-id="f6182-149">To change the database collation</span></span>  
  
1.  <span data-ttu-id="f6182-150">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="f6182-150">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f6182-151">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6182-151">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f6182-152">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6182-152">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f6182-153">この例は、 [ALTER DATABASE](/sql/t-sql/statements/collations) ステートメントで [COLLATE](/sql/t-sql/statements/alter-database-transact-sql) 句を使用して照合順序名を変更する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f6182-153">This example shows how to use the [COLLATE](/sql/t-sql/statements/collations) clause in an [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement to change the collation name.</span></span> <span data-ttu-id="f6182-154">`SELECT` ステートメントを実行して変更を確認します。</span><span class="sxs-lookup"><span data-stu-id="f6182-154">Execute the `SELECT` statement to verify the change.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE MyOptionsTest  
COLLATE French_CI_AS ;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6182-155">参照</span><span class="sxs-lookup"><span data-stu-id="f6182-155">See Also</span></span>  
 <span data-ttu-id="f6182-156">[照合順序と Unicode のサポート](collation-and-unicode-support.md) </span><span class="sxs-lookup"><span data-stu-id="f6182-156">[Collation and Unicode Support](collation-and-unicode-support.md) </span></span>  
 <span data-ttu-id="f6182-157">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6182-157">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span></span>  
 <span data-ttu-id="f6182-158">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6182-158">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="f6182-159">[SQL Server 照合順序名 &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6182-159">[SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span></span>  
 <span data-ttu-id="f6182-160">[Windows 照合順序名 &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6182-160">[Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) </span></span>  
 <span data-ttu-id="f6182-161">[COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations) </span><span class="sxs-lookup"><span data-stu-id="f6182-161">[COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations) </span></span>  
 <span data-ttu-id="f6182-162">[照合順序の優先順位 &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6182-162">[Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span></span>  
 <span data-ttu-id="f6182-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6182-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="f6182-164">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6182-164">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="f6182-165">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6182-165">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="f6182-166">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f6182-166">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
