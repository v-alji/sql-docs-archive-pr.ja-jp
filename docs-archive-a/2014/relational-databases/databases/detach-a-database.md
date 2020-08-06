---
title: データベースのデタッチ | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.detachdatabase.f1
helpviewer_keywords:
- database detaching [SQL Server]
- detaching databases [SQL Server]
ms.assetid: f63d4107-13e4-4bfe-922d-5e4f712e472d
author: stevestein
ms.author: sstein
ms.openlocfilehash: b8acc809b881012d18f78995bb8e521337fb02ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645631"
---
# <a name="detach-a-database"></a><span data-ttu-id="b6d34-102">データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="b6d34-102">Detach a Database</span></span>
  <span data-ttu-id="b6d34-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベースをデタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6d34-103">This topic describes how to detach a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b6d34-104">デタッチされたファイルはそのまま残り、FOR ATTACH または FOR ATTACH_REBUILD_LOG オプションを指定した CREATE DATABASE によって再アタッチできます。</span><span class="sxs-lookup"><span data-stu-id="b6d34-104">The detached files remain and can be reattached by using CREATE DATABASE with the FOR ATTACH or FOR ATTACH_REBUILD_LOG option.</span></span> <span data-ttu-id="b6d34-105">ファイルを別のサーバーに移動し、そこにアタッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b6d34-105">The files can be moved to another server and attached there.</span></span>  
  
 <span data-ttu-id="b6d34-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b6d34-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b6d34-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="b6d34-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b6d34-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b6d34-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b6d34-109">Security</span><span class="sxs-lookup"><span data-stu-id="b6d34-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b6d34-110">**データベースをデタッチする方法:**</span><span class="sxs-lookup"><span data-stu-id="b6d34-110">**To detach a database, using:**</span></span>  
  
     [<span data-ttu-id="b6d34-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6d34-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b6d34-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6d34-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b6d34-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="b6d34-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b6d34-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b6d34-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b6d34-115">制限事項と制約事項の一覧については、「 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)のデータベースをデタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6d34-115">For a list of limitations and restrictions, see [Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b6d34-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b6d34-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b6d34-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="b6d34-117">Permissions</span></span>  
 <span data-ttu-id="b6d34-118">db_owner 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="b6d34-118">Requires membership in the db_owner fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b6d34-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b6d34-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-detach-a-database"></a><span data-ttu-id="b6d34-120">データベースをデタッチするには</span><span class="sxs-lookup"><span data-stu-id="b6d34-120">To detach a database</span></span>  
  
1.  <span data-ttu-id="b6d34-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続して、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="b6d34-121">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand the instance.</span></span>  
  
2.  <span data-ttu-id="b6d34-122">**[データベース]** を展開し、デタッチするユーザー データベースの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6d34-122">Expand **Databases**, and select the name of the user database you want to detach.</span></span>  
  
3.  <span data-ttu-id="b6d34-123">データベース名を右クリックして **[タスク]** をポイントし、 **[デタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d34-123">Right-click the database name, point to **Tasks**, and then click **Detach**.</span></span> <span data-ttu-id="b6d34-124">**[データベースのデタッチ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d34-124">The **Detach Database** dialog box appears.</span></span>  
  
     <span data-ttu-id="b6d34-125">**[デタッチするデータベース]**</span><span class="sxs-lookup"><span data-stu-id="b6d34-125">**Databases to detach**</span></span>  
     <span data-ttu-id="b6d34-126">デタッチするデータベースを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b6d34-126">Lists the databases to detach.</span></span>  
  
     <span data-ttu-id="b6d34-127">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="b6d34-127">**Database Name**</span></span>  
     <span data-ttu-id="b6d34-128">デタッチするデータベースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="b6d34-128">Displays the name of the database to be detached.</span></span>  
  
     <span data-ttu-id="b6d34-129">**[接続の削除]**</span><span class="sxs-lookup"><span data-stu-id="b6d34-129">**Drop Connections**</span></span>  
     <span data-ttu-id="b6d34-130">指定したデータベースへの接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="b6d34-130">Disconnect connections to the specified database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b6d34-131">アクティブな接続があるデータベースをデタッチすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b6d34-131">You cannot detach a database with active connections.</span></span>  
  
     <span data-ttu-id="b6d34-132">**統計の更新**</span><span class="sxs-lookup"><span data-stu-id="b6d34-132">**Update Statistics**</span></span>  
     <span data-ttu-id="b6d34-133">既定では、データベースをデタッチしても、古い最適化統計情報が保持されます。既存の最適化統計情報を更新するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="b6d34-133">By default, the detach operation retains any out-of-date optimization statistics when detaching the database; to update the existing optimization statistics, click this check box.</span></span>  
  
     <span data-ttu-id="b6d34-134">**[フルテキスト カタログの保持]**</span><span class="sxs-lookup"><span data-stu-id="b6d34-134">**Keep Full-Text Catalogs**</span></span>  
     <span data-ttu-id="b6d34-135">既定では、デタッチ操作を行っても、データベースに関連付けられたフルテキスト カタログが保持されます。</span><span class="sxs-lookup"><span data-stu-id="b6d34-135">By default, the detach operation keeps any full-text catalogs that are associated with the database.</span></span> <span data-ttu-id="b6d34-136">これらのカタログを削除するには、 **[フルテキスト カタログの保持]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="b6d34-136">To remove them, clear the **Keep Full-Text Catalogs** check box.</span></span> <span data-ttu-id="b6d34-137">このオプションは、データベースを [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]からアップグレードする場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d34-137">This option appears only when you are upgrading a database from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="b6d34-138">**状態**</span><span class="sxs-lookup"><span data-stu-id="b6d34-138">**Status**</span></span>  
     <span data-ttu-id="b6d34-139">次のどちらかの状態が表示されます: **[準備完了]** または **[準備ができていません]** 。</span><span class="sxs-lookup"><span data-stu-id="b6d34-139">Displays one of the following states: **Ready** or **Not ready**.</span></span>  
  
     <span data-ttu-id="b6d34-140">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="b6d34-140">**Message**</span></span>  
     <span data-ttu-id="b6d34-141">**[メッセージ]** 列に、次のようにデータベースに関する情報が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b6d34-141">The **Message** column may display information about the database, as follows:</span></span>  
  
    -   <span data-ttu-id="b6d34-142">データベースがレプリケーションに含まれている場合、 **[状態]** は **[準備ができていません]** になり、 **[メッセージ]** 列に **[データベースがレプリケートされました]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6d34-142">When a database is involved with replication, the **Status** is **Not ready** and the **Message** column displays **Database replicated**.</span></span>  
  
    -   <span data-ttu-id="b6d34-143">データベースに 1 つまたは複数のアクティブな接続がある場合、 **[状態]** は **[準備ができていません]** になり、 **[メッセージ]** 列に _[<アクティブな接続数>_ **のアクティブな接続]** と表示されます。例: **[1 のアクティブな接続]** 。</span><span class="sxs-lookup"><span data-stu-id="b6d34-143">When a database has one or more active connections, the **Status** is **Not ready** and the **Message** column displays _<number_of_active_connections>_**Active connection(s)** - for example: **1 Active connection(s)**.</span></span> <span data-ttu-id="b6d34-144">データベースをデタッチするには、 **[接続の削除]** を選択してアクティブな接続を切断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6d34-144">Before you can detach the database, you need to disconnect any active connections by selecting **Drop Connections**.</span></span>  
  
     <span data-ttu-id="b6d34-145">メッセージについてより詳しい情報を得るには、ハイパーリンクのテキストをクリックして利用状況モニターを開きます。</span><span class="sxs-lookup"><span data-stu-id="b6d34-145">To obtain more information about a message, click the hyperlinked text to open Activity Monitor.</span></span>  
  
4.  <span data-ttu-id="b6d34-146">データベースをデタッチする準備ができたら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d34-146">When you are ready to detach the database, click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6d34-147">新たにデタッチしたデータベースは、表示を最新の情報に更新するまで、オブジェクト エクスプローラーの **[データベース]** ノード内に表示されたままです。</span><span class="sxs-lookup"><span data-stu-id="b6d34-147">The newly detached database will remain visible in the **Databases** node of Object Explorer until the view is refreshed.</span></span> <span data-ttu-id="b6d34-148">ビューはいつでも更新できます。[オブジェクト エクスプローラー] ウィンドウをクリックし、メニュー バーの **[表示]** メニューで **[最新の情報に更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b6d34-148">You can refresh the view at any time: Click in the Object Explorer pane, and from the menu bar select **View** and then **Refresh**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b6d34-149">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b6d34-149">Using Transact-SQL</span></span>  
  
#### <a name="to-detach-a-database"></a><span data-ttu-id="b6d34-150">データベースをデタッチするには</span><span class="sxs-lookup"><span data-stu-id="b6d34-150">To detach a database</span></span>  
  
1.  <span data-ttu-id="b6d34-151">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="b6d34-151">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b6d34-152">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d34-152">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b6d34-153">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6d34-153">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b6d34-154">この例では、skipchecks を true に設定して、AdventureWorks2012 データベースをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="b6d34-154">This example detaches the AdventureWorks2012 database with skipchecks set to true.</span></span>  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6d34-155">参照</span><span class="sxs-lookup"><span data-stu-id="b6d34-155">See Also</span></span>  
 <span data-ttu-id="b6d34-156">[データベースのデタッチとアタッチ &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b6d34-156">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 [<span data-ttu-id="b6d34-157">sp_detach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b6d34-157">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
  
