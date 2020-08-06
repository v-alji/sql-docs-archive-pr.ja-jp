---
title: データベースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], creating
- database creation [SQL Server], SQL Server Management Studio
- creating databases
ms.assetid: 4c4beea2-6cbc-4352-9db6-49ea8130bb64
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe42e394482e3abf4d87c00c6e79ee84db6ba278
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640080"
---
# <a name="create-a-database"></a><span data-ttu-id="95bcc-102">データベースの作成</span><span class="sxs-lookup"><span data-stu-id="95bcc-102">Create a Database</span></span>
  <span data-ttu-id="95bcc-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データベースを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-103">This topic describes how to create a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="95bcc-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="95bcc-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="95bcc-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="95bcc-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="95bcc-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="95bcc-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="95bcc-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="95bcc-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="95bcc-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="95bcc-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="95bcc-109">Security</span><span class="sxs-lookup"><span data-stu-id="95bcc-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="95bcc-110">**以下を使用してデータベースを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="95bcc-110">**To create a database, using:**</span></span>  
  
     [<span data-ttu-id="95bcc-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="95bcc-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="95bcc-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="95bcc-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="95bcc-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="95bcc-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="95bcc-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="95bcc-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="95bcc-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスには、最大 32,767 個のデータベースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="95bcc-115">A maximum of 32,767 databases can be specified on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="95bcc-116">前提条件</span><span class="sxs-lookup"><span data-stu-id="95bcc-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="95bcc-117">CREATE DATABASE ステートメントは自動コミット モード (既定のトランザクション管理モード) で実行する必要があり、明示的または暗黙的なトランザクション モードでは許可されません。</span><span class="sxs-lookup"><span data-stu-id="95bcc-117">The CREATE DATABASE statement must run in autocommit mode (the default transaction management mode) and is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="95bcc-118">推奨事項</span><span class="sxs-lookup"><span data-stu-id="95bcc-118">Recommendations</span></span>  
  
-   <span data-ttu-id="95bcc-119">[master](master-database.md) データベースは、ユーザー データベースが作成、変更、または削除されるたびにバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="95bcc-119">The [master](master-database.md) database should be backed up whenever a user database is created, modified, or dropped.</span></span>  
  
-   <span data-ttu-id="95bcc-120">データベースを作成する際に、データ ファイルのサイズは、データベースに記述されるデータの最大量を基に可能な限り大きく設定しておきます。</span><span class="sxs-lookup"><span data-stu-id="95bcc-120">When you create a database, make the data files as large as possible based on the maximum amount of data you expect in the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="95bcc-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="95bcc-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="95bcc-122">Permissions</span><span class="sxs-lookup"><span data-stu-id="95bcc-122">Permissions</span></span>  
 <span data-ttu-id="95bcc-123">master データベースの CREATE DATABASE 権限か、CREATE ANY DATABASE 権限または ALTER ANY DATABASE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="95bcc-123">Requires CREATE DATABASE permission in the master database, or requires CREATE ANY DATABASE, or ALTER ANY DATABASE permission.</span></span>  
  
 <span data-ttu-id="95bcc-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス上のディスク使用量を管理するため、通常、データベースを作成する権限をいくつかのログイン アカウントに制限します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-124">To maintain control over disk use on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], permission to create databases is typically limited to a few login accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="95bcc-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="95bcc-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-database"></a><span data-ttu-id="95bcc-126">データベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="95bcc-126">To create a database</span></span>  
  
1.  <span data-ttu-id="95bcc-127">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-127">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="95bcc-128">**[データベース]** を右クリックし、 **[新しいデータベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95bcc-128">Right-click **Databases**, and then click **New Database**.</span></span>  
  
3.  <span data-ttu-id="95bcc-129">**[新しいデータベース]** ダイアログ ボックスで、データベース名を入力します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-129">In **New Database**, enter a database name.</span></span>  
  
4.  <span data-ttu-id="95bcc-130">すべての既定値をそのまま使用してデータベースを作成するには、 **[OK]** をクリックします。変更する場合は、次に示すオプションの手順を続けて行います。</span><span class="sxs-lookup"><span data-stu-id="95bcc-130">To create the database by accepting all default values, click **OK**; otherwise, continue with the following optional steps.</span></span>  
  
5.  <span data-ttu-id="95bcc-131">所有者名を変更するには、参照ボタン **[...]** をクリックし、別の所有者を選択します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-131">To change the owner name, click (**...**) to select another owner.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95bcc-132">**以降のバージョンでは、すべてのユーザー データベースでフルテキストが有効になっているため、** [フルテキスト インデックスを使用する] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]オプションは常にオンに設定され、淡色表示されます。</span><span class="sxs-lookup"><span data-stu-id="95bcc-132">The **Use full-text indexing** option is always checked and dimmed because, beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], all user databases are full-text enabled.</span></span>  
  
6.  <span data-ttu-id="95bcc-133">プライマリ データ ファイルとトランザクション ログ ファイルの既定値を変更するには、 **[データベース ファイル]** グリッドで該当するセルをクリックし、新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-133">To change the default values of the primary data and transaction log files, in the **Database files** grid, click the appropriate cell and enter the new value.</span></span> <span data-ttu-id="95bcc-134">詳細については、「 [データベースに対するデータ ファイルまたはログ ファイルの追加](add-data-or-log-files-to-a-database.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="95bcc-134">For more information, see [Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md).</span></span>  
  
7.  <span data-ttu-id="95bcc-135">データベースの照合順序を変更するには、 **[オプション]** ページをクリックし、[照合順序] ボックスの一覧から照合順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-135">To change the collation of the database, select the **Options** page, and then select a collation from the list.</span></span>  
  
8.  <span data-ttu-id="95bcc-136">復旧モデルを変更するには、 **[オプション]** ページをクリックし、[復旧モデル] ボックスの一覧から復旧モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-136">To change the recovery model, select the **Options** page and select a recovery model from the list.</span></span>  
  
9. <span data-ttu-id="95bcc-137">データベースのオプションを変更するには、 **[オプション]** ページをクリックし、データベースのオプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-137">To change database options, select the **Options** page, and then modify the database options.</span></span> <span data-ttu-id="95bcc-138">各オプションの詳細については、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95bcc-138">For a description of each option, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
10. <span data-ttu-id="95bcc-139">新しいファイル グループを追加するには、 **[ファイル グループ]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="95bcc-139">To add a new filegroup, click the **Filegroups** page.</span></span> <span data-ttu-id="95bcc-140">**[追加]** をクリックし、ファイル グループを表す新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-140">Click **Add** and then enter the values for the filegroup.</span></span>  
  
11. <span data-ttu-id="95bcc-141">拡張プロパティをデータベースに追加するには、 **[拡張プロパティ]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="95bcc-141">To add an extended property to the database, select the **Extended Properties** page.</span></span>  
  
    1.  <span data-ttu-id="95bcc-142">**[名前]** 列に、拡張プロパティを表す名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-142">In the **Name** column, enter a name for the extended property.</span></span>  
  
    2.  <span data-ttu-id="95bcc-143">**[値]** 列に、拡張プロパティのテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-143">In the **Value** column, enter the extended property text.</span></span> <span data-ttu-id="95bcc-144">たとえば、データベースを説明する 1 つ以上のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-144">For example, enter one or more statements that describe the database.</span></span>  
  
12. <span data-ttu-id="95bcc-145">データベースを作成するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95bcc-145">To create the database, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="95bcc-146">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="95bcc-146">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database"></a><span data-ttu-id="95bcc-147">データベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="95bcc-147">To create a database</span></span>  
  
1.  <span data-ttu-id="95bcc-148">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="95bcc-149">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95bcc-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="95bcc-150">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95bcc-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="95bcc-151">この例では、 `Sales`データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="95bcc-151">This example creates the database `Sales`.</span></span> <span data-ttu-id="95bcc-152">PRIMARY キーワードが使用されていないので、最初のファイル (`Sales`_`dat`) がプライマリ ファイルになります。</span><span class="sxs-lookup"><span data-stu-id="95bcc-152">Because the keyword PRIMARY is not used, the first file (`Sales`_`dat`) becomes the primary file.</span></span> <span data-ttu-id="95bcc-153">`Sales`\_`dat` ファイルの SIZE パラメーターに MB も KB も指定されていないため、ファイルは MB を使用し、メガバイト単位で割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="95bcc-153">Because neither MB nor KB is specified in the SIZE parameter for the `Sales`\_`dat` file, it uses MB and is allocated in megabytes.</span></span> <span data-ttu-id="95bcc-154">`Sales`\_`log` ファイルは、 `MB` パラメーターに `SIZE` サフィックスが明示的に指定されているため、メガバイト単位で割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="95bcc-154">The `Sales`\_`log` file is allocated in megabytes because the `MB` suffix is explicitly stated in the `SIZE` parameter.</span></span>  
  
```sql  
USE master ;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
 <span data-ttu-id="95bcc-155">詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95bcc-155">For more examples, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95bcc-156">参照</span><span class="sxs-lookup"><span data-stu-id="95bcc-156">See Also</span></span>  
 <span data-ttu-id="95bcc-157">[Database Files and Filegroups](database-files-and-filegroups.md) </span><span class="sxs-lookup"><span data-stu-id="95bcc-157">[Database Files and Filegroups](database-files-and-filegroups.md) </span></span>  
 <span data-ttu-id="95bcc-158">[データベースのデタッチとアタッチ &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="95bcc-158">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="95bcc-159">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="95bcc-159">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="95bcc-160">データベースに対するデータ ファイルまたはログ ファイルの追加</span><span class="sxs-lookup"><span data-stu-id="95bcc-160">Add Data or Log Files to a Database</span></span>](add-data-or-log-files-to-a-database.md)  
  
  
