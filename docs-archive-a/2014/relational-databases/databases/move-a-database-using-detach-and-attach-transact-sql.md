---
title: デタッチとアタッチを使用してデータベースを移動する方法 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database attaching [SQL Server]
- moving databases [SQL Server]
- database detaching [SQL Server]
- relocating databases [SQL Server]
- detaching databases [SQL Server]
- attaching databases [SQL Server]
ms.assetid: 6732a431-cdef-4f1e-9262-4ac3b77c275e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 768a70dfe94af6f8d65f7c76fa08d3dff650fe7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645627"
---
# <a name="move-a-database-using-detach-and-attach-transact-sql"></a><span data-ttu-id="f0134-102">デタッチとアタッチを使用してデータベースを移動する方法 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f0134-102">Move a Database Using Detach and Attach (Transact-SQL)</span></span>
  <span data-ttu-id="f0134-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でデタッチしたデータベースを別の場所に移動し、同じまたは異なるサーバー インスタンスに再アタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f0134-103">This topic describes how to move a detached database to another location and re-attach it to the same or a different server instance in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="f0134-104">ただし、データベースを移動するときは、デタッチとアタッチではなく、ALTER DATABASE による計画的再配置手順を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0134-104">However, we recommend that you move databases by using the ALTER DATABASE planned relocation procedure, instead of using detach and attach.</span></span> <span data-ttu-id="f0134-105">詳細については、「 [ユーザー データベースの移動](move-user-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0134-105">For more information, see [Move User Databases](move-user-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f0134-106">不明なソースや信頼されていないソースからデータベースをアタッチまたは復元しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0134-106">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="f0134-107">こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f0134-107">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="f0134-108">不明または信頼できないソースのデータベースを使用する前に、運用サーバー以外のサーバーでそのデータベースに対し [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。</span><span class="sxs-lookup"><span data-stu-id="f0134-108">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="f0134-109">手順</span><span class="sxs-lookup"><span data-stu-id="f0134-109">Procedure</span></span>  
  
#### <a name="to-move-a-database-by-using-detach-and-attach"></a><span data-ttu-id="f0134-110">デタッチとアタッチを使用してデータベースを移動するには</span><span class="sxs-lookup"><span data-stu-id="f0134-110">To move a database by using detach and attach</span></span>  
  
1.  <span data-ttu-id="f0134-111">データベースをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="f0134-111">Detach the database.</span></span> <span data-ttu-id="f0134-112">詳細については、「 [データベースのデタッチ](detach-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0134-112">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
2.  <span data-ttu-id="f0134-113">Windows エクスプローラーまたは Windows コマンド プロンプト ウィンドウで、デタッチされたデータベース ファイルとログ ファイルを新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="f0134-113">In a Windows Explorer or Windows Command Prompt window, move the detached database file or files and log file or files to the new location.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0134-114">単一ファイルのデータベースを移動する場合は、電子メールを使用できます。ただし、ファイル サイズが電子メールで対応できる大きさである場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="f0134-114">To move a single-file database, you can use email if the file size is small enough for email to accommodate.</span></span>  
  
     <span data-ttu-id="f0134-115">新しいログ ファイルを作成する場合でも、ログ ファイルを移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0134-115">You should move the log files even if you intend to create new log files.</span></span> <span data-ttu-id="f0134-116">場合によっては、データベースの再アタッチに既存のログ ファイルが必要になります。</span><span class="sxs-lookup"><span data-stu-id="f0134-116">In some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="f0134-117">したがって、デタッチしたログ ファイルを使わずにデータベースを正常にアタッチできるまで、デタッチしたログ ファイルは必ずすべて保管しておいてください。</span><span class="sxs-lookup"><span data-stu-id="f0134-117">Therefore, always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0134-118">ログ ファイルを指定せずにデータベースのインポートを試みると、アタッチ操作は元の場所でログ ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="f0134-118">If you try to attach the database without specifying the log file, the attach operation will look for the log file in its original location.</span></span> <span data-ttu-id="f0134-119">ログのコピーが依然として元の場所にある場合は、そのコピーがアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="f0134-119">If a copy of the log still exists in the original location, that copy is attached.</span></span> <span data-ttu-id="f0134-120">元のログ ファイルが使用されないようにするには、新しいログ ファイルのパスを指定するか、ログ ファイルの元のコピーを (新しい場所にコピーした後で) 削除します。</span><span class="sxs-lookup"><span data-stu-id="f0134-120">To avoid using the original log file, either specify the path of the new log file or remove the original copy of the log file (after copying it to the new location).</span></span>  
  
3.  <span data-ttu-id="f0134-121">コピーしたファイルをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="f0134-121">Attach the copied files.</span></span> <span data-ttu-id="f0134-122">詳細については、「 [Attach a Database](attach-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0134-122">For more information, see [Attach a Database](attach-a-database.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0134-123">例</span><span class="sxs-lookup"><span data-stu-id="f0134-123">Example</span></span>  
 <span data-ttu-id="f0134-124">次の例では、ステートメントのコピーを、がアタッチされている [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] サーバーインスタンスに接続されているクエリエディターウィンドウで実行します。</span><span class="sxs-lookup"><span data-stu-id="f0134-124">The following example creates a copy of the [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] statements are executed in a Query Editor window that is connected to the server instance to which is attached.</span></span>  
  
1.  <span data-ttu-id="f0134-125">ステートメントをデタッチし [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f0134-125">Detach the [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'AdventureWorks2012';  
    GO  
    ```  
  
2.  <span data-ttu-id="f0134-126">任意の方法で、データベース ファイル (AdventureWorks208R2_Data.mdf と AdventureWorks208R2_log) を C:\MySQLServer\AdventureWorks208R2_Data.mdf と C:\MySQLServer\AdventureWorks208R2_Log.ldf にそれぞれコピーします。</span><span class="sxs-lookup"><span data-stu-id="f0134-126">Using the method of your choice, copy the database files (AdventureWorks208R2_Data.mdf and AdventureWorks208R2_log) to: C:\MySQLServer\AdventureWorks208R2_Data.mdf and C:\MySQLServer\AdventureWorks208R2_Log.ldf, respectively.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f0134-127">実稼動データベースの場合は、データベースとトランザクション ログを別のディスクに配置します。</span><span class="sxs-lookup"><span data-stu-id="f0134-127">For a production database, place the database and transaction log on separate disks.</span></span>  
  
     <span data-ttu-id="f0134-128">ファイルをネットワーク経由でリモート コンピューターのディスクにコピーするには、そのリモート コンピューターの UNC (Universal Naming Convention) 名を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0134-128">To copy files over the network to a disk on a remote computer, use the universal naming convention (UNC) name of the remote location.</span></span> <span data-ttu-id="f0134-129">UNC 名の形式は、 **\\\\** _Servername_ **\\** _Sharename_ **\\** _Path_ **\\** _Filename_です。</span><span class="sxs-lookup"><span data-stu-id="f0134-129">A UNC name takes the form **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="f0134-130">ローカル ハード ディスクにファイルを書き込む場合と同様、リモート ディスクでのファイルの読み取りや書き込みに必要な適切な権限が、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスで使用するユーザー アカウントに許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0134-130">As with writing files to the local hard disk, the appropriate permissions that are required to read or write to a file on the remote disk must be granted to the user account used by the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="f0134-131">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して、移動したデータベースとログをアタッチします (ログのアタッチは省略できます)。</span><span class="sxs-lookup"><span data-stu-id="f0134-131">Attach the moved database and, optionally, its log by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Data.mdf'),  
        (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Log.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     <span data-ttu-id="f0134-132">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、新しくアタッチされたデータベースはオブジェクト エクスプローラーにすぐに表示されません。</span><span class="sxs-lookup"><span data-stu-id="f0134-132">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], a newly attached database is not immediately visible in Object Explorer.</span></span> <span data-ttu-id="f0134-133">このデータベースを表示するには、オブジェクト エクスプローラーで、 **[表示]** をクリックし、 **[最新の情報に更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0134-133">To view the database, in Object Explorer, click **View,** and then **Refresh**.</span></span> <span data-ttu-id="f0134-134">オブジェクト エクスプローラーの **[データベース]** ノードを展開すると、データベースの一覧に新しくアタッチされたデータベースが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="f0134-134">When the **Databases** node is expanded in Object Explorer, the newly attached database now appears in the list of databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0134-135">参照</span><span class="sxs-lookup"><span data-stu-id="f0134-135">See Also</span></span>  
 [<span data-ttu-id="f0134-136">データベースのデタッチとアタッチ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f0134-136">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
