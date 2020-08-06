---
title: データベースのインポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb11b5c257007872e92d3f0a7eadb3e46b4969cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742233"
---
# <a name="attach-a-database"></a><span data-ttu-id="d93e2-102">データベースのインポート</span><span class="sxs-lookup"><span data-stu-id="d93e2-102">Attach a Database</span></span>
  <span data-ttu-id="d93e2-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベースをアタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-103">This topic describes how to attach a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d93e2-104">この機能は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのコピー、移動、またはアップグレードに使用できます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-104">You can use this feature to copy, move, or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="d93e2-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d93e2-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d93e2-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d93e2-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d93e2-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="d93e2-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="d93e2-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="d93e2-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d93e2-109">Security</span><span class="sxs-lookup"><span data-stu-id="d93e2-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d93e2-110">**以下を使用してデータベースをアタッチするには:**</span><span class="sxs-lookup"><span data-stu-id="d93e2-110">**To Attach a Database by using:**</span></span>  
  
     [<span data-ttu-id="d93e2-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d93e2-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d93e2-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d93e2-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d93e2-113">**補足情報:**  [データベースをアップグレードした後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d93e2-113">**Follow Up:**  [After Upgrading a Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d93e2-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="d93e2-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d93e2-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="d93e2-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="d93e2-116">最初にデータベースをデタッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d93e2-116">The database must first be detached.</span></span> <span data-ttu-id="d93e2-117">デタッチされていないデータベースをアタッチしようとすると、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-117">Attempting to attach a database that has not been detached will return an error.</span></span> <span data-ttu-id="d93e2-118">詳細については、「 [データベースのデタッチ](detach-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93e2-118">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
-   <span data-ttu-id="d93e2-119">データベースをアタッチするときは、すべてのデータ ファイル (MDF ファイルおよび LDF ファイル) を利用できる状態にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d93e2-119">When you attach a database, all data files (MDF and LDF files) must be available.</span></span> <span data-ttu-id="d93e2-120">データベースを最初に作成したときか最後にアタッチしたときとデータ ファイルのパスが異なる場合、ファイルの現在のパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d93e2-120">If any data file has a different path from when the database was first created or last attached, you must specify the current path of the file.</span></span>  
  
-   <span data-ttu-id="d93e2-121">データベースをアタッチするときに、MDF ファイルと LDF ファイルが異なるディレクトリに配置されており、いずれかのパスに \\\\?\GlobalRoot が含まれている場合は、操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-121">When you attach a database, if MDF and LDF files are located in different directories and one of the paths includes \\\\?\GlobalRoot, the operation will fail.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d93e2-122">推奨事項</span><span class="sxs-lookup"><span data-stu-id="d93e2-122">Recommendations</span></span>  
<span data-ttu-id="d93e2-123">`ALTER DATABASE`デタッチとアタッチを使用するのではなく、計画された再配置手順を使用してデータベースを移動することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d93e2-123">We recommend that you move databases by using the `ALTER DATABASE` planned relocation procedure, instead of using detach and attach.</span></span> <span data-ttu-id="d93e2-124">詳細については、「 [ユーザー データベースの移動](move-user-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93e2-124">For more information, see [Move User Databases](move-user-databases.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d93e2-125">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d93e2-125">Security</span></span>  
<span data-ttu-id="d93e2-126">ファイル アクセス許可は、データベースのデタッチやアタッチなど、さまざまなデータベース操作中に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-126">File access permissions are set during a number of database operations, including detaching or attaching a database.</span></span> <span data-ttu-id="d93e2-127">データベースをデタッチおよびアタッチするたびに設定されるファイル権限の詳細については、 [オンライン ブックの「](https://technet.microsoft.com/library/ms189128.aspx) データ ファイルとログ ファイルのセキュリティ保護 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93e2-127">For information about file permissions that are set whenever a database is detached and attached, see [Securing Data and Log Files](https://technet.microsoft.com/library/ms189128.aspx) in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online.</span></span>  
  
<span data-ttu-id="d93e2-128">不明なソースや信頼されていないソースからデータベースをアタッチまたは復元しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d93e2-128">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="d93e2-129">こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d93e2-129">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="d93e2-130">不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-130">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span> <span data-ttu-id="d93e2-131">データベースのアタッチ、およびデータベースのアタッチ時にメタデータに対して行われる変更の詳細については、「[データベースのデタッチとアタッチ &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93e2-131">For more information about attaching databases and information about changes that are made to metadata when you attach a database, see [Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d93e2-132">Permissions</span><span class="sxs-lookup"><span data-stu-id="d93e2-132">Permissions</span></span>  
<span data-ttu-id="d93e2-133">`CREATE DATABASE`、`CREATE ANY DATABASE`、または `ALTER ANY DATABASE` アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="d93e2-133">Requires `CREATE DATABASE`, `CREATE ANY DATABASE`, or `ALTER ANY DATABASE` permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d93e2-134">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d93e2-134">Using SQL Server Management Studio</span></span>  
  
### <a name="to-attach-a-database"></a><span data-ttu-id="d93e2-135">データベースをアタッチするには</span><span class="sxs-lookup"><span data-stu-id="d93e2-135">To Attach a Database</span></span>  
  
1.  <span data-ttu-id="d93e2-136">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-136">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d93e2-137">**[データベース]** を右クリックし、 **[アタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d93e2-137">Right-click **Databases** and click **Attach**.</span></span>  
  
3.  <span data-ttu-id="d93e2-138">アタッチするデータベースを指定するには、 **[データベースのインポート]** ダイアログ ボックスで **[追加]** をクリックし、 **[データベース ファイルの検索]** ダイアログ ボックスで目的のデータベースが常駐するディスク ドライブを選択します。次に、そのディレクトリ ツリーを展開し、そのデータベースの .mdf ファイルを選択します。たとえば、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-138">In the **Attach Databases** dialog box, to specify the database to be attached, click **Add**; and in the **Locate Database Files** dialog box, select the disk drive where the database resides and expand the directory tree to find and select the .mdf file of the database; for example:</span></span>  
  
     `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > <span data-ttu-id="d93e2-139">既にアタッチされているデータベースを選択しようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-139">Trying to select a database that is already attached generates an error.</span></span>  
  
     <span data-ttu-id="d93e2-140">**[アタッチするデータベース]**</span><span class="sxs-lookup"><span data-stu-id="d93e2-140">**Databases to attach**</span></span>  
     <span data-ttu-id="d93e2-141">選択されたデータベースに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-141">Displays information about the selected databases.</span></span>  
  
     \<no column header>  
     <span data-ttu-id="d93e2-142">アタッチ操作の状態を示すアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-142">Displays an icon indicating the status of the attach operation.</span></span> <span data-ttu-id="d93e2-143">表示されるアイコンの種類は、下の **[状態]** の説明に示します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-143">The possible icons are described in the **Status** description, below).</span></span>  
  
     <span data-ttu-id="d93e2-144">**[MDF ファイルの場所]**</span><span class="sxs-lookup"><span data-stu-id="d93e2-144">**MDF File Location**</span></span>  
     <span data-ttu-id="d93e2-145">選択した MDF ファイルのパスとファイル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-145">Displays the path and file name of the selected MDF file.</span></span>  
  
     <span data-ttu-id="d93e2-146">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="d93e2-146">**Database Name**</span></span>  
     <span data-ttu-id="d93e2-147">データベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-147">Displays the name of the database.</span></span>  
  
     <span data-ttu-id="d93e2-148">**[次の名前でアタッチ]**</span><span class="sxs-lookup"><span data-stu-id="d93e2-148">**Attach As**</span></span>  
     <span data-ttu-id="d93e2-149">データベースを別の名前でアタッチする場合に、その名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-149">Optionally, specifies a different name for the database to attach as.</span></span>  
  
     <span data-ttu-id="d93e2-150">**所有者**</span><span class="sxs-lookup"><span data-stu-id="d93e2-150">**Owner**</span></span>  
     <span data-ttu-id="d93e2-151">データベースの所有者のドロップダウン リストです。これを使用して、必要に応じて別の所有者を選択できます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-151">Provides a drop-down list of possible database owners from which you can optionally select a different owner.</span></span>  
  
     <span data-ttu-id="d93e2-152">**状態**</span><span class="sxs-lookup"><span data-stu-id="d93e2-152">**Status**</span></span>  
     <span data-ttu-id="d93e2-153">次の表に示すように、データベースの状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-153">Displays the status of the database according to the following table.</span></span>  
  
    |<span data-ttu-id="d93e2-154">アイコン</span><span class="sxs-lookup"><span data-stu-id="d93e2-154">Icon</span></span>|<span data-ttu-id="d93e2-155">状態テキスト</span><span class="sxs-lookup"><span data-stu-id="d93e2-155">Status text</span></span>|<span data-ttu-id="d93e2-156">説明</span><span class="sxs-lookup"><span data-stu-id="d93e2-156">Description</span></span>|  
    |----------|-----------------|-----------------|  
    |<span data-ttu-id="d93e2-157">(アイコンなし)</span><span class="sxs-lookup"><span data-stu-id="d93e2-157">(No icon)</span></span>|<span data-ttu-id="d93e2-158">(テキストなし)</span><span class="sxs-lookup"><span data-stu-id="d93e2-158">(No text)</span></span>|<span data-ttu-id="d93e2-159">このオブジェクトのアタッチ操作が開始されていないか、保留されています。</span><span class="sxs-lookup"><span data-stu-id="d93e2-159">Attach operation has not been started or may be pending for this object.</span></span> <span data-ttu-id="d93e2-160">これは、ダイアログ ボックスを開いたときの既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="d93e2-160">This is the default when the dialog is opened.</span></span>|  
    |<span data-ttu-id="d93e2-161">緑の右向き三角形</span><span class="sxs-lookup"><span data-stu-id="d93e2-161">Green, right-pointing triangle</span></span>|<span data-ttu-id="d93e2-162">進行中</span><span class="sxs-lookup"><span data-stu-id="d93e2-162">In progress</span></span>|<span data-ttu-id="d93e2-163">アタッチ操作が開始されましたが、完了していません。</span><span class="sxs-lookup"><span data-stu-id="d93e2-163">Attach operation has been started but it is not complete.</span></span>|  
    |<span data-ttu-id="d93e2-164">緑のチェック マーク</span><span class="sxs-lookup"><span data-stu-id="d93e2-164">Green check mark</span></span>|<span data-ttu-id="d93e2-165">Success</span><span class="sxs-lookup"><span data-stu-id="d93e2-165">Success</span></span>|<span data-ttu-id="d93e2-166">オブジェクトは正常にアタッチされました。</span><span class="sxs-lookup"><span data-stu-id="d93e2-166">The object has been attached successfully.</span></span>|  
    |<span data-ttu-id="d93e2-167">赤い丸の中に白い×印</span><span class="sxs-lookup"><span data-stu-id="d93e2-167">Red circle containing a white cross</span></span>|<span data-ttu-id="d93e2-168">エラー</span><span class="sxs-lookup"><span data-stu-id="d93e2-168">Error</span></span>|<span data-ttu-id="d93e2-169">アタッチ操作でエラーが発生し、正常に完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="d93e2-169">Attach operation encountered an error and did not complete successfully.</span></span>|  
    |<span data-ttu-id="d93e2-170">4 つに区切られた丸印 (左右の領域が黒、上下の領域が白)</span><span class="sxs-lookup"><span data-stu-id="d93e2-170">Circle containing two black quadrants (on left and right) and two white quadrants (on top and bottom)</span></span>|<span data-ttu-id="d93e2-171">停止済み</span><span class="sxs-lookup"><span data-stu-id="d93e2-171">Stopped</span></span>|<span data-ttu-id="d93e2-172">ユーザーがアタッチ操作を停止したため、正常に完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="d93e2-172">Attach operation was not completed successfully because the user stopped the operation.</span></span>|  
    |<span data-ttu-id="d93e2-173">丸の中に反時計回りの矢印</span><span class="sxs-lookup"><span data-stu-id="d93e2-173">Circle containing a curved arrow pointing counter-clockwise</span></span>|<span data-ttu-id="d93e2-174">[ロールバックされました]</span><span class="sxs-lookup"><span data-stu-id="d93e2-174">Rolled Back</span></span>|<span data-ttu-id="d93e2-175">アタッチ操作は正常に完了しましたが、他のオブジェクトのアタッチ中にエラーが発生したため、ロールバックされました。</span><span class="sxs-lookup"><span data-stu-id="d93e2-175">Attach operation was successful but it has been rolled back due to an error during attachment of another object.</span></span>|  
  
     <span data-ttu-id="d93e2-176">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="d93e2-176">**Message**</span></span>  
     <span data-ttu-id="d93e2-177">空白のメッセージ、または "ファイルが見つかりません" のハイパーリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-177">Displays either a blank message or a "File not found" hyperlink.</span></span>  
  
     <span data-ttu-id="d93e2-178">**追加**</span><span class="sxs-lookup"><span data-stu-id="d93e2-178">**Add**</span></span>  
     <span data-ttu-id="d93e2-179">主な必須データベース ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-179">Find the necessary main database files.</span></span> <span data-ttu-id="d93e2-180">ユーザーが .mdf ファイルを選択した場合、 **[アタッチするデータベース]** グリッドの対応するフィールドに、対応する情報が自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-180">When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="d93e2-181">**Remove**</span><span class="sxs-lookup"><span data-stu-id="d93e2-181">**Remove**</span></span>  
     <span data-ttu-id="d93e2-182">選択したファイルを **[アタッチするデータベース]** グリッドから削除します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-182">Removes the selected file from the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="d93e2-183">**"** *<database_name>* **" データベースの詳細**</span><span class="sxs-lookup"><span data-stu-id="d93e2-183">**"** *<database_name>* **" database details**</span></span>  
     <span data-ttu-id="d93e2-184">デタッチするファイルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-184">Displays the names of the files to be attached.</span></span> <span data-ttu-id="d93e2-185">ファイルのパス名を確認または変更するには、**参照**ボタン ( **[...]** ) をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="d93e2-185">To verify or change the pathname of a file, click the **Browse** button (**...**).</span></span>  
  
    > [!NOTE]  
    > <span data-ttu-id="d93e2-186">ファイルが存在しなかった場合、 **[メッセージ]** 列に "見つかりませんでした" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-186">If a file does not exist, the **Message** column displays "Not found."</span></span> <span data-ttu-id="d93e2-187">ログ ファイルが見つからない場合は、ログ ファイルが別のディレクトリに置かれているか、削除されています。</span><span class="sxs-lookup"><span data-stu-id="d93e2-187">If a log file is not found, it exists in another directory or has been deleted.</span></span> <span data-ttu-id="d93e2-188">**[データベースの詳細]** グリッドでファイル パスを更新し、正しい場所を指定するか、そのログ ファイルをグリッドから削除します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-188">You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid.</span></span> <span data-ttu-id="d93e2-189">.ndf データ ファイルが見つからない場合、グリッドのパスを更新して、正しい場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d93e2-189">If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.</span></span>  
  
     <span data-ttu-id="d93e2-190">**[元のファイル名]**</span><span class="sxs-lookup"><span data-stu-id="d93e2-190">**Original File Name**</span></span>  
     <span data-ttu-id="d93e2-191">データベースに属している、アタッチされたファイルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-191">Displays the name of the attached file belonging to the database.</span></span>  
  
     <span data-ttu-id="d93e2-192">**[ファイルの種類]**</span><span class="sxs-lookup"><span data-stu-id="d93e2-192">**File Type**</span></span>  
     <span data-ttu-id="d93e2-193">ファイルの種類を表します。 **[データ]** または **[ログ]** になります。</span><span class="sxs-lookup"><span data-stu-id="d93e2-193">Indicates the type of file, **Data** or **Log**.</span></span>  
  
     <span data-ttu-id="d93e2-194">**[現在のファイル パス]**</span><span class="sxs-lookup"><span data-stu-id="d93e2-194">**Current File Path**</span></span>  
     <span data-ttu-id="d93e2-195">選択されているデータベース ファイルのパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-195">Displays the path to the selected database file.</span></span> <span data-ttu-id="d93e2-196">このパスは手作業で編集できます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-196">The path can be edited manually.</span></span>  
  
     <span data-ttu-id="d93e2-197">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="d93e2-197">**Message**</span></span>  
     <span data-ttu-id="d93e2-198">空白のメッセージ、または **"ファイルが見つかりません"** ハイパーリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-198">Displays either a blank message or a "**File not found**" hyperlink.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d93e2-199">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d93e2-199">Using Transact-SQL</span></span>  
  
### <a name="to-attach-a-database"></a><span data-ttu-id="d93e2-200">データベースをアタッチするには</span><span class="sxs-lookup"><span data-stu-id="d93e2-200">To attach a database</span></span>  
  
1.  <span data-ttu-id="d93e2-201">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-201">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d93e2-202">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d93e2-202">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d93e2-203">[CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql)ステートメントを close と共に使用し `FOR ATTACH` ます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-203">Use the [CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the `FOR ATTACH` close.</span></span>  
  
     <span data-ttu-id="d93e2-204">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d93e2-204">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d93e2-205">この例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースのファイルをアタッチし、データベースの名前を `MyAdventureWorks`に変更します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-205">This example attaches the files of the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database and renames the database to `MyAdventureWorks`.</span></span>  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > <span data-ttu-id="d93e2-206">また、 [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) ストアド プロシージャまたは [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) ストアド プロシージャを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-206">Alternatively, you can use the [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) or [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) stored procedure.</span></span> <span data-ttu-id="d93e2-207">ただし、これらのプロシージャは、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の今後のバージョンでは削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="d93e2-207">However, these procedures will be removed in a future version of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d93e2-208">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="d93e2-208">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="d93e2-209">CREATE DATABASE を使用することをお勧めします...代わりに ATTACH を使用します。</span><span class="sxs-lookup"><span data-stu-id="d93e2-209">We recommend that you use CREATE DATABASE ... FOR ATTACH instead.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a><span data-ttu-id="d93e2-210">補足情報: SQL Server データベースのアップグレード後</span><span class="sxs-lookup"><span data-stu-id="d93e2-210">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="d93e2-211">後 attach メソッドを使用してデータベースをアップグレードすると、データベースは直ちに使用できるようになり、自動的にアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-211">fter you upgrade a database by using the attach method, the database becomes available immediately and is automatically upgraded.</span></span> <span data-ttu-id="d93e2-212">データベースにフルテキスト インデックスがある場合、アップグレード プロセスでは、 **"フルテキスト アップグレード オプション"** サーバー プロパティの設定に応じて、インポート、リセット、または再構築が行われます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-212">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **Full-Text Upgrade Option** server property.</span></span> <span data-ttu-id="d93e2-213">アップグレード オプションが **[インポート]** または **[再構築]** に設定されている場合、アップグレード中はフルテキスト インデックスを使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d93e2-213">If the upgrade option is set to **Import** or **Rebuild**, the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="d93e2-214">インデックスを作成するデータ量によって、インポートには数時間、再構築には最大でその 10 倍の時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="d93e2-214">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="d93e2-215">なお、アップグレード オプションが **[インポート]** に設定されており、フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。</span><span class="sxs-lookup"><span data-stu-id="d93e2-215">Note also that when the upgrade option is set to **Import**, if a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span>  
  
<span data-ttu-id="d93e2-216">アップグレード前のユーザー データベースの互換性レベルが 100 以上の場合は、アップグレード後も互換性レベルは変わりません。</span><span class="sxs-lookup"><span data-stu-id="d93e2-216">If the compatibility level of a user database is 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="d93e2-217">アップグレード前の互換性レベルが 90 の場合、アップグレードされたデータベースの互換性レベルは 100 に設定されます。これは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でサポートされている下限の互換性レベルです。</span><span class="sxs-lookup"><span data-stu-id="d93e2-217">If the compatibility level is 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="d93e2-218">詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93e2-218">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93e2-219">参照</span><span class="sxs-lookup"><span data-stu-id="d93e2-219">See Also</span></span>  
 <span data-ttu-id="d93e2-220">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d93e2-220">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="d93e2-221">データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="d93e2-221">Detach a Database</span></span>](detach-a-database.md)  
  
  
