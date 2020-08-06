---
title: テーブルとストアド プロシージャのネイティブ コンパイル | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5880fbd9-a23e-464a-8b44-09750eeb2dad
author: rothja
ms.author: jroth
ms.openlocfilehash: 32c5b04610d894e06278fbeecdaf3bbebe850d60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642082"
---
# <a name="native-compilation-of-tables-and-stored-procedures"></a><span data-ttu-id="ddd41-102">テーブルとストアド プロシージャのネイティブ コンパイル</span><span class="sxs-lookup"><span data-stu-id="ddd41-102">Native Compilation of Tables and Stored Procedures</span></span>
  <span data-ttu-id="ddd41-103">インメモリ OLTP により、ネイティブ コンパイルという概念が導入されています。</span><span class="sxs-lookup"><span data-stu-id="ddd41-103">In-Memory OLTP introduces the concept of native compilation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ddd41-104">はメモリ最適化テーブルにアクセスするストアド プロシージャをネイティブにコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-104">can natively compile stored procedures that access memory-optimized tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ddd41-105">はメモリ最適化テーブルをネイティブにコンパイルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-105">is also able to natively compile memory-optimized tables.</span></span> <span data-ttu-id="ddd41-106">ネイティブ コンパイルは、(従来の) 解釈された [!INCLUDE[tsql](../../includes/tsql-md.md)]よりも高速なデータ アクセスと効率的なクエリ実行を可能にします。</span><span class="sxs-lookup"><span data-stu-id="ddd41-106">Native compilation allows faster data access and more efficient query execution than interpreted (traditional) [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ddd41-107">テーブルとストアド プロシージャのネイティブ コンパイルを実行すると DLL が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-107">Native compilation of tables and stored procedures produce DLLs.</span></span>  
  
 <span data-ttu-id="ddd41-108">メモリ最適化テーブル型のネイティブ コンパイルもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ddd41-108">Native compilation of memory optimized table types is also supported.</span></span> <span data-ttu-id="ddd41-109">詳しくは、「 [Memory-Optimized Table Variables](../../database-engine/memory-optimized-table-variables.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ddd41-109">For more information, see [Memory-Optimized Table Variables](../../database-engine/memory-optimized-table-variables.md).</span></span>  
  
 <span data-ttu-id="ddd41-110">ネイティブ コンパイルとは、プログラミングの構造をネイティブ コードに変換する処理であり、追加のコンパイルまたは解釈を必要としないプロセッサ命令で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-110">Native compilation refers to the process of converting programming constructs to native code, consisting of processor instructions without the need for further compilation or interpretation.</span></span>  
  
 <span data-ttu-id="ddd41-111">インメモリ OLTP は、作成されたときにメモリ最適化テーブルを、そしてネイティブ DLL に読み込まれたときにネイティブ コンパイル ストアド プロシージャをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ddd41-111">In-Memory OLTP compiles memory-optimized tables when they are created, and natively compiled stored procedures when they are loaded to native DLLs.</span></span> <span data-ttu-id="ddd41-112">また、DLL は、データベースまたはサーバーが再起動した後に再コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-112">In addition, the DLLs are recompiled after a database or server restart.</span></span> <span data-ttu-id="ddd41-113">DLL を再作成するために必要な情報がデータベース メタデータに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-113">The information necessary to recreate the DLLs is stored in the database metadata.</span></span> <span data-ttu-id="ddd41-114">DLL は、データベースに関連付けられていますが、データベースの一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="ddd41-114">The DLLs are not part of the database, though they are associated with the database.</span></span> <span data-ttu-id="ddd41-115">たとえば、DLL は、データベース バックアップに含まれていません。</span><span class="sxs-lookup"><span data-stu-id="ddd41-115">For example, the DLLs are not included in database backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddd41-116">メモリ最適化テーブルは、サーバーの再起動中に再コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-116">Memory-optimized tables are recompiled during a server restart.</span></span> <span data-ttu-id="ddd41-117">データベースの復元を迅速に行うために、ネイティブ コンパイル ストアド プロシージャは、サーバーの再起動中に再コンパイルされず、最初の実行時にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-117">To speed up database recovery, natively compiled stored procedures are not recompiled during a server restart, they are compiled at the time of first execution.</span></span> <span data-ttu-id="ddd41-118">このようにコンパイルが延期されるため、ネイティブ コンパイル ストアド プロシージャは、最初の実行後に [sys.dm_os_loaded_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql) を呼び出した場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-118">As a result of this deferred compilation, natively compiled stored procedures only appear when calling [sys.dm_os_loaded_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql) after first execution.</span></span>  
  
## <a name="maintenance-of-in-memory-oltp-dlls"></a><span data-ttu-id="ddd41-119">インメモリ OLTP DLL のメンテナンス</span><span class="sxs-lookup"><span data-stu-id="ddd41-119">Maintenance of In-Memory OLTP DLLs</span></span>  
 <span data-ttu-id="ddd41-120">次のクエリは、サーバーのメモリに現在読み込まれているすべてのテーブルとストアド プロシージャ DLL を示します。</span><span class="sxs-lookup"><span data-stu-id="ddd41-120">The following query shows all table and stored procedure DLLs currently loaded in memory on the server:</span></span>  
  
```sql  
SELECT name, description FROM sys.dm_os_loaded_modules  
where description = 'XTP Native DLL'  
```  
  
 <span data-ttu-id="ddd41-121">ネイティブ コンパイルによって生成されたファイルをデータベース管理者が維持する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ddd41-121">Database administrators do not need to maintain files that are generated by a native compilation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ddd41-122">によって、不要になった生成ファイルが自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-122">automatically removes generated files that are no longer needed.</span></span> <span data-ttu-id="ddd41-123">たとえばテーブルやストアド プロシージャが削除されたとき、またはデータベースが削除されたときに、生成ファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-123">For example, generated files will be deleted when a table and stored procedure is deleted, or if a database is dropped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddd41-124">コンパイルが失敗するか、中断した場合、生成されたファイルの一部は削除されません。</span><span class="sxs-lookup"><span data-stu-id="ddd41-124">If compilation fails or is interrupted, some generated files are not removed.</span></span> <span data-ttu-id="ddd41-125">これらのファイルはサポート性のために意図的に残され、データベースが削除されるときに削除されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-125">These files are intentionally left behind for supportability and are removed when the database is dropped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddd41-126">データベースを起動している間に、SQL Server によってデータベースの復旧に必要なすべてのテーブルの Dll がコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-126">During database startup, SQL Server compiles DLLs for all tables needed for database recovery.</span></span> <span data-ttu-id="ddd41-127">データベースを再起動する直前にテーブルが削除された場合、チェックポイント ファイルかトランザクション ログにテーブルの残存物が存在するため、データベースの起動中にテーブルの DLL が再コンパイルされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ddd41-127">If a table was dropped just prior to a database restart there can still be remnants of the table in the checkpoint files or the transaction log so the DLL for the table might be recompiled during database startup.</span></span> <span data-ttu-id="ddd41-128">再起動後に DLL がアンロードされ、通常のクリーンアップ プロセスによってファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-128">After restart the DLL will be unloaded and the files will be removed by the normal cleanup process.</span></span>  
  
## <a name="native-compilation-of-tables"></a><span data-ttu-id="ddd41-129">テーブルのネイティブ コンパイル</span><span class="sxs-lookup"><span data-stu-id="ddd41-129">Native Compilation of Tables</span></span>  
 <span data-ttu-id="ddd41-130">`CREATE TABLE` ステートメントを使用してメモリ最適化テーブルを作成すると、テーブル情報がデータベース メタデータに書き込まれ、テーブルとインデックス構造がメモリに作成されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-130">Creating a memory-optimized table using the `CREATE TABLE` statement results in the table information being written to the database metadata and the table and index structures created in memory.</span></span> <span data-ttu-id="ddd41-131">また、テーブルは DLL にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-131">The table will also be compiled to a DLL.</span></span>  
  
 <span data-ttu-id="ddd41-132">データベースとメモリ最適化テーブルを作成する、次のサンプル スクリプトについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-132">Consider the following sample script, which creates a database and a memory-optimized table:</span></span>  
  
```sql  
use master  
go  
create database db1  
go  
alter database db1 add filegroup db1_mod contains memory_optimized_data  
go  
-- adapt filename as needed  
alter database db1 add file (name='db1_mod', filename='c:\data\db1_mod') to filegroup db1_mod  
go  
use db1  
go  
create table dbo.t1  
   (c1 int not null primary key nonclustered,  
    c2 INT)  
with (memory_optimized=on)  
go  
-- retrieve the path of the DLL for table t1  
select name, description FROM sys.dm_os_loaded_modules  
where name like '%xtp_t_' + cast(db_id() as varchar(10)) + '_' + cast(object_id('dbo.t1') as varchar(10)) + '.dll'  
go  
```  
  
 <span data-ttu-id="ddd41-133">テーブルを作成すると、テーブル DLL が作成され、メモリに DLL が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-133">Creating the table also creates the table DLL and loads the DLL in memory.</span></span> <span data-ttu-id="ddd41-134">CREATE TABLE ステートメントの直後の DMV クエリは、テーブル DLL のパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ddd41-134">The DMV query immediately after the CREATE TABLE statement retrieves the path of the table DLL.</span></span>  
  
 <span data-ttu-id="ddd41-135">テーブル DLL は、テーブルのインデックス構造と行形式を理解します。</span><span class="sxs-lookup"><span data-stu-id="ddd41-135">The table DLL understands the index structures and row format of the table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ddd41-136">は DLL を使用してインデックスをスキャンし、行を取得し、行のコンテンツを格納します。</span><span class="sxs-lookup"><span data-stu-id="ddd41-136">uses the DLL for traversing indexes, retrieving rows, as well as storing the contents of the rows.</span></span>  
  
## <a name="native-compilation-of-stored-procedures"></a><span data-ttu-id="ddd41-137">ストアド プロシージャのネイティブ コンパイル</span><span class="sxs-lookup"><span data-stu-id="ddd41-137">Native Compilation of Stored Procedures</span></span>  
 <span data-ttu-id="ddd41-138">NATIVE_COMPILATION が設定されているストアド プロシージャはネイティブでコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-138">Stored procedures that are marked with NATIVE_COMPILATION are natively compiled.</span></span> <span data-ttu-id="ddd41-139">つまり、パフォーマンスが重要なビジネス ロジックの効率的な実行のために、プロシージャの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがすべてネイティブ コードにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-139">This means the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the procedure are all compiled to native code for efficient execution of performance-critical business logic.</span></span>  
  
 <span data-ttu-id="ddd41-140">ネイティブ コンパイル ストアド プロシージャの詳細については、「 [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ddd41-140">For more information about natively compiled stored procedures, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="ddd41-141">前の例のテーブル t1 に行を挿入する、次のサンプル ストアド プロシージャについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-141">Consider the following sample stored procedure, which inserts rows in the table t1 from the previous example:</span></span>  
  
```sql  
create procedure dbo.native_sp  
with native_compilation, schemabinding, execute as owner  
as  
begin atomic  
with (transaction isolation level=snapshot, language=N'us_english')  
  
  declare @i int = 1000000  
  while @i > 0  
  begin  
    insert dbo.t1 values (@i, @i+1)  
    set @i -= 1  
  end  
  
end  
go  
exec dbo.native_sp  
go  
-- reset  
delete from dbo.t1  
go  
```  
  
 <span data-ttu-id="ddd41-142">行をできる限り高速に挿入するために、native_sp の DLL は t1 の DLL およびインメモリ OLTP ストレージ エンジンと直接やり取りできます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-142">The DLL for native_sp can interact directly with the DLL for t1, as well as the In-Memory OLTP storage engine, to insert the rows as fast as possible.</span></span>  
  
 <span data-ttu-id="ddd41-143">インメモリ OLTP コンパイラは、ストアド プロシージャの各クエリに有効な実行プランを作成するためにクエリ オプティマイザーを活用します。</span><span class="sxs-lookup"><span data-stu-id="ddd41-143">The In-Memory OLTP compiler leverages the query optimizer to create an efficient execution plan for each of the queries in the stored procedure.</span></span> <span data-ttu-id="ddd41-144">テーブルのデータが変更された場合はネイティブ コンパイル ストアド プロシージャは自動的に再コンパイルされないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ddd41-144">Note that natively compiled stored procedures are not automatically recompiled if the data in the table changes.</span></span> <span data-ttu-id="ddd41-145">インメモリ OLTP の統計とストアド プロシージャの管理の詳細については、「 [メモリ最適化テーブルの統計](memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddd41-145">For more information on maintaining statistics and stored procedures with In-Memory OLTP see [Statistics for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="security-considerations-for-native-compilation"></a><span data-ttu-id="ddd41-146">ネイティブ コンパイルにおけるセキュリティの注意点</span><span class="sxs-lookup"><span data-stu-id="ddd41-146">Security Considerations for Native Compilation</span></span>  
 <span data-ttu-id="ddd41-147">テーブルおよびストアド プロシージャのネイティブ コンパイルでは、インメモリ OLTP コンパイラを使用します。</span><span class="sxs-lookup"><span data-stu-id="ddd41-147">Native compilation of tables and stored procedures uses the In-Memory OLTP compiler.</span></span> <span data-ttu-id="ddd41-148">このコンパイラはファイルを生成し、そのファイルがディスクに書き込まれて、メモリに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-148">This compiler produces files that are written to disk and loaded into memory.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ddd41-149">では、これらのファイルへのアクセスを制限するために、次のメカニズムを使用しています。</span><span class="sxs-lookup"><span data-stu-id="ddd41-149">uses the following mechanisms to limit access to these files.</span></span>  
  
### <a name="native-compiler"></a><span data-ttu-id="ddd41-150">ネイティブ コンパイラ</span><span class="sxs-lookup"><span data-stu-id="ddd41-150">Native Compiler</span></span>  
 <span data-ttu-id="ddd41-151">コンパイラの実行可能ファイルと、ネイティブ コンパイルに必要なバイナリおよびヘッダー ファイルは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの一部として MSSQL\Binn\Xtp フォルダー内にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-151">The compiler executable, as well as binaries and header files required for native compilation are installed as part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance under the folder MSSQL\Binn\Xtp.</span></span> <span data-ttu-id="ddd41-152">そのため、既定のインスタンスが c:\program files の下にインストールされている場合、コンパイラファイルは c:\program files \MSSQL12. にインストールされます。 \\ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]MSSQLSERVER\MSSQL\Binn\Xtp.</span><span class="sxs-lookup"><span data-stu-id="ddd41-152">So, if the default instance is installed under C:\Program Files, the compiler files are installed in C:\Program Files\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn\Xtp.</span></span>  
  
 <span data-ttu-id="ddd41-153">コンパイラへのアクセスを制限するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、バイナリ ファイルへのアクセスを制限するアクセス制御リスト (ACL) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-153">To limit access to the compiler, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses access control lists (ACLs) to restrict access to binary files.</span></span> <span data-ttu-id="ddd41-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのバイナリは、変更や改ざんが起こらないよう ACL で保護されています。</span><span class="sxs-lookup"><span data-stu-id="ddd41-154">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries are protected against modification or tampering through ACLs.</span></span> <span data-ttu-id="ddd41-155">ネイティブ コンパイラの ACL では、コンパイラの使用も制限されます。ネイティブ コンパイラ ファイルに対する読み取り権限と実行権限を持っているのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントとシステム管理者のみです。</span><span class="sxs-lookup"><span data-stu-id="ddd41-155">The native compiler's ACLs also limit use of the compiler; only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and system administrators have read and execute permissions for native compiler files.</span></span>  
  
### <a name="files-generated-by-a-native-compilation"></a><span data-ttu-id="ddd41-156">ネイティブ コンパイルによって生成されるファイル</span><span class="sxs-lookup"><span data-stu-id="ddd41-156">Files Generated by a Native Compilation</span></span>  
 <span data-ttu-id="ddd41-157">テーブルまたはストアド プロシージャのコンパイル時に生成されるファイルには、DLL のほか、.c、.obj、.xml、.pdb などの拡張子を持つ中間ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="ddd41-157">The files produced when a table or stored procedure is compiled include the DLL and intermediate files including files with the following extensions: .c, .obj, .xml, and .pdb.</span></span> <span data-ttu-id="ddd41-158">生成されたファイルは、既定のデータ フォルダーのサブフォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-158">The generated files are saved in a subfolder of the default data folder.</span></span> <span data-ttu-id="ddd41-159">サブフォルダーは Xtp と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-159">The subfolder is called Xtp.</span></span> <span data-ttu-id="ddd41-160">既定のデータフォルダーを使用して既定のインスタンスをインストールすると、生成されたファイルは C:\Program files \MSSQL12. に配置されます。 \\ [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]MSSQLSERVER\MSSQL\DATA\Xtp.</span><span class="sxs-lookup"><span data-stu-id="ddd41-160">When installing the default instance with the default data folder, the generated files are placed in C:\Program Files\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\DATA\Xtp.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ddd41-161">は 3 とおりの方法で、生成した DLL に対する改ざんを回避します。</span><span class="sxs-lookup"><span data-stu-id="ddd41-161">prevents tampering with the generated DLLs in three ways:</span></span>  
  
-   <span data-ttu-id="ddd41-162">テーブルまたはストアド プロシージャが DLL にコンパイルされると、この DLL は直ちにメモリに読み込まれ、sqlserver.exe プロセスにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-162">When a table or stored procedure is compiled to a DLL, this DLL is immediately loaded into memory and linked to the sqlserver.exe process.</span></span> <span data-ttu-id="ddd41-163">プロセスにリンクされている間、その DLL は変更できません。</span><span class="sxs-lookup"><span data-stu-id="ddd41-163">A DLL cannot be modified while it is linked to a process.</span></span>  
  
-   <span data-ttu-id="ddd41-164">データベースを再起動すると、データベースのメタデータに基づいて、すべてのテーブルとストアド プロシージャが再コンパイル (削除後、再作成) されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-164">When a database is restarted, all tables and stored procedures are recompiled (removed and recreated) based on the database metadata.</span></span> <span data-ttu-id="ddd41-165">これにより、生成されたファイルに対して悪意のあるエージェントによって行われた変更があれば、すべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-165">This will remove any changes made to a generated file by a malicious agent.</span></span>  
  
-   <span data-ttu-id="ddd41-166">生成されたファイルはユーザー データの一部と見なされ、ACL を介して、データベース ファイルと同じセキュリティ制限が適用されます。これらのファイルにアクセスできるのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントとシステム管理者のみです。</span><span class="sxs-lookup"><span data-stu-id="ddd41-166">The generated files are considered part of user data, and have the same security restrictions, via ACLs, as database files: only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account and system administrators can access these files.</span></span>  
  
 <span data-ttu-id="ddd41-167">これらのファイルの管理には、ユーザー操作は不要です。</span><span class="sxs-lookup"><span data-stu-id="ddd41-167">No user interaction is needed to manage these files.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ddd41-168">により、必要に応じてファイルの作成および削除が行われます。</span><span class="sxs-lookup"><span data-stu-id="ddd41-168">will create and remove the files as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd41-169">参照</span><span class="sxs-lookup"><span data-stu-id="ddd41-169">See Also</span></span>  
 <span data-ttu-id="ddd41-170">[メモリ最適化テーブル](memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="ddd41-170">[Memory-Optimized Tables](memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="ddd41-171">ネイティブ コンパイル ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ddd41-171">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
