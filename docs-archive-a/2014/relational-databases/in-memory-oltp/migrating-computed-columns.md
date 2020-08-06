---
title: 計算列の移行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 64a9eade-22c3-4a9d-ab50-956219e08df1
author: rothja
ms.author: jroth
ms.openlocfilehash: feb50ef64f42d95913ad4e13f9a79e6e0e4ecad3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742097"
---
# <a name="migrating-computed-columns"></a><span data-ttu-id="2a79c-102">計算列の移行</span><span class="sxs-lookup"><span data-stu-id="2a79c-102">Migrating Computed Columns</span></span>
  <span data-ttu-id="2a79c-103">計算列は、メモリ最適化テーブルではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2a79c-103">Computed columns are not supported in memory-optimized tables.</span></span> <span data-ttu-id="2a79c-104">ただし、計算列をシミュレートすることはできます。</span><span class="sxs-lookup"><span data-stu-id="2a79c-104">However, you can simulate a computed column.</span></span>  
  
 <span data-ttu-id="2a79c-105">ディスク ベース テーブルをメモリ最適化テーブルに移行するときは、計算列を保存する必要性を検討してください。</span><span class="sxs-lookup"><span data-stu-id="2a79c-105">You should consider the need to persist your computed columns when you migrate your disk-based tables to memory-optimized tables.</span></span> <span data-ttu-id="2a79c-106">メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャのさまざまなパフォーマンス特性によって、保存の必要性がなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2a79c-106">The different performance characteristics of memory-optimized tables and natively compiled stored procedures may negate the need for persistence.</span></span>  
  
## <a name="non-persisted-computed-columns"></a><span data-ttu-id="2a79c-107">保存されない計算列</span><span class="sxs-lookup"><span data-stu-id="2a79c-107">Non-Persisted Computed Columns</span></span>  
 <span data-ttu-id="2a79c-108">保存されない計算列の効果をシミュレートするには、メモリ最適化テーブルのビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="2a79c-108">To simulate the effects of a non-persisted computed column, create a view on the memory-optimized table.</span></span> <span data-ttu-id="2a79c-109">ビューを定義する SELECT ステートメントで、計算列の定義をビューに追加します。</span><span class="sxs-lookup"><span data-stu-id="2a79c-109">In the SELECT statement that defines the view, add the computed column definition into the view.</span></span> <span data-ttu-id="2a79c-110">ネイティブ コンパイル ストアド プロシージャ内を除き、計算列からの値を使用するクエリは、このビューから読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a79c-110">Except in a natively compiled stored procedure, queries that use values from the computed column should read from the view.</span></span> <span data-ttu-id="2a79c-111">ネイティブ コンパイル ストアド プロシージャ内では、計算列の定義によって、SELECT、UPDATE、または DELETE ステートメントを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a79c-111">Inside natively compiled stored procedures, you should update any select, update, or delete statement according to your computed column definition.</span></span>  
  
```sql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is not persisted.  
CREATE VIEW dbo.v_order_details AS  
   SELECT  
      OrderId,  
      ProductId,  
      SalePrice,  
      Quantity,  
      Quantity * SalePrice AS Total  
   FROM dbo.order_details  
```  
  
## <a name="persisted-computed-columns"></a><span data-ttu-id="2a79c-112">保存される計算列</span><span class="sxs-lookup"><span data-stu-id="2a79c-112">Persisted Computed Columns</span></span>  
 <span data-ttu-id="2a79c-113">保存される計算列の効果をシミュレートするには、テーブルに挿入するためのストアド プロシージャとテーブルを更新するためのストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="2a79c-113">To simulate the effects of a persisted computed column, create a stored procedure for inserting into the table and another stored procedure for updating the table.</span></span> <span data-ttu-id="2a79c-114">テーブルに対する挿入または更新を行う場合、これらのストアド プロシージャを呼び出してそれぞれのタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="2a79c-114">When inserting or updating the table, invoke these stored procedures to perform these tasks.</span></span> <span data-ttu-id="2a79c-115">ストアド プロシージャ内では、元のディスク ベース テーブルでの計算列の定義のように、入力に従って算定フィールドの値を計算します。</span><span class="sxs-lookup"><span data-stu-id="2a79c-115">Inside the stored procedures, calculate the value for the computed field according to the inputs, much like how the computed column is defined on the original disk-based table.</span></span> <span data-ttu-id="2a79c-116">次に、ストアド プロシージャ内では必要に応じて、テーブルに対する挿入を更新を実行します。</span><span class="sxs-lookup"><span data-stu-id="2a79c-116">Then, insert or update the table as needed inside the stored procedure.</span></span>  
  
```sql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is persisted.  
-- we need to create insert and update procedures to calculate Total.  
CREATE PROCEDURE sp_insert_order_details   
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  
-- compute the value here.   
-- this stored procedure works with single rows only.  
-- for bulk inserts, accept a table-valued parameter into the stored procedure  
-- and use an INSERT INTO SELECT statement.  
DECLARE @total money = @SalePrice * @Quantity  
INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  
-- compute the value here.   
-- this stored procedure works with single rows only.  
DECLARE @total money = @SalePrice * @Quantity  
UPDATE dbo.OrderDetails   
SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
WHERE OrderId = @OrderId  
END  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a79c-117">参照</span><span class="sxs-lookup"><span data-stu-id="2a79c-117">See Also</span></span>  
 [<span data-ttu-id="2a79c-118">インメモリ OLTP への移行</span><span class="sxs-lookup"><span data-stu-id="2a79c-118">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
