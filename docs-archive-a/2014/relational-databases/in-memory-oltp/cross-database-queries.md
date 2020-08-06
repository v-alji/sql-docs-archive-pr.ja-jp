---
title: 複数データベースのクエリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
author: rothja
ms.author: jroth
ms.openlocfilehash: 4afbb580a55273ec241005493fd37f99e98ec0e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633845"
---
# <a name="cross-database-queries"></a><span data-ttu-id="25950-102">複数データベースにまたがるクエリ</span><span class="sxs-lookup"><span data-stu-id="25950-102">Cross-Database Queries</span></span>
  <span data-ttu-id="25950-103">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、メモリ最適化テーブルで複数データベースにまたがるトランザクションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="25950-103">In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], memory-optimized tables do not support cross-database transactions.</span></span> <span data-ttu-id="25950-104">メモリ最適化テーブルにもアクセスする同じトランザクションまたは同じクエリから別のデータベースにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="25950-104">You cannot access another database from the same transaction or the same query that also accesses a memory-optimized table.</span></span> <span data-ttu-id="25950-105">あるデータベースのテーブルから別のデータベースのメモリ最適化テーブルに、データを簡単にコピーすることはできません。</span><span class="sxs-lookup"><span data-stu-id="25950-105">You cannot easily copy data from a table in one database, to a memory-optimized table in another database.</span></span>  
  
 <span data-ttu-id="25950-106">テーブル変数はトランザクション処理されません。</span><span class="sxs-lookup"><span data-stu-id="25950-106">Table variables are not transactional.</span></span> <span data-ttu-id="25950-107">そのため、メモリ最適化テーブル変数を複数データベースにまたがるクエリで使用して、あるデータベースのデータを別のデータベースのメモリ最適化テーブルに簡単に移動できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="25950-107">Therefore, memory-optimized table variables can be used in cross-database queries, and can thus facilitate moving data from one database into memory-optimized tables in another.</span></span> <span data-ttu-id="25950-108">2 つのトランザクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="25950-108">You can use two transactions.</span></span> <span data-ttu-id="25950-109">最初のトランザクションで、リモート テーブルから変数にデータを挿入します。</span><span class="sxs-lookup"><span data-stu-id="25950-109">In the first transaction, insert the data from the remote table into the variable.</span></span> <span data-ttu-id="25950-110">2 つ目のトランザクションで、ローカルなメモリ最適化テーブルに変数からデータを挿入します。</span><span class="sxs-lookup"><span data-stu-id="25950-110">In the second transaction, insert the data into the local memory-optimized table from the variable.</span></span>  
  
 <span data-ttu-id="25950-111">たとえば、dbo.tt1 型の変数を使用して、データベース db1 のテーブル t1 から db2 のテーブル t2 に行をコピーするに @v1 は、次のようなコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="25950-111">For example, to copy the row from table t1 in database db1 to table t2 in db2, using variable @v1 of type dbo.tt1, you can use something like:</span></span>  
  
```sql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="25950-112">参照</span><span class="sxs-lookup"><span data-stu-id="25950-112">See Also</span></span>  
 [<span data-ttu-id="25950-113">インメモリ OLTP への移行</span><span class="sxs-lookup"><span data-stu-id="25950-113">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
