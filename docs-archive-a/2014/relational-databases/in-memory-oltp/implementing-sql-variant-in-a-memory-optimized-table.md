---
title: メモリ最適化テーブルへの SQL_VARIANT の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f17f21df-959d-4e20-92f3-bd707d555a46
author: rothja
ms.author: jroth
ms.openlocfilehash: b6cffacc2ab4e8768adbfeace0eafa60f551f278
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631013"
---
# <a name="implementing-sql_variant-in-a-memory-optimized-table"></a><span data-ttu-id="3b577-102">メモリ最適化テーブルへの SQL_VARIANT の実装</span><span class="sxs-lookup"><span data-stu-id="3b577-102">Implementing SQL_VARIANT in a Memory-Optimized Table</span></span>
  <span data-ttu-id="3b577-103">例として `SQL_VARIANT` 列を含むテーブルを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="3b577-103">Consider an example of a table with `SQL_VARIANT` column:</span></span>  
  
```sql  
CREATE TABLE [dbo].[T1]([Key] [sql_variant] NOT NULL)  
```  
  
 <span data-ttu-id="3b577-104">キー列が `BIGINT` または `NVARCHAR(300)` のどちらかであると仮定します。</span><span class="sxs-lookup"><span data-stu-id="3b577-104">Assume that the key column can only be either a `BIGINT` or `NVARCHAR(300)`.</span></span> <span data-ttu-id="3b577-105">このテーブルを次のように作成できます。</span><span class="sxs-lookup"><span data-stu-id="3b577-105">You can model this table as follows:</span></span>  
  
```sql  
-- original disk-based table  
CREATE TABLE [dbo].[T1_disk]([Key] int not null primary key,  
       [Value] [sql_variant])  
go  
  
insert dbo.T1_disk values (1, 12345678)  
insert dbo.T1_disk values (2, N'my nvarchar')  
insert dbo.T1_disk values (3, NULL)  
go  
  
-- new memory-optimized table  
CREATE TABLE [dbo].[T1_inmem]([Key] INT NOT NULL PRIMARY KEY NONCLUSTERED,  
       [Value_bi] BIGINT,  
       [Value_nv] NVARCHAR(300),  
       [Value_enum] TINYINT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
go  
  
-- copy data   
INSERT INTO dbo.T1_inmem  
  SELECT [Key],  
              CASE WHEN SQL_VARIANT_PROPERTY([Value], 'basetype') = 'bigint' THEN convert (bigint, [Value])  
              ELSE NULL END,  
              CASE WHEN SQL_VARIANT_PROPERTY([Value], 'basetype') != 'bigint' THEN convert (nvarchar(300), [Value])  
              ELSE NULL END,  
              CASE WHEN SQL_VARIANT_PROPERTY([Value], 'basetype') = 'bigint' THEN 1  
              ELSE 0 END  
  FROM dbo.T1_disk  
GO  
  
-- select data, converting back to sql_variant [will not work inside native proc]  
select [Key],   
       case [Value_enum] when 1 then convert(sql_variant, [Value_bi])   
    else convert(sql_variant, [Value_nv])   
    end  
from dbo.T1_inmem  
```  
  
 <span data-ttu-id="3b577-106">ここで、T1 でカーソルを開くことによって、T1 から [T1_HK] にデータを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="3b577-106">Now you can load data into [T1_HK] from T1 by opening a cursor on T1:</span></span>  
  
```sql  
DECLARE T1_rows_cursor CURSOR FOR    
select *  
FROM dbo.T1  
  
OPEN T1_rows_cursor     
  
-- declare 1 variable each for column in HK table  
  
Declare  
@Key_biBIGINT = 0,  
@Key_nvnvarchar(300)= ' ',  
@Key_enumsmallint,  
@Keysql_variant  
  
FETCH NEXT FROM T1_rows_cursor INTO @key  
  
WHILE @@FETCH_STATUS = 0     
BEGIN     
  
-- setting the input parameters for inserting into the memory-optimized table  
-- convert SQL Variant types  
-- @key_enum =1 represents BIGINT  
if (SQL_VARIANT_PROPERTY(@Key, 'basetype') = 'bigint')  
begin  
set @key_bi = convert (bigint, @Key)  
set @key_enum = 1  
set @key_nv = 'invalid'  
end  
else  
begin  
set @Key_nv = convert (nvarchar (300), @Key)  
set @Key_enum = 0  
set @Key_bi = -1  
end  
  
-- inserting the row  
INSERT INTO T1_HK VALUES (@Key_bi, @Key_nv, @Key_enum)  
  
FETCH NEXT FROM T1_rows_cursor INTO @key  
END  
  
CLOSE T1_rows_cursor     
DEALLOCATE T1_rows_cursor  
```  
  
 <span data-ttu-id="3b577-107">次のように `SQL_VARIANT` にデータを変換します。</span><span class="sxs-lookup"><span data-stu-id="3b577-107">You can convert data back to `SQL_VARIANT` as follows:</span></span>  
  
```sql  
case [Key_enum] when 1 then convert(sql_variant, [Key_bi])   
                       else convert(sql_variant, [Key_nv])   
                       end  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b577-108">参照</span><span class="sxs-lookup"><span data-stu-id="3b577-108">See Also</span></span>  
 [<span data-ttu-id="3b577-109">インメモリ OLTP への移行</span><span class="sxs-lookup"><span data-stu-id="3b577-109">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
