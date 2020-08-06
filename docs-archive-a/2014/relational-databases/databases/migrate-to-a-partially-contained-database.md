---
title: 部分的包含データベースへの移行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, migrating to
ms.assetid: 90faac38-f79e-496d-b589-e8b2fe01c562
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6142d46dc0540e5998fa66d463538d1453a17d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742161"
---
# <a name="migrate-to-a-partially-contained-database"></a><span data-ttu-id="b7be1-102">Migrate to a Partially Contained Database</span><span class="sxs-lookup"><span data-stu-id="b7be1-102">Migrate to a Partially Contained Database</span></span>
  <span data-ttu-id="b7be1-103">このトピックでは、部分的包含データベース モデルへの変更を準備する方法を説明し、移行手順を示します。</span><span class="sxs-lookup"><span data-stu-id="b7be1-103">This topic discusses how to prepare to change to the partially contained database model and then provides the migration steps.</span></span>  
  
 <span data-ttu-id="b7be1-104">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="b7be1-104">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="b7be1-105">データベースを移行する準備</span><span class="sxs-lookup"><span data-stu-id="b7be1-105">Preparing to Migrate a Database</span></span>](#prepare)  
  
-   [<span data-ttu-id="b7be1-106">包含データベースの有効化</span><span class="sxs-lookup"><span data-stu-id="b7be1-106">Enable Contained Databases</span></span>](#enable)  
  
-   [<span data-ttu-id="b7be1-107">部分的包含へのデータベースの変換</span><span class="sxs-lookup"><span data-stu-id="b7be1-107">Converting a Database to Partially Contained</span></span>](#convert)  
  
-   [<span data-ttu-id="b7be1-108">包含データベース ユーザーへのユーザーの移行</span><span class="sxs-lookup"><span data-stu-id="b7be1-108">Migrating Users to Contained Database Users</span></span>](#users)  
  
##  <a name="preparing-to-migrate-a-database"></a><a name="prepare"></a> <span data-ttu-id="b7be1-109">データベースを移行する準備</span><span class="sxs-lookup"><span data-stu-id="b7be1-109">Preparing to Migrate a Database</span></span>  
 <span data-ttu-id="b7be1-110">データベースを部分的包含データベース モデルに移行することを検討している場合は、次の点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="b7be1-110">Review the following items when considering migrating a database to the partially contained database model.</span></span>  
  
-   <span data-ttu-id="b7be1-111">部分的包含データベース モデルを理解している。</span><span class="sxs-lookup"><span data-stu-id="b7be1-111">You should understand the partially contained database model.</span></span> <span data-ttu-id="b7be1-112">詳細については、「 [包含データベース](contained-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7be1-112">For more information, see [Contained Databases](contained-databases.md).</span></span>  
  
-   <span data-ttu-id="b7be1-113">部分的包含データベースに固有のリスクを理解している。</span><span class="sxs-lookup"><span data-stu-id="b7be1-113">You should understand risks that are unique to partially contained databases.</span></span> <span data-ttu-id="b7be1-114">詳細については、「 [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7be1-114">For more information, see [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md).</span></span>  
  
-   <span data-ttu-id="b7be1-115">包含データベースは、レプリケーション、変更データ キャプチャ、または変更の追跡をサポートしていない。</span><span class="sxs-lookup"><span data-stu-id="b7be1-115">Contained databases do not support replication, change data capture, or change tracking.</span></span> <span data-ttu-id="b7be1-116">データベースがこれらの機能を使用していないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b7be1-116">Confirm the database does not use these features.</span></span>  
  
-   <span data-ttu-id="b7be1-117">部分的包含データベースに関して変更されているデータベース機能の一覧を確認する。</span><span class="sxs-lookup"><span data-stu-id="b7be1-117">Review the list of database features that are modified for partially contained databases.</span></span> <span data-ttu-id="b7be1-118">詳細については、「[変更された機能 &#40;包含データベース&#41;](modified-features-contained-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7be1-118">For more information, see [Modified Features &#40;Contained Database&#41;](modified-features-contained-database.md).</span></span>  
  
-   <span data-ttu-id="b7be1-119">[sys.dm_db_uncontained_entitiess &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql) クエリを実行し、データベース内の非包含オブジェクトまたは機能を検索します。</span><span class="sxs-lookup"><span data-stu-id="b7be1-119">Query [sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql) to find uncontained objects or features in the database.</span></span> <span data-ttu-id="b7be1-120">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7be1-120">For more information, see.</span></span>  
  
-   <span data-ttu-id="b7be1-121">**database_uncontained_usage** XEvent を監視し、非包含機能がいつ使用されるかを確認する。</span><span class="sxs-lookup"><span data-stu-id="b7be1-121">Monitor the **database_uncontained_usage** XEvent to see when uncontained features are used.</span></span>  
  
##  <a name="enable-contained-databases"></a><a name="enable"></a> <span data-ttu-id="b7be1-122">包含データベースの有効化</span><span class="sxs-lookup"><span data-stu-id="b7be1-122">Enable Contained Databases</span></span>  
 <span data-ttu-id="b7be1-123">包含データベースを作成するためには、あらかじめ [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスで包含データベースを有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7be1-123">Contained databases must be enabled on the instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], before contained databases can be created.</span></span>  
  
### <a name="enabling-contained-databases-using-transact-sql"></a><span data-ttu-id="b7be1-124">Transact SQL を使用して包含データベースを有効にする</span><span class="sxs-lookup"><span data-stu-id="b7be1-124">Enabling Contained Databases Using Transact-SQL</span></span>  
 <span data-ttu-id="b7be1-125">次の例では、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスで包含データベースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b7be1-125">The following example enables contained databases on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
```sql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE ;  
GO  
```  
  
#### <a name="enabling-contained-databases-using-management-studio"></a><span data-ttu-id="b7be1-126">Management Studio を使用して包含データベースを有効にする</span><span class="sxs-lookup"><span data-stu-id="b7be1-126">Enabling Contained Databases Using Management Studio</span></span>  
 <span data-ttu-id="b7be1-127">次の例では、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスで包含データベースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b7be1-127">The following example enables contained databases on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
1.  <span data-ttu-id="b7be1-128">オブジェクト エクスプローラーでサーバー名を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7be1-128">In Object Explorer, right-click the server name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b7be1-129">**[詳細設定]** ページの **[包含]** セクションで、 **[包含データベースを有効にする]** オプションを **True**に設定します。</span><span class="sxs-lookup"><span data-stu-id="b7be1-129">On the **Advanced** page, in the **Containment** section, set the **Enable Contained Databases** option to **True**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="converting-a-database-to-partially-contained"></a><a name="convert"></a> <span data-ttu-id="b7be1-130">部分的包含へのデータベースの変換</span><span class="sxs-lookup"><span data-stu-id="b7be1-130">Converting a Database to Partially Contained</span></span>  
 <span data-ttu-id="b7be1-131">データベースを包含データベースに変換するには、 **CONTAINMENT** オプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="b7be1-131">A database is converted to a contained database by changing the **CONTAINMENT** option.</span></span>  
  
### <a name="converting-a-database-to-partially-contained-using-transact-sql"></a><span data-ttu-id="b7be1-132">Transact-SQL を使用してデータベースを部分的包含に変換する</span><span class="sxs-lookup"><span data-stu-id="b7be1-132">Converting a Database to Partially Contained Using Transact-SQL</span></span>  
 <span data-ttu-id="b7be1-133">次の例では、 `Accounting` という名前のデータベースを部分的包含データベースに変換します。</span><span class="sxs-lookup"><span data-stu-id="b7be1-133">The following example converts a database named `Accounting` to a partially contained database.</span></span>  
  
```sql  
USE [master]  
GO  
ALTER DATABASE [Accounting] SET CONTAINMENT = PARTIAL  
GO  
```  
  
### <a name="converting-a-database-to-partially-contained-using-management-studio"></a><span data-ttu-id="b7be1-134">Management Studio を使用してデータベースを部分的包含に変換する</span><span class="sxs-lookup"><span data-stu-id="b7be1-134">Converting a Database to Partially contained Using Management Studio</span></span>  
 <span data-ttu-id="b7be1-135">次の例では、データベースを部分的包含データベースに変換します。</span><span class="sxs-lookup"><span data-stu-id="b7be1-135">The following example converts a database to a partially contained database.</span></span>  
  
1.  <span data-ttu-id="b7be1-136">オブジェクト エクスプローラーで、 **[データベース]** を展開し、変換するデータベースを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7be1-136">In Object Explorer, expand **Databases**, right-click the database to be converted, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b7be1-137">**[オプション]** ページで、 **[包含の種類]** オプションを **[部分]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="b7be1-137">On the **Options** page, change the **Containment type** option to **Partial**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="migrating-users-to-contained-database-users"></a><a name="users"></a> <span data-ttu-id="b7be1-138">包含データベース ユーザーへのユーザーの移行</span><span class="sxs-lookup"><span data-stu-id="b7be1-138">Migrating Users to Contained Database Users</span></span>  
 <span data-ttu-id="b7be1-139">次の例では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに基づくすべてのユーザーを、パスワードを持つ包含データベース ユーザーに移行します。</span><span class="sxs-lookup"><span data-stu-id="b7be1-139">The following example migrates all users that are based on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins to contained database users with passwords.</span></span> <span data-ttu-id="b7be1-140">有効になっていないログインは除外します。</span><span class="sxs-lookup"><span data-stu-id="b7be1-140">The example excludes logins that are not enabled.</span></span> <span data-ttu-id="b7be1-141">この例は、包含データベースで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7be1-141">The example must be executed in the contained database.</span></span>  
  
```sql  
DECLARE @username sysname ;  
DECLARE user_cursor CURSOR  
    FOR   
        SELECT dp.name   
        FROM sys.database_principals AS dp  
        JOIN sys.server_principals AS sp   
        ON dp.sid = sp.sid  
        WHERE dp.authentication_type = 1 AND sp.is_disabled = 0;  
OPEN user_cursor  
FETCH NEXT FROM user_cursor INTO @username  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        EXECUTE sp_migrate_user_to_contained   
        @username = @username,  
        @rename = N'keep_name',  
        @disablelogin = N'disable_login';  
    FETCH NEXT FROM user_cursor INTO @username  
    END  
CLOSE user_cursor ;  
DEALLOCATE user_cursor ;  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7be1-142">参照</span><span class="sxs-lookup"><span data-stu-id="b7be1-142">See Also</span></span>  
 <span data-ttu-id="b7be1-143">[包含データベース](contained-databases.md) </span><span class="sxs-lookup"><span data-stu-id="b7be1-143">[Contained Databases](contained-databases.md) </span></span>  
 <span data-ttu-id="b7be1-144">[sp_migrate_user_to_contained &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b7be1-144">[sp_migrate_user_to_contained &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql) </span></span>  
 [<span data-ttu-id="b7be1-145">sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b7be1-145">sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql)  
  
  
