---
title: SQL Server Management Studio によるインメモリ OLTP のサポート | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ee847b5f-6a1a-448e-a746-d61a023881ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 644ba0cfdbe2f0043364c633676bbc536c641efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631905"
---
# <a name="sql-server-management-studio-support-for-in-memory-oltp"></a><span data-ttu-id="936d5-102">SQL Server Management Studio によるインメモリ OLTP のサポート</span><span class="sxs-lookup"><span data-stu-id="936d5-102">SQL Server Management Studio Support for In-Memory OLTP</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="936d5-103">は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インフラストラクチャを管理するための統合環境です。</span><span class="sxs-lookup"><span data-stu-id="936d5-103">is an integrated environment for managing your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="936d5-104">には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを構成、監視、および管理するためのツールが備わっています。</span><span class="sxs-lookup"><span data-stu-id="936d5-104">provides tools to configure, monitor, and administer instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="936d5-105">詳細については、「 [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="936d5-105">For more information, see [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)</span></span>  
  
 <span data-ttu-id="936d5-106">このトピックのタスクでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してメモリ最適化テーブル、メモリ最適化テーブルのインデックス、ネイティブ コンパイル ストアド プロシージャ、およびユーザー定義のメモリ最適化テーブル型を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="936d5-106">The tasks in this topic describe how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage memory-optimized tables; indexes on memory-optimized tables; natively compiled stored procedures; and user-defined, memory-optimized table types.</span></span>  
  
 <span data-ttu-id="936d5-107">プログラムによってメモリ最適化テーブルを作成する方法については、「 [メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャの作成](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="936d5-107">For information on how to programmatically create memory-optimized tables, see [Creating a Memory-Optimized Table and a Natively Compiled Stored Procedure](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-database-with-a-memory-optimized-data-filegroup"></a><span data-ttu-id="936d5-108">メモリ最適化データ ファイル グループが含まれるデータベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="936d5-108">To create a database with a memory-optimized data filegroup</span></span>  
  
1.  <span data-ttu-id="936d5-109">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="936d5-109">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="936d5-110">**[データベース]** を右クリックし、 **[新しいデータベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-110">Right-click **Databases**, and then click **New Database**.</span></span>  
  
3.  <span data-ttu-id="936d5-111">新しいメモリ最適化データ ファイル グループを追加するには、 **[ファイル グループ]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-111">To add a new memory-optimized data filegroup, click the **Filegroups** page.</span></span> <span data-ttu-id="936d5-112">**[メモリ最適化データ]** で **[ファイル グループの追加]** をクリックし、メモリ最適化データ ファイル グループの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="936d5-112">Under **MEMORY OPTIMIZED DATA**, click **Add filegroup** and then enter the name of the memory-optimized data filegroup.</span></span>  <span data-ttu-id="936d5-113">**[FILESTREAM ファイル]** という列は、ファイル グループ内のコンテナー数を表します。</span><span class="sxs-lookup"><span data-stu-id="936d5-113">The column labeled **FILESTREAM Files** represents the number of containers in the filegroup.</span></span> <span data-ttu-id="936d5-114">コンテナーは、 **[全般]** ページで追加します。</span><span class="sxs-lookup"><span data-stu-id="936d5-114">Containers are added on the **General** page.</span></span>  
  
4.  <span data-ttu-id="936d5-115">ファイル グループにファイル (コンテナー) を追加するには、 **[全般]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-115">To add a file (container) to the filegroup, click the **General** page.</span></span> <span data-ttu-id="936d5-116">**[データベース ファイル]** の **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-116">Under **Database files**, click **Add**.</span></span> <span data-ttu-id="936d5-117">**[ファイルの種類]** として **[FILESTREAM データ]** を選択し、コンテナーの論理名を指定して、メモリ最適化ファイル グループを選択します。次に **[自動拡張 / 最大サイズ]** が **[無制限]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="936d5-117">Select **File Type** as **FILESTREAM Data**, specify the logical name of the container, select the memory-optimized filegroup, and make sure that **Autogrowth / Maxsize** is set to **Unlimited**.</span></span>  
  
     <span data-ttu-id="936d5-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して新しいデータベースを作成する方法の詳細については、「 [データベースの作成](../databases/create-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="936d5-118">For more information on how to create a new database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [Create a Database](../databases/create-a-database.md).</span></span>  
  
### <a name="to-create-a-memory-optimized-table"></a><span data-ttu-id="936d5-119">メモリ最適化テーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="936d5-119">To create a memory-optimized table</span></span>  
  
1.  <span data-ttu-id="936d5-120">**オブジェクト エクスプローラー**で、データベースの **[テーブル]** ノードを右クリックし、 **[新規]** 、 **[メモリ最適化テーブル]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-120">In **Object Explorer**, right-click the **Tables** node of your database, click **New**, and then click **Memory Optimized Table**.</span></span>  
  
     <span data-ttu-id="936d5-121">メモリ最適化テーブルを作成するためのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="936d5-121">A template for creating memory-optimized tables is displayed.</span></span>  
  
2.  <span data-ttu-id="936d5-122">テンプレートのパラメーターを置き換えるには、 **[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-122">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="936d5-123">テンプレートの使用方法の詳細については、「 [テンプレート エクスプローラー](../../ssms/template/template-explorer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="936d5-123">For more information on how to use templates, see [Template Explorer](../../ssms/template/template-explorer.md).</span></span>  
  
3.  <span data-ttu-id="936d5-124">**オブジェクト エクスプローラー**では、テーブルはまずディスク ベース テーブル、次にメモリ最適化テーブルの順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="936d5-124">In **Object Explorer**, tables will be ordered first by disk-based tables followed by memory-optimized tables.</span></span> <span data-ttu-id="936d5-125">すべてのテーブルを名前順で確認するには、「 **オブジェクト エクスプローラーの詳細** 」を使用します。</span><span class="sxs-lookup"><span data-stu-id="936d5-125">Use **Object Explorer Details** to see all tables ordered by name.</span></span>  
  
### <a name="to-create-a-natively-compiled-stored-procedure"></a><span data-ttu-id="936d5-126">ネイティブ コンパイル ストアド プロシージャを作成するには</span><span class="sxs-lookup"><span data-stu-id="936d5-126">To create a natively compiled stored procedure</span></span>  
  
1.  <span data-ttu-id="936d5-127">**オブジェクト エクスプローラー**で、データベースの **[ストアド プロシージャ]** ノードを右クリックし、 **[新規]** 、 **[ネイティブ コンパイル ストアド プロシージャ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-127">In **Object Explorer**, right-click the **Stored Procedures** node of your database, click **New**, and then click **Natively Compiled Stored Procedure**.</span></span>  
  
     <span data-ttu-id="936d5-128">ネイティブ コンパイル ストアド プロシージャを作成するためのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="936d5-128">A template for creating natively compiled stored procedures is displayed.</span></span>  
  
2.  <span data-ttu-id="936d5-129">テンプレートのパラメーターを置き換えるには、 **[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-129">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query menu**.</span></span>  
  
     <span data-ttu-id="936d5-130">新しいストアド プロシージャを作成する方法の詳細については、「 [ストアド プロシージャの作成](../stored-procedures/create-a-stored-procedure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="936d5-130">For more information on how to create a new stored procedure, see [Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-user-defined-memory-optimized-table-type"></a><span data-ttu-id="936d5-131">ユーザー定義のメモリ最適化テーブル型を作成するには</span><span class="sxs-lookup"><span data-stu-id="936d5-131">To create a user-defined memory-optimized table type</span></span>  
  
1.  <span data-ttu-id="936d5-132">**[オブジェクト エクスプローラー]** でデータベースの **[種類]** ノードを展開し、 **[ユーザー定義テーブル型]** ノードを右クリックします。次に **[新規作成]** をクリックし、 **[ユーザー定義のメモリ最適化テーブル型]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-132">In **Object Explorer**, expand the **Types** node of your database, right-click the **User-Defined Table Types** node, click **New**, and then click **User-Defined Memory Optimized Table Type**.</span></span>  
  
     <span data-ttu-id="936d5-133">ユーザー定義のメモリ最適化テーブル型を作成するためのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="936d5-133">A template for creating user-defined memory-optimized table type is displayed.</span></span>  
  
2.  <span data-ttu-id="936d5-134">テンプレートのパラメーターを置き換えるには、 **[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-134">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="936d5-135">新しいストアド プロシージャを作成する方法の詳細については、「[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="936d5-135">For more information on how to create a new stored procedure, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
## <a name="memory-monitoring"></a><span data-ttu-id="936d5-136">メモリの監視</span><span class="sxs-lookup"><span data-stu-id="936d5-136">Memory Monitoring</span></span>  
  
#### <a name="view-memory-usage-by-memory-optimized-objects-report"></a><span data-ttu-id="936d5-137">メモリ最適化オブジェクトによるメモリ使用量レポートの表示</span><span class="sxs-lookup"><span data-stu-id="936d5-137">View Memory Usage by Memory-Optimized Objects Report</span></span>  
  
-   <span data-ttu-id="936d5-138">**オブジェクト エクスプローラー**でデータベースを右クリックし、 **[レポート]** 、 **[標準レポート]** 、 **[メモリ最適化オブジェクトによるメモリ使用量]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-138">In **Object Explorer**, right-click your database, click **Reports**, click **Standard Reports**, and then click **Memory Usage By Memory Optimized Objects**.</span></span>  
  
     <span data-ttu-id="936d5-139">このレポートでは、データベース内のメモリ最適化オブジェクトによるメモリ領域の使用に関して詳細なデータが提供されます。</span><span class="sxs-lookup"><span data-stu-id="936d5-139">This report provides detailed data on the utilization of memory space by memory-optimized objects within the database.</span></span>  
  
#### <a name="view-properties-for-allocated-and-used-memory-for-a-table-database"></a><span data-ttu-id="936d5-140">テーブルまたはデータベースに対する割り当てメモリおよび使用メモリのプロパティの表示</span><span class="sxs-lookup"><span data-stu-id="936d5-140">View Properties for Allocated and Used Memory for a Table, Database</span></span>  
  
1.  <span data-ttu-id="936d5-141">インメモリ使用量に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="936d5-141">To get information about in-memory usage:</span></span>  
  
    -   <span data-ttu-id="936d5-142">**[オブジェクト エクスプローラー]** でメモリ最適化テーブルを右クリックし、 **[プロパティ]** 、 **[ストレージ]** ページの順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-142">In **Object Explorer**, right-click on your memory-optimized table, click **Properties**, and then the **Storage** page.</span></span> <span data-ttu-id="936d5-143">**[データ領域]** プロパティの値は、テーブル内のデータによって使用されるメモリを示します。</span><span class="sxs-lookup"><span data-stu-id="936d5-143">The value for the **Data Space** property indicates the memory used by the data in the table.</span></span> <span data-ttu-id="936d5-144">**[インデックス領域]** プロパティの値は、テーブルのインデックスによって使用されるメモリを示します。</span><span class="sxs-lookup"><span data-stu-id="936d5-144">The value for the **Index Space** property indicates the memory used by the indexes on table.</span></span>  
  
    -   <span data-ttu-id="936d5-145">**[オブジェクト エクスプローラー]** で、データベースを右クリックし、 **[プロパティ]** 、 **[全般]** ページの順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-145">In **Object Explorer**, right-click on your database, click **Properties**, and then click the **General** page.</span></span> <span data-ttu-id="936d5-146">**[メモリ最適化オブジェクトに割り当てられたメモリ]** プロパティの値は、データベースのメモリ最適化オブジェクトに割り当てられたメモリを示します。</span><span class="sxs-lookup"><span data-stu-id="936d5-146">The value for the **Memory Allocated To Memory Optimized Objects** property indicates the memory allocated to memory-optimized objects in the database.</span></span> <span data-ttu-id="936d5-147">**[メモリ最適化オブジェクトに使用されるメモリ]** プロパティの値は、データベースのメモリ最適化オブジェクトに使用されるメモリを示します。</span><span class="sxs-lookup"><span data-stu-id="936d5-147">The value for the **Memory Used By Memory Optimized Objects** property indicates the memory used by memory-optimized objects in the database.</span></span>  
  
## <a name="supported-features-in-ssmanstudiofull"></a><span data-ttu-id="936d5-148">でサポートされる機能 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="936d5-148">Supported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="936d5-149">は、メモリ最適化データ ファイル グループ、メモリ最適化テーブル、インデックス、およびネイティブ コンパイル ストアド プロシージャを含むデータベースのデータベース エンジンによってサポートされる操作と機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="936d5-149">supports features and operations that are supported by the database engine on databases with memory-optimized data filegroup, memory-optimized tables, indexes, and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="936d5-150">データベース、テーブル、ストアド プロシージャ、ユーザー定義テーブル型、またはインデックス オブジェクトについては、インメモリ OLTP をサポートするために [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の次の機能が更新または拡張されています。</span><span class="sxs-lookup"><span data-stu-id="936d5-150">For database, table, stored procedure, user-defined table type, or index objects, the following [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] features have been updated or extended to support In-Memory OLTP.</span></span>  
  
-   <span data-ttu-id="936d5-151">オブジェクト エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="936d5-151">Object Explorer</span></span>  
  
    -   <span data-ttu-id="936d5-152">コンテキスト メニュー</span><span class="sxs-lookup"><span data-stu-id="936d5-152">Context menus</span></span>  
  
    -   <span data-ttu-id="936d5-153">フィルターの設定</span><span class="sxs-lookup"><span data-stu-id="936d5-153">Filter settings</span></span>  
  
    -   <span data-ttu-id="936d5-154">スクリプト化</span><span class="sxs-lookup"><span data-stu-id="936d5-154">Script As</span></span>  
  
    -   <span data-ttu-id="936d5-155">タスク</span><span class="sxs-lookup"><span data-stu-id="936d5-155">Tasks</span></span>  
  
    -   <span data-ttu-id="936d5-156">Reports</span><span class="sxs-lookup"><span data-stu-id="936d5-156">Reports</span></span>  
  
    -   <span data-ttu-id="936d5-157">Properties</span><span class="sxs-lookup"><span data-stu-id="936d5-157">Properties</span></span>  
  
    -   <span data-ttu-id="936d5-158">データベース タスク:</span><span class="sxs-lookup"><span data-stu-id="936d5-158">Database tasks:</span></span>  
  
        -   <span data-ttu-id="936d5-159">メモリ最適化テーブルを含むデータベースをアタッチおよびデタッチします。</span><span class="sxs-lookup"><span data-stu-id="936d5-159">Attach and detach a database that contains memory-optimized tables.</span></span>  
  
             <span data-ttu-id="936d5-160">**[データベースのアタッチ]** のユーザー インターフェイスには、メモリ最適化データ ファイル グループは表示されません。</span><span class="sxs-lookup"><span data-stu-id="936d5-160">The **Attach Databases** user interface does not display the memory-optimized data filegroup.</span></span> <span data-ttu-id="936d5-161">ただし、データベースのアタッチを続行することはでき、データベースは正しくアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="936d5-161">However, you can proceed with attaching the database and the database will be attached correctly.</span></span>  
  
            > [!NOTE]  
            >  <span data-ttu-id="936d5-162">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してメモリ最適化データ ファイル グループ コンテナーを持つデータベースをアタッチする場合、データベースのメモリ最適化データ ファイル グループ コンテナーが別のコンピューター上に作成されているときには、両方のコンピューターでメモリ最適化データ ファイル グループ コンテナーの場所が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="936d5-162">If you want to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to attach a database that has a memory-optimized data filegroup container, and if the database's memory-optimized data filegroup container was created on another computer, the location of the memory-optimized data filegroup container must be the same on both computers.</span></span> <span data-ttu-id="936d5-163">新しいコンピューターでデータベースのメモリ最適化データ ファイル グループ コンテナーを別の場所に配置する場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してデータベースをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="936d5-163">If you want the location of the database's memory-optimized data filegroup container to be different on the new computer, you can, use [!INCLUDE[tsql](../../includes/tsql-md.md)] to attach the database.</span></span> <span data-ttu-id="936d5-164">次の例では、新しいコンピューターのメモリ最適化データ ファイル グループ コンテナーの場所は C:\Folder2 です。</span><span class="sxs-lookup"><span data-stu-id="936d5-164">In the following example, the location of the memory-optimized data filegroup container on the new computer is C:\Folder2.</span></span> <span data-ttu-id="936d5-165">ただし、最初のコンピューターでは、メモリ最適化データ ファイル グループ コンテナーは C:\Folder1 に作成されています。</span><span class="sxs-lookup"><span data-stu-id="936d5-165">But when the memory-optimized data filegroup container was created, on the first computer, the location was C:\Folder1.</span></span>  
            >   
            >  `CREATE DATABASE[imoltp] ON`  
            >   
            >  `(NAME =N'imoltp',FILENAME=N'C:\Folder2\imoltp.mdf'),`  
            >   
            >  `(NAME =N'imoltp_mod1',FILENAME=N'C:\Folder2\imoltp_mod1'),`  
            >   
            >  `(NAME =N'imoltp_log',FILENAME=N'C:\Folder2\imoltp_log.ldf')`  
            >   
            >  `FOR ATTACH`  
            >   
            >  `GO`  
  
        -   <span data-ttu-id="936d5-166">スクリプトの生成。</span><span class="sxs-lookup"><span data-stu-id="936d5-166">Generate scripts.</span></span>  
  
             <span data-ttu-id="936d5-167">**スクリプトの生成とパブリッシュ ウィザード**で、 **[オブジェクトの有無を確認する]** スクリプト作成オプションの既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="936d5-167">In the **Generate and Publish Scripts Wizard**, the default value for **Check for object existence** scripting option is FALSE.</span></span> <span data-ttu-id="936d5-168">ウィザードの **[スクリプト作成オプションの設定]** 画面で、 **[オブジェクトの有無を確認する]** スクリプト作成オプションの値を TRUE に設定すると、生成されるスクリプトに "CREATE PROCEDURE <プロシージャ名> AS" および "ALTER PROCEDURE <プロシージャ名> <プロシージャ定義>" が含められます。</span><span class="sxs-lookup"><span data-stu-id="936d5-168">If the value of **Check for object existence** scripting option is set to TRUE in the **Set Scripting Options** screen of the wizard, the script generated would contain "CREATE PROCEDURE <procedure_name> AS" and "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span> <span data-ttu-id="936d5-169">生成されたスクリプトを実行すると、ネイティブ コンパイル ストアド プロシージャが ALTER PROCEDURE をサポートしていないことが原因で、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="936d5-169">When executed, the generated script will return an error as ALTER PROCEDURE is not supported on natively compiled stored procedures.</span></span>  
  
             <span data-ttu-id="936d5-170">ネイティブ コンパイル ストアド プロシージャごとに生成されるスクリプトを変更するには</span><span class="sxs-lookup"><span data-stu-id="936d5-170">To change the generated script for each natively compiled stored procedure:</span></span>  
  
            1.  <span data-ttu-id="936d5-171">In "CREATE PROCEDURE <プロシージャ名> AS" で、"AS" を "<プロシージャ定義>" に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="936d5-171">In "CREATE PROCEDURE <procedure_name> AS", replace "AS" with "<procedure_definition>".</span></span>  
  
            2.  <span data-ttu-id="936d5-172">"ALTER PROCEDURE <プロシージャ名> <プロシージャ定義>" を削除します。</span><span class="sxs-lookup"><span data-stu-id="936d5-172">Delete "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span>  
  
        -   <span data-ttu-id="936d5-173">データベースのコピー。</span><span class="sxs-lookup"><span data-stu-id="936d5-173">Copy databases.</span></span> <span data-ttu-id="936d5-174">メモリ最適化オブジェクトを含むデータベースの場合、コピー先サーバー上にデータベースを作成する動作とデータを転送する動作が 1 回のトランザクション内で実行されることはありません。</span><span class="sxs-lookup"><span data-stu-id="936d5-174">For databases with memory-optimized objects, the creation of the database on the destination server and transfer of data will not be executed within a transaction.</span></span>  
  
        -   <span data-ttu-id="936d5-175">データのインポートとエクスポート。</span><span class="sxs-lookup"><span data-stu-id="936d5-175">Import and export data.</span></span> <span data-ttu-id="936d5-176">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードの [1 つ以上のテーブルまたはビューからデータをコピーする]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="936d5-176">Use the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export WizardCopy data from one or more tables or views** option.</span></span> <span data-ttu-id="936d5-177">対象のテーブルが転送先データベースに存在しないメモリ最適化テーブルの場合には、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="936d5-177">If the destination table is a memory-optimized table that does not exist in the destination database:</span></span>  
  
            1.  <span data-ttu-id="936d5-178">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザード**の **[テーブルのコピーまたはクエリの指定]** 画面で、 **[1 つ以上のテーブルまたはビューのデータをコピーする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="936d5-178">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard**, in the **Specify Table Copy or Query** screen, select **Copy data from one or more tables or views**.</span></span> <span data-ttu-id="936d5-179">続けて、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-179">Then click **Next**.</span></span>  
  
            2.  <span data-ttu-id="936d5-180">**[マッピングの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-180">Click **Edit Mappings**.</span></span> <span data-ttu-id="936d5-181">**[変換先テーブルを作成する]** 、 **[SQL の編集]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="936d5-181">Then select **Create destination table** and click **Edit SQL**.</span></span> <span data-ttu-id="936d5-182">CREATE TABLE 構文を入力して、転送先データベースにメモリ最適化テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="936d5-182">Enter the CREATE TABLE syntax for creating a memory-optimized table on the destination database.</span></span> <span data-ttu-id="936d5-183">**[OK]** をクリックし、ウィザードの残りの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="936d5-183">Click **OK** and complete the remaining steps in the wizard.</span></span>  
  
        -   <span data-ttu-id="936d5-184">メンテナンス プラン。</span><span class="sxs-lookup"><span data-stu-id="936d5-184">Maintenance plans.</span></span> <span data-ttu-id="936d5-185">インデックスを再構成し、再構築するメンテナンス タスクは、メモリ最適化テーブルとそのインデックスではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="936d5-185">The maintenance tasks reorganize index and rebuild index are not supported on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="936d5-186">このため、インデックスを再構築および再構成するメンテナンス プランを実行しても、選択したデータベース内のメモリ最適化テーブルおよびそのインデックスは省略されます。</span><span class="sxs-lookup"><span data-stu-id="936d5-186">Therefore, when a maintenance plan for rebuild index and reorganize index are executed, the memory-optimized tables and their indexes in the selected databases are omitted.</span></span>  
  
             <span data-ttu-id="936d5-187">メンテナンス タスクの統計の更新は、メモリ最適化テーブルおよびそのインデックスのサンプル スキャンではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="936d5-187">The maintenance task update statistics are not supported with a sample scan on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="936d5-188">したがって、統計の更新のメンテナンス プランを実行すると、メモリ最適化テーブルおよびそのインデックスの統計は、常に `WITH FULLSCAN, NORECOMPUTE` に更新されます。</span><span class="sxs-lookup"><span data-stu-id="936d5-188">Therefore, when a maintenance plan for update statistics is executed, the statistics for memory-optimized tables and their indexes are always updated to `WITH FULLSCAN, NORECOMPUTE`.</span></span>  
  
-   <span data-ttu-id="936d5-189">[オブジェクト エクスプローラーの詳細] ペイン</span><span class="sxs-lookup"><span data-stu-id="936d5-189">Object Explorer details pane</span></span>  
  
-   <span data-ttu-id="936d5-190">テンプレート エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="936d5-190">Template Explorer</span></span>  
  
## <a name="unsupported-features-in-ssmanstudiofull"></a><span data-ttu-id="936d5-191">でサポートされない機能 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="936d5-191">Unsupported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 <span data-ttu-id="936d5-192">インメモリ OLTP オブジェクトに対して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、データベース エンジンでもサポートされない機能と操作はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="936d5-192">For In-Memory OLTP objects, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] does not support features and operations that are also not supported by the database engine.</span></span>  
  
 <span data-ttu-id="936d5-193">サポートされていない機能の詳細につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「[サポートされる SQL Server 機能](unsupported-sql-server-features-for-in-memory-oltp.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="936d5-193">For more information on unsupported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features, see [Supported SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="936d5-194">参照</span><span class="sxs-lookup"><span data-stu-id="936d5-194">See Also</span></span>  
 [<span data-ttu-id="936d5-195">SQL Server によるインメモリ OLTP のサポート</span><span class="sxs-lookup"><span data-stu-id="936d5-195">SQL Server Support for In-Memory OLTP</span></span>](sql-server-support-for-in-memory-oltp.md)  
  
  
