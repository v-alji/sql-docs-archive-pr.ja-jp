---
title: 複数行のデータを処理するための DML トリガーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple row DML triggers
- UPDATE statement [SQL Server], DML triggers
- DELETE statement [SQL Server], DML triggers
- multirow DML triggers [SQL Server]
- INSERT statement [SQL Server], DML triggers
- DML triggers, multirow
ms.assetid: d476c124-596b-4b27-a883-812b6b50a735
author: rothja
ms.author: jroth
ms.openlocfilehash: 11ea7aa457a5cdfcafd4a8c4e0ac170ae0e3b9c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644904"
---
# <a name="create-dml-triggers-to-handle-multiple-rows-of-data"></a><span data-ttu-id="438d1-102">複数行のデータを処理するための DML トリガーの作成</span><span class="sxs-lookup"><span data-stu-id="438d1-102">Create DML Triggers to Handle Multiple Rows of Data</span></span>
  <span data-ttu-id="438d1-103">DML トリガーのコードを記述するときは、トリガーを起動するステートメントが、1 行だけではなく複数行のデータに影響する場合があることを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="438d1-103">When you write the code for a DML trigger, consider that the statement that causes the trigger to fire can be a single statement that affects multiple rows of data, instead of a single row.</span></span> <span data-ttu-id="438d1-104">この動作は UPDATE トリガーや DELETE トリガーの場合によく見られます。UPDATE ステートメントや DELETE ステートメントが複数行に影響を与えることが多いためです。</span><span class="sxs-lookup"><span data-stu-id="438d1-104">This behavior is common for UPDATE and DELETE triggers because these statements frequently affect multiple rows.</span></span> <span data-ttu-id="438d1-105">INSERT トリガーの場合は、INSERT ステートメントが 1 行単位で追加を行うため、この動作はあまり見られません。</span><span class="sxs-lookup"><span data-stu-id="438d1-105">The behavior is less common for INSERT triggers because the basic INSERT statement adds only a single row.</span></span> <span data-ttu-id="438d1-106">ただし、INSERT トリガーは INSERT INTO (*table_name*) SELECT ステートメントにより起動されることもあります。その場合は、1 回のトリガーの呼び出しで複数行が挿入される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="438d1-106">However, because an INSERT trigger can be fired by an INSERT INTO (*table_name*) SELECT statement, the insertion of many rows may cause a single trigger invocation.</span></span>  
  
 <span data-ttu-id="438d1-107">複数行への影響について考慮することは、DML トリガーの機能によって 1 つのテーブルから自動的に集計値が再計算され、その結果を他のテーブルに保存して集計を続行するような場合は、特に重要です。</span><span class="sxs-lookup"><span data-stu-id="438d1-107">Multirow considerations are especially important when the function of a DML trigger is to automatically recalculate summary values from one table and store the results in another for ongoing tallies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="438d1-108">パフォーマンスが低下する可能性があるので、トリガーにカーソルを使用することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="438d1-108">We do not recommend using cursors in triggers because they could potentially reduce performance.</span></span> <span data-ttu-id="438d1-109">複数行に影響を与えるトリガーを設計する場合は、カーソルではなく行セットをベースにしたロジックを使用してください。</span><span class="sxs-lookup"><span data-stu-id="438d1-109">To design a trigger that affects multiple rows, use rowset-based logic instead of cursors.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="438d1-110">例</span><span class="sxs-lookup"><span data-stu-id="438d1-110">Examples</span></span>  
 <span data-ttu-id="438d1-111">次の例の DML トリガーはどれも、ある列の集計の途中経過を [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの別のテーブル内に保存するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="438d1-111">The DML triggers in the following examples are designed to store a running total of a column in another table of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
### <a name="a-storing-a-running-total-for-a-single-row-insert"></a><span data-ttu-id="438d1-112">A.</span><span class="sxs-lookup"><span data-stu-id="438d1-112">A.</span></span> <span data-ttu-id="438d1-113">単一の行を挿入する場合の集計途中経過の格納</span><span class="sxs-lookup"><span data-stu-id="438d1-113">Storing a running total for a single-row insert</span></span>  
 <span data-ttu-id="438d1-114">最初の例の DML トリガーは、 `PurchaseOrderDetail` テーブルに 1 行のデータが追加される場合、つまり 1 行単位の挿入は問題なく実行できます。</span><span class="sxs-lookup"><span data-stu-id="438d1-114">The first version of the DML trigger works well for a single-row insert when a row of data is loaded into the `PurchaseOrderDetail` table.</span></span> <span data-ttu-id="438d1-115">INSERT ステートメントにより DML トリガーが起動され、トリガーの実行中に **inserted** テーブルに新しい行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="438d1-115">An INSERT statement fires the DML trigger, and the new row is loaded into the **inserted** table for the duration of the trigger execution.</span></span> <span data-ttu-id="438d1-116">`UPDATE` ステートメントでは行の `LineTotal` 列の値が読み取られ、その値が `SubTotal` テーブルの `PurchaseOrderHeader` 列の既存の値に加算されます。</span><span class="sxs-lookup"><span data-stu-id="438d1-116">The `UPDATE` statement reads the `LineTotal` column value for the row and adds that value to the existing value in the `SubTotal` column in the `PurchaseOrderHeader` table.</span></span> <span data-ttu-id="438d1-117">`WHERE` 句により、 `PurchaseOrderDetail` テーブルで更新された行が `PurchaseOrderID` inserted **テーブルの行の** に一致することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="438d1-117">The `WHERE` clause makes sure that the updated row in the `PurchaseOrderDetail` table matches the `PurchaseOrderID` of the row in the **inserted** table.</span></span>  
  
```  
-- Trigger is valid for single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID ;  
```  
  
### <a name="b-storing-a-running-total-for-a-multirow-or-single-row-insert"></a><span data-ttu-id="438d1-118">B.</span><span class="sxs-lookup"><span data-stu-id="438d1-118">B.</span></span> <span data-ttu-id="438d1-119">複数または単一の行を挿入する場合の集計途中経過の格納</span><span class="sxs-lookup"><span data-stu-id="438d1-119">Storing a running total for a multirow or single-row insert</span></span>  
 <span data-ttu-id="438d1-120">複数行を挿入する場合は、例 A で示した DML トリガーは正しく実行されない可能性があります。UPDATE ステートメントの代入式の右側の式 (`SubTotal` + `LineTotal`) は必ず単一の値になり、値のリストを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="438d1-120">For a multirow insert, the DML trigger in example A might not operate correctly; the expression to the right of an assignment expression in an UPDATE statement (`SubTotal` + `LineTotal`) can be only a single value, not a list of values.</span></span> <span data-ttu-id="438d1-121">したがって、このトリガーの結果は、 **inserted** テーブル内の 1 行から値を取得して、その値を、特定の `SubTotal` 値に対する `PurchaseOrderHeader` テーブルの既存の `PurchaseOrderID` 値に追加することになります。</span><span class="sxs-lookup"><span data-stu-id="438d1-121">Therefore, the effect of the trigger is to retrieve a value from any single row in the **inserted** table and add that value to the existing `SubTotal` value in the `PurchaseOrderHeader` table for a specific `PurchaseOrderID` value.</span></span> <span data-ttu-id="438d1-122">この操作では、1 つの `PurchaseOrderID` が **inserted** テーブルに複数登録されている場合には、予想どおりの結果が得られないことがあります。</span><span class="sxs-lookup"><span data-stu-id="438d1-122">This operation might not have the expected effect if a single `PurchaseOrderID` value occurred more than one time in the **inserted** table.</span></span>  
  
 <span data-ttu-id="438d1-123">`PurchaseOrderHeader` テーブルを正しく更新するには、 **inserted** テーブルに複数の行がある場合を考慮してトリガーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="438d1-123">To correctly update the `PurchaseOrderHeader` table, the trigger must allow for the chance of multiple rows in the **inserted** table.</span></span> <span data-ttu-id="438d1-124">これを行うには、 `SUM` ごとに `LineTotal` inserted **テーブル内の行グループで** の合計を計算する `PurchaseOrderID`関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="438d1-124">You can do this by using the `SUM` function that calculates the total `LineTotal` for a group of rows in the **inserted** table for each `PurchaseOrderID`.</span></span> <span data-ttu-id="438d1-125">`SUM` 関数は、相関サブクエリ (かっこ内の `SELECT` ステートメント) に指定します。</span><span class="sxs-lookup"><span data-stu-id="438d1-125">The `SUM` function is included in a correlated subquery (the `SELECT` statement in parentheses).</span></span> <span data-ttu-id="438d1-126">このサブクエリは、 `PurchaseOrderID` テーブルの **に一致するか、これと相関関係にある** inserted `PurchaseOrderID` テーブルの `PurchaseOrderHeader` の各値を返します。</span><span class="sxs-lookup"><span data-stu-id="438d1-126">This subquery returns a single value for each `PurchaseOrderID` in the **inserted** table that matches or is correlated with a `PurchaseOrderID` in the `PurchaseOrderHeader` table.</span></span>  
  
```  
-- Trigger is valid for multirow and single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail2  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted);  
```  
  
 <span data-ttu-id="438d1-127">このトリガーは 1 行だけの挿入でも正しく実行されます。この場合、 `LineTotal` 値の列の合計は、1 つの行だけの値になります。</span><span class="sxs-lookup"><span data-stu-id="438d1-127">This trigger also works correctly in a single-row insert; the sum of the `LineTotal` value column is the sum of a single row.</span></span> <span data-ttu-id="438d1-128">ただし、このトリガーでは、相関サブクエリと `IN` 句で使用されている `WHERE` 演算子のために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]による追加の処理を必要とします。</span><span class="sxs-lookup"><span data-stu-id="438d1-128">However, with this trigger the correlated subquery and the `IN` operator that is used in the `WHERE` clause require additional processing from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="438d1-129">これは、1 行単位の挿入操作の場合は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="438d1-129">This is unnecessary for a single-row insert.</span></span>  
  
### <a name="c-storing-a-running-total-based-on-the-type-of-insert"></a><span data-ttu-id="438d1-130">C.</span><span class="sxs-lookup"><span data-stu-id="438d1-130">C.</span></span> <span data-ttu-id="438d1-131">挿入の種類に基づいた集計の途中経過の格納</span><span class="sxs-lookup"><span data-stu-id="438d1-131">Storing a running total based on the type of insert</span></span>  
 <span data-ttu-id="438d1-132">処理対象の行数に応じて最適の方法を使用するようにトリガーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="438d1-132">You can change the trigger to use the method optimal for the number of rows.</span></span> <span data-ttu-id="438d1-133">たとえば、1 行だけの挿入と複数行の挿入を区別するには、トリガーのロジックで `@@ROWCOUNT` 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="438d1-133">For example, the `@@ROWCOUNT` function can be used in the logic of the trigger to distinguish between a single and a multirow insert.</span></span>  
  
```  
-- Trigger valid for multirow and single row inserts  
-- and optimal for single row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail3  
ON Purchasing.PurchaseOrderDetail  
FOR INSERT AS  
IF @@ROWCOUNT = 1  
BEGIN  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
END  
ELSE  
BEGIN  
      UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted)  
END;  
```  
  
## <a name="see-also"></a><span data-ttu-id="438d1-134">参照</span><span class="sxs-lookup"><span data-stu-id="438d1-134">See Also</span></span>  
 [<span data-ttu-id="438d1-135">DML トリガー</span><span class="sxs-lookup"><span data-stu-id="438d1-135">DML Triggers</span></span>](dml-triggers.md)  
  
  
