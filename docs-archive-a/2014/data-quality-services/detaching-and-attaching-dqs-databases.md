---
title: DQS データベースのデタッチとアタッチ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 830e33bc-dd15-4f8e-a4ac-d8634b78fe45
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3bcac9d1f53b10cf6356b878ce4006f66c198d99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633320"
---
# <a name="detaching-and-attaching-dqs-databases"></a><span data-ttu-id="eb59b-102">DQS データベースのデタッチとアタッチ</span><span class="sxs-lookup"><span data-stu-id="eb59b-102">Detaching and Attaching DQS Databases</span></span>
  <span data-ttu-id="eb59b-103">ここでは、DQS データベースをデタッチおよびアタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-103">This topic describes how to detach and attach the DQS databases.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eb59b-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="eb59b-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limitations"></a> <span data-ttu-id="eb59b-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="eb59b-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="eb59b-106">制限事項と制約事項の一覧については、「 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md)のデータベースをデタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-106">For a list of limitations and restrictions, see [Database Detach and Attach &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="eb59b-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="eb59b-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="eb59b-108">DQS で実行中のアクティビティまたはプロセスがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-108">Ensure that there are no running activities or processes in DQS.</span></span> <span data-ttu-id="eb59b-109">これは **[アクティビティ監視]** 画面を使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="eb59b-109">This can be verified using the **Activity Monitoring** screen.</span></span> <span data-ttu-id="eb59b-110">この画面の操作の詳細については、「 [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb59b-110">For detailed information about working in this screen, see [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).</span></span>  
  
-   <span data-ttu-id="eb59b-111">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]にログオンしているユーザーがいないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-111">Ensure that there are no users logged on the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eb59b-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="eb59b-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eb59b-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="eb59b-113">Permissions</span></span>  
  
-   <span data-ttu-id="eb59b-114">DQS データベースをデタッチするには、Windows ユーザー アカウントが、SQL Server インスタンスの db_owner 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="eb59b-114">Your Windows user account must be a member of the db_owner fixed server role in the SQL Server instance to detach DQS databases.</span></span>  
  
-   <span data-ttu-id="eb59b-115">データベースをアタッチするには、Windows ユーザー アカウントに、CREATE DATABASE、CREATE ANY DATABASE、または ALTER ANY DATABASE の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="eb59b-115">Your Windows user account must have CREATE DATABASE, CREATE ANY DATABASE, or ALTER ANY DATABASE permission to attach a database.</span></span>  
  
-   <span data-ttu-id="eb59b-116">DQS の実行中のアクティビティを終了させたり実行中のプロセスを停止させたりするには、DQS_MAIN データベースの dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="eb59b-116">You must have the dqs_administrator role on the DQS_MAIN database to terminate any running activities or stop any running processes in DQS.</span></span>  
  
##  <a name="detach-dqs-databases"></a><a name="Detach"></a><span data-ttu-id="eb59b-117">DQS データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="eb59b-117">Detach DQS Databases</span></span>  
 <span data-ttu-id="eb59b-118">SQL Server Management Studio を使用して DQS データベースをデタッチすると、デタッチされたファイルはコンピューターに残り、同じ SQL Server インスタンスに再アタッチすることも、別のサーバーに移動して、そこにアタッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="eb59b-118">When you detach a DQS database using SQL Server Management Studio, the detached files remain on your computer, and can be reattached to the same SQL Server instance or can be can be moved to another server and attached there.</span></span> <span data-ttu-id="eb59b-119">DQS データベースファイルは通常、Data Quality Services コンピューターの C:\Program are SQL Server\MSSQL12. にあります。*<Instance_Name>* \mssql\data</span><span class="sxs-lookup"><span data-stu-id="eb59b-119">The DQS database files are typically available at the following location on your Data Quality Services computer: C:\Program Files\Microsoft SQL Server\MSSQL12.*<Instance_Name>* \MSSQL\DATA.</span></span>  
  
1.  <span data-ttu-id="eb59b-120">Microsoft SQL Server Management Studio を起動し、適切な SQL Server インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-120">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="eb59b-121">オブジェクト エクスプローラーで、 **[データベース]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-121">In Object Explorer, expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="eb59b-122">**DQS_MAIN** データベースを右クリックして **[タスク]** をポイントし、 **[デタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-122">Right-click the **DQS_MAIN** database, point to **Tasks**, and then click **Detach**.</span></span> <span data-ttu-id="eb59b-123">**[データベースのデタッチ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb59b-123">The **Detach Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="eb59b-124">**[削除]** 列の下にあるチェック ボックスをオンにし、 **[OK]** をクリックして DQS_MAIN データベースをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-124">Select the check box under the **Drop** column, and click **OK** to detach the DQS_MAIN database.</span></span>  
  
5.  <span data-ttu-id="eb59b-125">DQS_PROJECTS データベースと DQS_STAGING_DATA データベースで手順 3. と 4. を繰り返し、それらをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-125">Repeat steps 3 and 4 with the DQS_PROJECTS and DQS_STAGING_DATA databases to detach them.</span></span>  
  
 <span data-ttu-id="eb59b-126">Transact-SQL ステートメントで sp_detach_db ストアド プロシージャを使用して、DQS データベースをデタッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="eb59b-126">You can also detach DQS databases using the Transact-SQL statements by using the sp_detach_db stored procedure.</span></span> <span data-ttu-id="eb59b-127">Transact-SQL ステートメントを使用したデータベースのデタッチに関する詳細については、「 [Using Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) 」の「 [Detach a Database](../relational-databases/databases/detach-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb59b-127">For more information about detaching databases using Transact-SQL statements, see [Using Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) in [Detach a Database](../relational-databases/databases/detach-a-database.md).</span></span>  
  
##  <a name="attach-dqs-databases"></a><a name="Attach"></a><span data-ttu-id="eb59b-128">DQS データベースをアタッチする</span><span class="sxs-lookup"><span data-stu-id="eb59b-128">Attach DQS Databases</span></span>  
 <span data-ttu-id="eb59b-129">次の手順を使用して、DQS データベースを (デタッチした場所から) 同じ SQL Server インスタンスまたは [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] がインストールされている別の SQL Server インスタンスにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-129">Use the following instructions to attach a DQS database to the same SQL Server instance (from where you detached) or a different SQL Server instance where [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
1.  <span data-ttu-id="eb59b-130">Microsoft SQL Server Management Studio を起動し、適切な SQL Server インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-130">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="eb59b-131">オブジェクト エクスプローラーで、 **[データベース]** を右クリックし、 **[アタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-131">In Object Explorer, right-click **Databases**, and then click **Attach**.</span></span> <span data-ttu-id="eb59b-132">**[データベースのデタッチ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb59b-132">The **Attach Databases** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="eb59b-133">アタッチするデータベースを指定するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-133">To specify the database to be attached, click **Add**.</span></span> <span data-ttu-id="eb59b-134">**[データベース ファイルの検索]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb59b-134">The **Locate Database Files** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="eb59b-135">データベースが存在するディスク ドライブを選択し、ディレクトリ ツリーを展開してデータベースの .mdf ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-135">Select the disk drive where the database resides and expand the directory tree to find and select the .mdf file of the database.</span></span> <span data-ttu-id="eb59b-136">たとえば、DQS_MAIN データベースの場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="eb59b-136">For example, for the DQS_MAIN database:</span></span>  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\DQS_MAIN.mdf  
    ```  
  
5.  <span data-ttu-id="eb59b-137">**[データベースの詳細]** (下部) ペインには、アタッチするファイルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb59b-137">The **database details** (lower) pane displays the names of the files to be attached.</span></span> <span data-ttu-id="eb59b-138">ファイルのパス名を確認または変更するには、**参照**ボタン ( [...] ) をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="eb59b-138">To verify or change the pathname of a file, click the **Browse** button (...).</span></span>  
  
6.  <span data-ttu-id="eb59b-139">DQS_MAIN データベースをアタッチするには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-139">Click **OK** to attach the DQS_MAIN database.</span></span>  
  
7.  <span data-ttu-id="eb59b-140">DQS_PROJECTS データベースと DQS_STAGING_DATA データベースで手順 2. ～ 6. を繰り返し、それらをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-140">Repeat steps 2-6 for the DQS_PROJECTS and DQS_STAGING_DATA databases to attach them.</span></span>  
  
8.  <span data-ttu-id="eb59b-141">また、DQS_MAIN データベースを復元した後の次の手順で Transact-SQL ステートメントを実行する必要もあります。これを実行しない場合、Data Quality Client アプリケーションを使用して Data Quality Server に接続しようとするとエラー メッセージが表示され、接続できません。</span><span class="sxs-lookup"><span data-stu-id="eb59b-141">You must also run the Transact-SQL statements in the next step after restoring the DQS_MAIN database otherwise an error message is displayed when you try to connect to Data Quality Server by using the Data Quality Client application, and you cannot connect.</span></span> <span data-ttu-id="eb59b-142">ただし、DQS_PROJECTS データベースまたは DQS_STAGING_DATA データベースをアタッチし、DQS_MAIN をアタッチしていない場合、手順 9. と 10. を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="eb59b-142">However, you do not need to perform steps 9 and 10 if you have just attached the DQS_PROJECTS or DQS_STAGING_DATA database, and not DQS_MAIN.</span></span>  
  
     <span data-ttu-id="eb59b-143">Transact-SQL ステートメントを実行するには、オブジェクト エクスプローラーで、サーバーを右クリックし、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-143">To run the Transact-SQL statements, in Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
9. <span data-ttu-id="eb59b-144">クエリ エディター ウィンドウで、SQL ステートメントをコピーします。</span><span class="sxs-lookup"><span data-stu-id="eb59b-144">In the Query Editor window, copy the following SQL statements:</span></span>  
  
    ```sql  
    ALTER DATABASE [DQS_MAIN] SET TRUSTWORTHY ON;  
    EXEC sp_configure 'clr enabled', 1;  
    RECONFIGURE WITH OVERRIDE  
    ALTER DATABASE [DQS_MAIN] SET ENABLE_BROKER  
    ALTER AUTHORIZATION ON DATABASE::[DQS_MAIN] TO [##MS_dqs_db_owner_login##]  
    ALTER AUTHORIZATION ON DATABASE::[DQS_PROJECTS] TO [##MS_dqs_db_owner_login##]  
    ```  
  
10. <span data-ttu-id="eb59b-145">F5 キーを押してステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-145">Press F5 to execute the statements.</span></span> <span data-ttu-id="eb59b-146">[結果] ペインを確認してステートメントが正常に実行されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-146">Check the Results pane to verify that the statements have executed successfully.</span></span> <span data-ttu-id="eb59b-147">" `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb59b-147">You will see the following message: `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`</span></span>  
  
11. <span data-ttu-id="eb59b-148">Data Quality Client を使用して Data Quality Server に接続し、正常に接続できるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="eb59b-148">Connect to the Data Quality Server using the Data Quality Client to verify if you can connect successfully.</span></span>  
  
 <span data-ttu-id="eb59b-149">また、Transact-SQL ステートメントを使用して DQS データベースをアタッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="eb59b-149">You can also attach DQS databases using the Transact-SQL statements.</span></span> <span data-ttu-id="eb59b-150">Transact-SQL ステートメントを使用したデータベースのインポートに関する詳細については、「 [Using Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) 」の「 [Attach a Database](../relational-databases/databases/attach-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb59b-150">For more information about attaching databases using Transact-SQL statements, see [Using Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) in [Attach a Database](../relational-databases/databases/attach-a-database.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb59b-151">参照</span><span class="sxs-lookup"><span data-stu-id="eb59b-151">See Also</span></span>  
 [<span data-ttu-id="eb59b-152">Manage DQS Databases</span><span class="sxs-lookup"><span data-stu-id="eb59b-152">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
