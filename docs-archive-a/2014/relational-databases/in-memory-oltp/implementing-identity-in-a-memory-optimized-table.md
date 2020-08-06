---
title: メモリ最適化テーブルへの IDENTITY の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: rothja
ms.author: jroth
ms.openlocfilehash: 955f9f1a905a9d0c71304320f60abe300e430e4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639523"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a><span data-ttu-id="2cabc-102">メモリ最適化テーブルへの IDENTITY の実装</span><span class="sxs-lookup"><span data-stu-id="2cabc-102">Implementing IDENTITY in a Memory-Optimized Table</span></span>
  <span data-ttu-id="2cabc-103">メモリ最適化テーブルでは、IDENTITY(1, 1) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2cabc-103">IDENTITY(1, 1) is supported on a memory-optimized table.</span></span> <span data-ttu-id="2cabc-104">ただし、IDENTITY(x, y) という定義を持つ ID 列で、x != 1 または y != 1 の場合は、メモリ最適化テーブルでサポートされません。</span><span class="sxs-lookup"><span data-stu-id="2cabc-104">However, identity columns with definition of IDENTITY(x, y) where x != 1 or y != 1 are not supported on memory-optimized tables.</span></span> <span data-ttu-id="2cabc-105">ID 値の回避策では、シーケンスオブジェクト ([シーケンス番号](../sequence-numbers/sequence-numbers.md)) を使用します。</span><span class="sxs-lookup"><span data-stu-id="2cabc-105">The workaround for IDENTITY values uses the SEQUENCE object ([Sequence Numbers](../sequence-numbers/sequence-numbers.md)).</span></span>  
  
 <span data-ttu-id="2cabc-106">最初に、インメモリ OLTP に変換しているテーブルから IDENTITY プロパティを削除します。</span><span class="sxs-lookup"><span data-stu-id="2cabc-106">First remove the IDENTITY property from the table you are converting to In-Memory OLTP.</span></span> <span data-ttu-id="2cabc-107">次に、テーブルの列に新しい SEQUENCE オブジェクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="2cabc-107">Then, define a new SEQUENCE object for the column in the table.</span></span> <span data-ttu-id="2cabc-108">SEQUENCE オブジェクトは IDENTITY 列として、新しい IDENTITY 値を取得する NEXT VALUE FOR 構文を使用する列の DEFAULT 値を作成する機能に依存します。</span><span class="sxs-lookup"><span data-stu-id="2cabc-108">SEQUENCE objects as identity columns rely on the ability to create DEFAULT values for columns that use the NEXT VALUE FOR syntax to get a new identity value.</span></span> <span data-ttu-id="2cabc-109">インメモリ OLTP では DEFAULT がサポートされていないため、新しく生成される SEQUENCE 値を INSERT 構文または挿入しないネイティブ コンパイル ストアド プロシージャに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cabc-109">Since DEFAULTs are not supported in In-Memory OLTP, you need to pass the newly-generated SEQUENCE value either to the INSERT statement or to a natively compiled stored procedure that does the insert.</span></span> <span data-ttu-id="2cabc-110">次の例でそのパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="2cabc-110">The following example demonstrates this pattern.</span></span>  
  
```sql  
-- Create a new In-Memory OLTP table to simulate IDENTITY insert  
-- Here the column C1 was the identity column in the original table  
--  
create table T1  
(  
  
[c1] integer not null primary key T1_c1 nonclustered,  
[c2] varchar(32) not null,  
[c3] datetime not null  
  
) with (memory_optimized = on)  
go  
  
-- This is a sequence provider that will give us values for column [c1]  
--  
create sequence usq_SequenceForT1 as integer start with 2 increment by 1  
go  
  
--   insert a sample row using the sequence  
--   note that a new value needs to be retrieved form   
--   the sequence object for every insert  
--  
declare @c1 integer = next value for [dbo].[usq_SequenceForT1]  
insert into T1 values (@c1, 'test', getdate())  
```  
  
 <span data-ttu-id="2cabc-111">挿入を複数回実行した後、単調に増加する有効な値が列 [c1] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2cabc-111">After performing the insert several times, you see valid monotonically increasing values in column [c1].</span></span> <span data-ttu-id="2cabc-112">この結果セットは、`ORDER BY` を含まないテーブル スキャンとハッシュ インデックスを使用して生成されるため、行は順序付けされません。</span><span class="sxs-lookup"><span data-stu-id="2cabc-112">This result set is generated using table scan and hash index without `ORDER BY` so the rows are not ordered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cabc-113">参照</span><span class="sxs-lookup"><span data-stu-id="2cabc-113">See Also</span></span>  
 [<span data-ttu-id="2cabc-114">インメモリ OLTP への移行</span><span class="sxs-lookup"><span data-stu-id="2cabc-114">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
