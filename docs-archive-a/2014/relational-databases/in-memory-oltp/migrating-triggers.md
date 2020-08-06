---
title: トリガーの移行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
author: rothja
ms.author: jroth
ms.openlocfilehash: 25965e7cce84b0dcfcd3b6ce6176e8ad3ddabc6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742086"
---
# <a name="migrating-triggers"></a><span data-ttu-id="6b120-102">トリガーの移行</span><span class="sxs-lookup"><span data-stu-id="6b120-102">Migrating Triggers</span></span>
  <span data-ttu-id="6b120-103">このトピックでは、DDL トリガーと DML トリガー、およびメモリ最適化テーブルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6b120-103">This topic discusses DDL and DML triggers and memory-optimized tables.</span></span>  
  
 <span data-ttu-id="6b120-104">LOGON トリガーとは、LOGON イベントで起動するように定義されたトリガーです。</span><span class="sxs-lookup"><span data-stu-id="6b120-104">LOGON triggers are triggers defined to fire on LOGON events.</span></span> <span data-ttu-id="6b120-105">LOGON トリガーは、メモリ最適化テーブルに影響しません。</span><span class="sxs-lookup"><span data-stu-id="6b120-105">LOGON triggers do not affect memory-optimized tables.</span></span>  
  
## <a name="ddl-triggers"></a><span data-ttu-id="6b120-106">DDL トリガー</span><span class="sxs-lookup"><span data-stu-id="6b120-106">DDL Triggers</span></span>  
 <span data-ttu-id="6b120-107">DDL トリガーとは、自らを定義しているデータベースまたはサーバーに対して CREATE、ALTER、DROP、GRANT、DENY、REVOKE、または UPDATE STATISTICS の各ステートメントを実行したときに起動するように定義されているトリガーです。</span><span class="sxs-lookup"><span data-stu-id="6b120-107">DDL triggers are triggers defined to fire when a CREATE, ALTER, DROP, GRANT, DENY, REVOKE, or UPDATE STATISTICS statement is executed on the database or server on which it is defined.</span></span>  
  
 <span data-ttu-id="6b120-108">データベースまたはサーバーで、CREATE_TABLE イベントまたはこのイベントを含むイベント グループに対応する 1 つ以上の DDL トリガーが定義されている場合は、メモリ最適化テーブルを作成できません。</span><span class="sxs-lookup"><span data-stu-id="6b120-108">You cannot create memory-optimized tables if the database or server has one or more DDL trigger defined on CREATE_TABLE or any event group that includes it.</span></span> <span data-ttu-id="6b120-109">データベースまたはサーバーで、DROP_TABLE イベントまたはこのイベントを含むイベント グループに対応する 1 つ以上の DDL トリガーが定義されている場合は、メモリ最適化テーブルを削除できません。</span><span class="sxs-lookup"><span data-stu-id="6b120-109">You cannot drop a memory-optimized table if the database or server has one or more DDL trigger defined on DROP_TABLE or any event group that includes it.</span></span>  
  
 <span data-ttu-id="6b120-110">CREATE_PROCEDURE、DROP_PROCEDURE、またはこれらのイベントを含むイベント グループに対応する 1 つ以上の DDL トリガーが存在している場合は、ネイティブ コンパイル ストアド プロシージャを作成できません。</span><span class="sxs-lookup"><span data-stu-id="6b120-110">You cannot create natively compiled stored procedures if there are one or more DDL triggers on CREATE_PROCEDURE, DROP_PROCEDURE, or any event group that includes those events.</span></span>  
  
## <a name="dml-triggers"></a><span data-ttu-id="6b120-111">DML トリガー</span><span class="sxs-lookup"><span data-stu-id="6b120-111">DML Triggers</span></span>  
 <span data-ttu-id="6b120-112">メモリ最適化テーブルで DML トリガーを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="6b120-112">DML triggers cannot be defined on memory-optimized tables.</span></span> <span data-ttu-id="6b120-113">ただし、ストアド プロシージャを明示的に使用してデータの挿入、更新、または削除を実行する場合は、インメモリ OLTP により、DML トリガーと同様の効果を達成できます。</span><span class="sxs-lookup"><span data-stu-id="6b120-113">However, In-Memory OLTP allows you to achieve an effect similar to DML triggers if you explicitly use stored procedures to insert, update, or delete data.</span></span> <span data-ttu-id="6b120-114">システムにアドホック クエリが含まれている場合は、DML トリガーの結果をシミュレートする代わりに、これらのストアド プロシージャを使用してクエリを変換します。</span><span class="sxs-lookup"><span data-stu-id="6b120-114">If your system contains ad-hoc queries, convert them to use these stored procedures instead to simulate the effect of DML triggers.</span></span>  
  
 <span data-ttu-id="6b120-115">トリガー イベント (FOR/AFTER または INSTEAD OF) によっては、テーブルに対して INSERT、UPDATE、DELETE を実行する適切なストアド プロシージャをトリガーする内容を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="6b120-115">Depending on the trigger event (FOR/AFTER or INSTEAD OF), you may include the content of the trigger in the appropriate stored procedure that performs INSERT, UPDATE, or DELETE on that table.</span></span> <span data-ttu-id="6b120-116">たとえば、AFTER INSERT トリガーを移行する場合は、適切な INSERT ステートメントの後にトリガーの内容を含めることによって、挿入操作を実行するストアド プロシージャを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="6b120-116">For example, when migrating an AFTER INSERT trigger, you could alter the stored procedure that performs the insert operation by including the content of the trigger after the appropriate INSERT statement.</span></span>  
  
 <span data-ttu-id="6b120-117">インタープリターによって処理されるストアド プロシージャ、またはネイティブ コンパイル ストアド プロシージャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b120-117">You can use an interpreted stored procedure or a natively compiled stored procedure.</span></span> <span data-ttu-id="6b120-118">インタープリターによって処理されるストアド プロシージャを使用する [!INCLUDE[tsql](../../includes/tsql-md.md)] 構造のほとんどは、メモリ最適化されたテーブルに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="6b120-118">Most [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs in an interpreted stored procedure can execute on a memory-optimized table.</span></span> <span data-ttu-id="6b120-119">ただし、ネイティブ コンパイル ストアド プロシージャでは、[!INCLUDE[tsql](../../includes/tsql-md.md)] 構造のサブセットのみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6b120-119">However, only a subset of [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs are supported in natively compiled stored procedures.</span></span> <span data-ttu-id="6b120-120">[!INCLUDE[tsql](../../includes/tsql-md.md)]メモリ最適化テーブルのサポートの詳細については、「解釈された[Transact-sql を使用したメモリ最適化テーブルへのアクセス](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b120-120">For information on [!INCLUDE[tsql](../../includes/tsql-md.md)] support on memory-optimized tables, see [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).</span></span> <span data-ttu-id="6b120-121">[!INCLUDE[tsql](../../includes/tsql-md.md)]ネイティブコンパイルストアドプロシージャのサポートの詳細については、「インメモリ OLTP でサポートされて[いない Transact-sql の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b120-121">For information on [!INCLUDE[tsql](../../includes/tsql-md.md)] support in natively compiled stored procedures, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
 <span data-ttu-id="6b120-122">次に、メモリ最適化テーブルに対する DML トリガーの動作をシミュレートする簡単な例を示します。</span><span class="sxs-lookup"><span data-stu-id="6b120-122">The following is a simple example of simulating DML trigger behavior on a memory-optimized table.</span></span>  
  
 <span data-ttu-id="6b120-123">このデータベースには、CREATE TABLE、CREATE TRIGGER、および CREATE PROCEDURE の各ステートメントを使用してスクリプト化した次のオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b120-123">The database contains the following objects, scripted as CREATE TABLE, CREATE TRIGGER, and CREATE PROCEDURE statements:</span></span>  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null primary key,  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
)  
GO  
  
CREATE TRIGGER tr_order_details_insteadof_insert  
ON OrderDetails  
INSTEAD OF INSERT AS  
BEGIN  
   DECLARE @pid int, @qty_buy int, @qty_remain int  
   SELECT @pid = ProductId, @qty_buy = Quantity FROM inserted  
   SELECT @qty_remain = Quantity FROM Inventory WHERE ProductId = @pid  
   IF (@qty_remain <= @qty_buy)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      SELECT OrderId, ProductId, SalePrice, Quantity, Total FROM inserted  
      UPDATE Inventory SET Quantity = Quantity - @qty_buy WHERE ProductId = @pid  
   END  
END  
GO  
  
CREATE TRIGGER tr_order_details_after_update  
ON OrderDetails  
AFTER UPDATE AS  
BEGIN  
   INSERT INTO UpdateNotifications (OrderId, UpdateTime) SELECT OrderId, GETDATE() FROM inserted     
END  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
AS BEGIN  
   INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
   VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
AS BEGIN  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
END  
GO  
```  
  
 <span data-ttu-id="6b120-124">次の各オブジェクトは、移行前の状態と機能的に等価です。</span><span class="sxs-lookup"><span data-stu-id="6b120-124">The following objects are functionally equivalent to the pre-migration state:</span></span>  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 1048576),  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE Inventory  
(  
   ProductId int not null PRIMARY KEY NONCLUSTERED,  
   Quantity int not null  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE UpdateNotifications  
(  
   OrderId int not null,  
   UpdateTime datetime2 not null  
   CONSTRAINT pk_updateNotifications PRIMARY KEY NONCLUSTERED (OrderId, UpdateTime)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   DECLARE @qty_remain int  
   SELECT @qty_remain = Quantity FROM dbo.Inventory WHERE ProductId = @ProductId  
   IF (@qty_remain <= @Quantity)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
      UPDATE dbo.Inventory SET Quantity = Quantity - @Quantity WHERE ProductId = @ProductId  
   END  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
   INSERT INTO dbo.UpdateNotifications (OrderId, UpdateTime) VALUES (@OrderId, GETDATE())  
END  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b120-125">参照</span><span class="sxs-lookup"><span data-stu-id="6b120-125">See Also</span></span>  
 [<span data-ttu-id="6b120-126">インメモリ OLTP への移行</span><span class="sxs-lookup"><span data-stu-id="6b120-126">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
