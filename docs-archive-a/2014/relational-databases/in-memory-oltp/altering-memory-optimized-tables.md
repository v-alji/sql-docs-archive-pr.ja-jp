---
title: メモリ最適化テーブルの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
author: rothja
ms.author: jroth
ms.openlocfilehash: 4eedc6fdb45efc6c87765cd2208ead90c1887c27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644469"
---
# <a name="altering-memory-optimized-tables"></a><span data-ttu-id="13b18-102">メモリ最適化テーブルの変更</span><span class="sxs-lookup"><span data-stu-id="13b18-102">Altering Memory-Optimized Tables</span></span>
  <span data-ttu-id="13b18-103">メモリ最適化テーブルに対する ALTER 操作はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="13b18-103">Performing ALTER operations on memory-optimized tables is not supported.</span></span> <span data-ttu-id="13b18-104">これには、bucket_count の変更、インデックスの追加または削除、列の追加または削除などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="13b18-104">This includes such operations as changing the bucket_count, adding or removing an index, and adding or removing a column.</span></span> <span data-ttu-id="13b18-105">このトピックでは、メモリ最適化テーブルを更新する方法のガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="13b18-105">This topic provides guidelines on how to update memory-optimized tables.</span></span>  
  
## <a name="updating-the-definition-of-a-memory-optimized-table"></a><span data-ttu-id="13b18-106">メモリ最適化テーブルの定義の更新</span><span class="sxs-lookup"><span data-stu-id="13b18-106">Updating the Definition of a Memory-Optimized Table</span></span>  
 <span data-ttu-id="13b18-107">メモリ最適化テーブルの定義を更新すると、更新されたテーブル定義を使用して新しいテーブルを作成し、新しいテーブルにデータをコピーし、新しいテーブルの使用を開始することが必要になります。</span><span class="sxs-lookup"><span data-stu-id="13b18-107">Updating the definition of a memory-optimized table requires you to create a new table with the updated table definition, copy the data to the new table, and start using the new table.</span></span> <span data-ttu-id="13b18-108">テーブルが読み取り専用でない限り、データ コピーが行われている間にテーブルに変更が行われないように、テーブル上のワークロードを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13b18-108">Unless the table is read-only, this requires stopping the workload on the table, to ensure no changes are made to the table while the data copy is performed.</span></span>  
  
 <span data-ttu-id="13b18-109">以下に、テーブルの更新手順の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="13b18-109">The following procedure outlines the steps required to update a table.</span></span> <span data-ttu-id="13b18-110">この例では、インデックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="13b18-110">In this example, the update adds an index.</span></span> <span data-ttu-id="13b18-111">この手順はテーブルの名前を保持し、一時テーブルに 1 回、新しいテーブルに 1 回の、2 つのデータ コピー操作が必要となります。</span><span class="sxs-lookup"><span data-stu-id="13b18-111">This procedure preserves the name of the table and requires two data copy operations: once to a temporary table, and once to the new table.</span></span> <span data-ttu-id="13b18-112">インデックスの bucket_count の変更や、列の追加または削除も同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="13b18-112">Changing the bucket_count of an index or adding or removing a column is performed the same way.</span></span>  
  
1.  <span data-ttu-id="13b18-113">テーブル上のワークロードを停止します。</span><span class="sxs-lookup"><span data-stu-id="13b18-113">Stop the workload on the table.</span></span>  
  
2.  <span data-ttu-id="13b18-114">テーブルのスクリプトを生成し、スクリプトに新しいインデックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="13b18-114">Generate script for the table and add the new index to the script.</span></span>  
  
3.  <span data-ttu-id="13b18-115">T とその権限を参照するスキーマ バインド オブジェクト (主にネイティブ コンパイル ストアド プロシージャ) のスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="13b18-115">Generate script for the schema-bound objects (mainly natively compiled stored procedures) referencing T and their permissions.</span></span>  
  
     <span data-ttu-id="13b18-116">テーブルを参照するスキーマ バインド オブジェクトは、次のクエリを使用して見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="13b18-116">The schema-bound objects referencing the table can be found using the following query:</span></span>  
  
    ```sql  
    declare @t nvarchar(255) = N'<table name>'  
  
    select r.referencing_schema_name, r.referencing_entity_name  
    from sys.dm_sql_referencing_entities (@t, 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
    where r.is_caller_dependent = 0 and m.is_schema_bound=1;  
    ```  
  
     <span data-ttu-id="13b18-117">ストアド プロシージャの権限は、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してスクリプト化できます。</span><span class="sxs-lookup"><span data-stu-id="13b18-117">The permissions of a stored procedure can be scripted using the following [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
    ```sql  
    declare @sp nvarchar(255) = N'<procedure name>'  
    declare @permissions nvarchar(max) = N''  
  
    select @permissions += dp.state_desc + N' ' + dp.permission_name + N' ON ' +   
       quotename(schema_name(o.schema_id)) + N'.' + quotename(o.name) + N' TO ' +  
       quotename(u.name) + N'; ' + char(13)  
    from sys.database_permissions as dp  
  
    join sys.database_principals as u  
       on u.principal_id = dp.grantee_principal_id  
  
    join sys.objects as o  
       on o.object_id = dp.major_id  
    where dp.class = 1 /* object */  
       and dp.minor_id = 0 and o.object_id=object_id(@sp);  
  
    select @permissions  
    ```  
  
4.  <span data-ttu-id="13b18-118">テーブルのコピーを作成し、元のテーブルからテーブルのコピーにデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="13b18-118">Create a copy of the table and copy the data from the original table to the copy of the table.</span></span> <span data-ttu-id="13b18-119">コピーは、次の1を使用して作成でき [!INCLUDE[tsql](../../includes/tsql-md.md)] <sup>1</sup>ます。</span><span class="sxs-lookup"><span data-stu-id="13b18-119">The copy can be created using the following [!INCLUDE[tsql](../../includes/tsql-md.md)]<sup>1</sup>.</span></span>  
  
    ```sql  
    select * into dbo.T_copy from dbo.T  
    ```  
  
     <span data-ttu-id="13b18-120">使用可能なメモリが十分にある場合、は `T_copy` メモリ最適化テーブルである可能性があります。これにより、データのコピーが高速になります。<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="13b18-120">If there is enough available memory, `T_copy` could be a memory-optimized table, which makes the data copy faster.<sup>2</sup></span></span>  
  
5.  <span data-ttu-id="13b18-121">元のテーブルを参照するスキーマ バインド オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="13b18-121">Drop the schema-bound objects referencing the original table.</span></span>  
  
6.  <span data-ttu-id="13b18-122">元のテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="13b18-122">Drop the original table.</span></span>  
  
7.  <span data-ttu-id="13b18-123">新しいインデックスを含むスクリプトで、新しいテーブル (`T`) を作成します。</span><span class="sxs-lookup"><span data-stu-id="13b18-123">Create the new table (`T`) with the script containing the new index.</span></span>  
  
8.  <span data-ttu-id="13b18-124">`T_copy` から `T` にデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="13b18-124">Copy the data from `T_copy` to `T`.</span></span>  
  
9. <span data-ttu-id="13b18-125">参照しているスキーマ バインド オブジェクトを再作成し、権限を適用します。</span><span class="sxs-lookup"><span data-stu-id="13b18-125">Recreate the referencing schema-bound objects and apply the permissions.</span></span>  
  
10. <span data-ttu-id="13b18-126">`T` のワークロードを起動します。</span><span class="sxs-lookup"><span data-stu-id="13b18-126">Start the workload on `T`.</span></span>  
  
 <span data-ttu-id="13b18-127"><sup>1</sup> `T_copy` この例では、がディスクに保存されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="13b18-127"><sup>1</sup> Note that `T_copy` is persisted to disk in this example.</span></span> <span data-ttu-id="13b18-128">`T` のバックアップが使用可能であれば、`T_copy` に一時的または持続性のないテーブルを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="13b18-128">If a backup of `T` is available, `T_copy` could be a temporary or a non-durable table.</span></span>  
  
 <span data-ttu-id="13b18-129"><sup>2</sup>に十分なメモリが必要 `T_copy` です。</span><span class="sxs-lookup"><span data-stu-id="13b18-129"><sup>2</sup> There must be enough memory for `T_copy`.</span></span> <span data-ttu-id="13b18-130">`DROP TABLE` ではメモリがすぐには解放されません。</span><span class="sxs-lookup"><span data-stu-id="13b18-130">Memory is not freed immediately on `DROP TABLE`.</span></span> <span data-ttu-id="13b18-131">`T_copy` がメモリ最適化されている場合は、`T` のコピーを 2 つ作成するための十分なメモリが必要です。</span><span class="sxs-lookup"><span data-stu-id="13b18-131">If `T_copy` is memory optimized, there needs to be enough memory for two additional copies of `T`.</span></span> <span data-ttu-id="13b18-132">`T_copy` がディスク ベース テーブルの場合は、`T` の古いバージョンを削除した後にガベージ コレクターによって補完されるため、`T` の付加的なコピーを 1 つ作成するためのメモリがあれば問題ありません。</span><span class="sxs-lookup"><span data-stu-id="13b18-132">If `T_copy` is a disk-based table, there only needs to be enough memory for one additional copy of `T`, due to the garbage collector needing to catch up after dropping the old version of `T`.</span></span>  
  
## <a name="changing-schema-powershell"></a><span data-ttu-id="13b18-133">スキーマの変更 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="13b18-133">Changing Schema (PowerShell)</span></span>  
 <span data-ttu-id="13b18-134">次の PowerShell スクリプトは、テーブルや関連する権限のスクリプトを作成することで、スキーマの変更に備えます。</span><span class="sxs-lookup"><span data-stu-id="13b18-134">The following PowerShell scripts prepare and generate for schema changes by scripting the table and associated permissions.</span></span>  
  
```powershell
prepare_schema_change.ps1 <serverName> <databaseName> <schemaName> <tableName>
```
  
 <span data-ttu-id="13b18-135">このスクリプトは、引数としてテーブルを受け取り、オブジェクトとその権限のスクリプトを作成し、現在のフォルダーのスキーマ バインド オブジェクトとその権限を参照します。</span><span class="sxs-lookup"><span data-stu-id="13b18-135">This script takes as arguments a table, and scripts the object and its permissions and referencing schema-bound objects and their permissions in the current folder.</span></span> <span data-ttu-id="13b18-136">入力テーブルのスキーマを更新するために、合計 7 種類のスクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="13b18-136">A total of 7 scripts are generated for updating the schema of the input table:</span></span>  
  
-   <span data-ttu-id="13b18-137">一時テーブル (ヒープ) にデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="13b18-137">Copy data to a temporary table (a heap).</span></span>  
  
-   <span data-ttu-id="13b18-138">テーブルを参照するスキーマ バインド オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="13b18-138">Drop schema-bound objects referencing the table.</span></span>  
  
-   <span data-ttu-id="13b18-139">テーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="13b18-139">Drop the table.</span></span>  
  
-   <span data-ttu-id="13b18-140">新しいスキーマでテーブルを再作成し、権限を再適用します。</span><span class="sxs-lookup"><span data-stu-id="13b18-140">Recreate the table with the new schema and reapply permissions.</span></span>  
  
-   <span data-ttu-id="13b18-141">一時テーブルから再作成されたテーブルにデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="13b18-141">Copy data from the temporary table to the recreated table.</span></span>  
  
-   <span data-ttu-id="13b18-142">テーブルとその権限を参照しているスキーマ バインド オブジェクトを再作成します。</span><span class="sxs-lookup"><span data-stu-id="13b18-142">Recreate schema-bound objects referencing the table and their permissions.</span></span>  
  
-   <span data-ttu-id="13b18-143">一時テーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="13b18-143">Drop the temporary table.</span></span>  
  
 <span data-ttu-id="13b18-144">目的のスキーマの変更を反映するように、手順 4. のスクリプトを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13b18-144">The script for step 4 should be updated to reflect the desired schema changes.</span></span> <span data-ttu-id="13b18-145">テーブルの列に変更がある場合は、手順 5. (一時テーブルからのデータのコピー) および 6 (ストアドプロシージャの再作成) のスクリプトを必要に応じて更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13b18-145">If there are any changes in the columns of the table, the scripts for steps 5 (copy data from temporary table) and 6 (recreate stored procedures) should be updated as necessary.</span></span>  
  
```powershell
# Prepare for schema changes by scripting out the table, as well as associated permissions
# Usage: prepare_schema_change.ps1 server_name db_name schema_name table_name  
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage prepare_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
$object_heap = "$object$(Get-Random)"  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$scripter = New-Object ("Microsoft.SqlServer.Management.SMO.Scripter") ($server)  
  
## initialize table variable  
$tableUrn = $server.Databases[$database].Tables[$object, $schema]  
if($tableUrn.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
## initialize scripting object  
$scriptingOptions = New-Object ("Microsoft.SqlServer.Management.SMO.ScriptingOptions")
$scriptingOptions.Permissions = $True  
$scriptingOptions.ScriptDrops = $True  
  
$scripter.Options = $scriptingOptions;  
  
Write-Host "(1) Scripting SELECT INTO $object_heap for table [$object] to 1_copy_to_heap_for_$schema`_$object.sql"  
Echo "SELECT * INTO $schema.$object_heap FROM $schema.$object WITH (SNAPSHOT)" | Out-File "1_copy_to_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Scripting DROP for procs schema-bound to [$object] 2_drop_procs_$schema`_$object.sql"  
## query referencing schema-bound objects  
$dt = $server.Databases[$database].ExecuteWithResults("select r.referencing_schema_name, r.referencing_entity_name  
from sys.dm_sql_referencing_entities ('$schema.$object', 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
where r.is_caller_dependent = 0 and m.is_schema_bound=1;")  
  
## initialize out file  
Echo "" | Out-File "2_drop_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script object   
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      $scripter.Script($so) | Out-File -Append "2_drop_procs_$schema`_$object.sql"  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
Write-Host "(3) Scripting DROP table for [$object] to 3_drop_table_$schema`_$object.sql"
$scripter.Script($tableUrn) | Out-File "3_drop_table_$schema`_$object.sql";
Write-Host "--done--"  
Write-Host ""  
  
## now script creates  
$scriptingOptions.ScriptDrops = $False  
  
Write-Host "(4) Scripting CREATE table and permissions for [$object] to !please_edit_4_create_table_$schema`_$object.sql"  
Write-Host "***** rename this script to 4_create_table.sql after completing the updates to the schema"
$scripter.Script($tableUrn) | Out-File "!please_edit_4_create_table_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Scripting INSERT INTO table from heap and UPDATE STATISTICS for [$object] to 5_copy_from_heap_$schema`_$object.sql"  
Write-Host "[update this script if columns are added to or removed from the table]"  
Echo "INSERT INTO [$schema].[$object] SELECT * FROM [$schema].[$object_heap]; UPDATE STATISTICS [$schema].[$object] WITH FULLSCAN, NORECOMPUTE" | Out-File "5_copy_from_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Scripting CREATE PROC and permissions for procedures schema-bound to [$object] to 6_create_procs_$schema`_$object.sql"  
Write-Host "[update the procedure definitions if columns are renamed or removed]"  
## initialize out file  
Echo "" | Out-File "6_create_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script the schema-bound object  
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      ForEach($s In $scripter.Script($so))  
        {  
            Echo $s | Out-File -Append "6_create_procs_$schema`_$object.sql"  
            Echo "GO" | Out-File -Append "6_create_procs_$schema`_$object.sql"  
        }  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Scripting DROP $object_heap to 7_drop_heap_$schema`_$object.sql"  
Echo "DROP TABLE $schema.$object_heap" | Out-File "7_drop_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
```  
  
 <span data-ttu-id="13b18-146">次の PowerShell スクリプトでは、前のサンプルでスクリプトを作成したスキーマの変更を実行します。</span><span class="sxs-lookup"><span data-stu-id="13b18-146">The following PowerShell script executes the schema changes that were scripted in the previous sample.</span></span> <span data-ttu-id="13b18-147">このスクリプトは、テーブルを引数として受け取り、このテーブルや関連付けられたストアド プロシージャ用に生成されたスキーマ変更スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="13b18-147">This script takes as argument a table, and executes the schema change scripts that were generated for that table and the associated stored procedures.</span></span>  
  
 <span data-ttu-id="13b18-148">使用法: execute_schema_change.ps1 *server_name \* \* db_name `schema_name` table_name*</span><span class="sxs-lookup"><span data-stu-id="13b18-148">Usage: execute_schema_change.ps1 *server_name\*\*db_name`schema_name`table_name*</span></span>  
  
```powershell
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage execute_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$database = $server.Databases[$database]  
$table = $database.Tables[$object, $schema]  
if($table.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
$1 = Get-Item "1_copy_to_heap_$schema`_$object.sql"  
$2 = Get-Item "2_drop_procs_$schema`_$object.sql"  
$3 = Get-Item "3_drop_table_$schema`_$object.sql"  
$4 = Get-Item "4_create_table_$schema`_$object.sql"  
$5 = Get-Item "5_copy_from_heap_$schema`_$object.sql"  
$6 = Get-Item "6_create_procs_$schema`_$object.sql"  
$7 = Get-Item "7_drop_heap_$schema`_$object.sql"  
  
Write-Host "(1) Running SELECT INTO heap for table [$object] from 1_copy_to_heap_for_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $1.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Running DROP for procs schema-bound from [$object] 2_drop_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $2.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(3) Running DROP table for [$object] to 4_drop_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $3.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(4) Running CREATE table and permissions for [$object] from 4_create_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $4.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Running INSERT INTO table from heap for [$object] and UPDATE STATISTICS from 5_copy_from_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $5.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Running CREATE PROC and permissions for procedures schema-bound to [$object] from 6_create_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $6.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Running DROP heap from 7_drop_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $7.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
```  
  
## <a name="see-also"></a><span data-ttu-id="13b18-149">参照</span><span class="sxs-lookup"><span data-stu-id="13b18-149">See Also</span></span>  
 [<span data-ttu-id="13b18-150">メモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="13b18-150">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
