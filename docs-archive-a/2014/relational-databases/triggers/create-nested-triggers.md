---
title: 入れ子になったトリガーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- recursive DML triggers [SQL Server]
- DML triggers, nested
- triggers [SQL Server], nested
- direct recursion [SQL Server]
- triggers [SQL Server], recursive
- DML triggers, recursive
- RECURSIVE_TRIGGERS option
- indirect recursion [SQL Server]
- nested DML triggers
ms.assetid: cd522dda-b4ab-41b8-82b0-02445bdba7af
author: rothja
ms.author: jroth
ms.openlocfilehash: c0016fc3cdd93ea78ceed56efa076a01bd85be50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644901"
---
# <a name="create-nested-triggers"></a><span data-ttu-id="19bc7-102">入れ子になったトリガーの作成</span><span class="sxs-lookup"><span data-stu-id="19bc7-102">Create Nested Triggers</span></span>
  <span data-ttu-id="19bc7-103">あるトリガーが別のトリガーを起動する操作を実行するときは、DML トリガーと DDL トリガーの両方が入れ子になります。</span><span class="sxs-lookup"><span data-stu-id="19bc7-103">Both DML and DDL triggers are nested when a trigger performs an action that initiates another trigger.</span></span> <span data-ttu-id="19bc7-104">このような操作では、他のトリガーを順次開始できます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-104">These actions can initiate other triggers, and so on.</span></span> <span data-ttu-id="19bc7-105">DML トリガーと DDL トリガーは、32 レベルまで入れ子にできます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-105">DML and DDL triggers can be nested up to 32 levels.</span></span> <span data-ttu-id="19bc7-106">**nested triggers** サーバー構成オプションにより、AFTER トリガーを入れ子にできるかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-106">You can control whether AFTER triggers can be nested through the **nested triggers** server configuration option.</span></span> <span data-ttu-id="19bc7-107">INSTEAD OF トリガーは、このサーバー オプションの設定とは無関係に入れ子にできます。INSTEAD OF トリガーにできるのは DML トリガーだけです。</span><span class="sxs-lookup"><span data-stu-id="19bc7-107">INSTEAD OF triggers (only DML triggers can be INSTEAD OF triggers) can be nested regardless of this setting.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19bc7-108">[!INCLUDE[tsql](../../includes/tsql-md.md)] トリガーからマネージド コードへの参照は、32 レベルの入れ子制限の 1 レベルとしてカウントされます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-108">Any reference to managed code from a [!INCLUDE[tsql](../../includes/tsql-md.md)] trigger counts as one level against the 32-level nesting limit.</span></span> <span data-ttu-id="19bc7-109">マネージド コード内から呼び出されたメソッドは、この制限としてはカウントされません。</span><span class="sxs-lookup"><span data-stu-id="19bc7-109">Methods invoked from within managed code do not count against this limit.</span></span>  
  
 <span data-ttu-id="19bc7-110">トリガーを入れ子にできる場合に、トリガーのチェーンのどれかが無限ループを開始すると、入れ子階層の上限を超えることになり、トリガーは終了します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-110">If nested triggers are allowed and a trigger in the chain starts an infinite loop, the nesting level is exceeded and the trigger terminates.</span></span>  
  
 <span data-ttu-id="19bc7-111">入れ子になったトリガーを使用して、前のトリガーの影響を受けた行のバックアップ コピーを保存するなど、システムの運用上有益な機能を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-111">You can use nested triggers to perform useful housekeeping functions such as storing a backup copy of rows affected by a previous trigger.</span></span> <span data-ttu-id="19bc7-112">たとえば、 `PurchaseOrderDetail` トリガーが削除した `PurchaseOrderDetail` 行のバックアップ コピーを保存するトリガーを `delcascadetrig` に作成することができます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-112">For example, you can create a trigger on `PurchaseOrderDetail` that saves a backup copy of the `PurchaseOrderDetail` rows that the `delcascadetrig` trigger deleted.</span></span> <span data-ttu-id="19bc7-113">`delcascadetrig` トリガーが有効な場合、 `PurchaseOrderID` から `PurchaseOrderHeader` 1965 が削除されると、 `PurchaseOrderDetail`から対応する行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-113">With the `delcascadetrig` trigger in effect, deleting `PurchaseOrderID` 1965 from `PurchaseOrderHeader` deletes the corresponding row or rows from `PurchaseOrderDetail`.</span></span> <span data-ttu-id="19bc7-114">このデータを保存するには、 `PurchaseOrderDetail` に DELETE トリガーを作成します。このトリガーでは削除されたデータが、別に作成されたテーブル `del_save`に保存されます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-114">To save the data, you can create a DELETE trigger on `PurchaseOrderDetail` that saves the deleted data into another separately created table, `del_save`.</span></span> <span data-ttu-id="19bc7-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-115">For example:</span></span>  
  
```  
CREATE TRIGGER Purchasing.savedel  
   ON Purchasing.PurchaseOrderDetail  
FOR DELETE  
AS  
   INSERT del_save;  
   SELECT * FROM deleted;  
```  
  
 <span data-ttu-id="19bc7-116">入れ子の順序に依存するトリガーを使用することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="19bc7-116">We do not recommend using nested triggers in an order-dependent sequence.</span></span> <span data-ttu-id="19bc7-117">個別のトリガーを使用し、順番にデータ修正を行ってください。</span><span class="sxs-lookup"><span data-stu-id="19bc7-117">Use separate triggers to cascade data modifications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19bc7-118">トリガーはトランザクション内で実行されるので、入れ子になったトリガーのいずれかのレベルで障害が発生すると、トランザクション全体が取り消され、すべてのデータ修正がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-118">Because triggers execute within a transaction, a failure at any level of a set of nested triggers cancels the entire transaction, and all data modifications are rolled back.</span></span> <span data-ttu-id="19bc7-119">どこで障害が発生したかを判断できるように、トリガーに PRINT ステートメントを含めてください。</span><span class="sxs-lookup"><span data-stu-id="19bc7-119">Include PRINT statements in your triggers so that you can determine where the failure has occurred.</span></span>  
  
## <a name="recursive-triggers"></a><span data-ttu-id="19bc7-120">再帰トリガー</span><span class="sxs-lookup"><span data-stu-id="19bc7-120">Recursive Triggers</span></span>  
 <span data-ttu-id="19bc7-121">RECURSIVE_TRIGGERS データベース オプションが ON になっている場合を除いて、AFTER トリガーが自分自身を再帰呼び出しすることはありません。</span><span class="sxs-lookup"><span data-stu-id="19bc7-121">An AFTER trigger does not call itself recursively unless the RECURSIVE_TRIGGERS database option is set.</span></span>  
  
 <span data-ttu-id="19bc7-122">再帰には、次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="19bc7-122">There are two types of recursion:</span></span>  
  
-   <span data-ttu-id="19bc7-123">直接再帰</span><span class="sxs-lookup"><span data-stu-id="19bc7-123">Direct recursion</span></span>  
  
     <span data-ttu-id="19bc7-124">起動されたトリガーによる処理が、同じトリガーを再び起動する場合にこの再帰が発生します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-124">This recursion occurs when a trigger fires and performs an action that causes the same trigger to fire again.</span></span> <span data-ttu-id="19bc7-125">たとえば、アプリケーションで **T3**テーブルが更新され、これにより **Trig3** トリガーが起動されたとします。</span><span class="sxs-lookup"><span data-stu-id="19bc7-125">For example, an application updates table **T3**; this causes trigger **Trig3** to fire.</span></span> <span data-ttu-id="19bc7-126">**Trig3** がテーブル **T3** を更新するトリガーだとすると、テーブルが再度更新され、 **Trig3** が再び起動されることになります。</span><span class="sxs-lookup"><span data-stu-id="19bc7-126">**Trig3** updates table **T3** again; this causes trigger **Trig3** to fire again.</span></span>  
  
     <span data-ttu-id="19bc7-127">別の種類 (AFTER または INSTEAD OF) のトリガーが呼び出された後で、同じトリガーが呼び出されても、直接再帰が発生します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-127">Direct recursion can also occur when the same trigger is called again, but after a trigger of a different type (AFTER or INSTEAD OF) is called.</span></span> <span data-ttu-id="19bc7-128">つまり、同じ INSTEAD OF トリガーが 2 回呼び出されると、その間に AFTER トリガーが 1 回以上呼び出されていたとしても、INSTEAD OF トリガーの直接再帰が発生します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-128">In other words, direct recursion of an INSTEAD OF trigger can occur when the same INSTEAD OF trigger is called for a second time, even if one or more AFTER triggers are called in between.</span></span> <span data-ttu-id="19bc7-129">同様に、同じ AFTER トリガーが 2 回呼び出されると、その間に INSTEAD OF トリガーが 1 回以上呼び出されていたとしても、AFTER トリガーの直接再帰が発生します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-129">Likewise, direct recursion of an AFTER trigger can occur when the same AFTER trigger is called for a second time, even if one or more INSTEAD OF triggers are called in between.</span></span> <span data-ttu-id="19bc7-130">たとえば、アプリケーションがテーブル **T4**を更新します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-130">For example, an application updates table **T4**.</span></span> <span data-ttu-id="19bc7-131">この更新により、INSTEAD OF トリガー **Trig4** が起動します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-131">This update causes INSTEAD OF trigger **Trig4** to fire.</span></span> <span data-ttu-id="19bc7-132">**Trig4** はテーブル **T5**を更新します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-132">**Trig4** updates table **T5**.</span></span> <span data-ttu-id="19bc7-133">この更新により、AFTER トリガー **Trig5** が起動します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-133">This update causes AFTER trigger **Trig5** to fire.</span></span> <span data-ttu-id="19bc7-134">**Trig5** がテーブル **T4**を更新し、これにより INSTEAD OF トリガー **Trig4** が再び起動されます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-134">**Trig5** updates table **T4**, and this update causes INSTEAD OF trigger **Trig4** to fire again.</span></span> <span data-ttu-id="19bc7-135">このようなイベントの連鎖は、 **Trig4**に対する直接再帰と見なされます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-135">This chain of events is considered direct recursion for **Trig4**.</span></span>  
  
-   <span data-ttu-id="19bc7-136">間接再帰</span><span class="sxs-lookup"><span data-stu-id="19bc7-136">Indirect recursion</span></span>  
  
     <span data-ttu-id="19bc7-137">起動されたトリガーが実行した処理によって、同じ種類 (AFTER または INSTEAD OF) の別のトリガーが起動する場合、この再帰が発生します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-137">This recursion occurs when a trigger fires and performs an action that causes another trigger of the same type (AFTER or INSTEAD OF) to fire.</span></span> <span data-ttu-id="19bc7-138">この 2 番目のトリガーにより、最初のトリガーを再度起動する操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-138">This second trigger performs an action that causes the original trigger to fire again.</span></span> <span data-ttu-id="19bc7-139">つまり、ある INSTEAD OF トリガーが 2 回呼び出され、その間に別の INSTEAD OF トリガーが呼び出されていると、間接再帰が発生します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-139">In other words, indirect recursion can occur when an INSTEAD OF trigger is called for a second time, but not until another INSTEAD OF trigger is called in between.</span></span> <span data-ttu-id="19bc7-140">同様に、ある AFTER トリガーが 2 回呼び出され、その間に別の AFTER トリガーが呼び出されていると、間接再帰が発生します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-140">Likewise, indirect recursion can occur when an AFTER trigger is called for a second time, but not until another AFTER trigger is called in between.</span></span> <span data-ttu-id="19bc7-141">たとえば、アプリケーションがテーブル **T1**を更新します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-141">For example, an application updates table **T1**.</span></span> <span data-ttu-id="19bc7-142">この更新により、AFTER トリガー **Trig1** が起動します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-142">This update causes AFTER trigger **Trig1** to fire.</span></span> <span data-ttu-id="19bc7-143">**Trig1** がテーブル **T2**を更新し、これにより AFTER トリガー **Trig2** が起動します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-143">**Trig1** updates table **T2**, and this update causes AFTER trigger **Trig2** to fire.</span></span> <span data-ttu-id="19bc7-144">次に、**Trig2** がテーブル **T1** を更新し、これにより AFTER トリガー **Trig1** が再び起動します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-144">**Trig2** in turn updates table **T1** that causes AFTER trigger **Trig1** to fire again.</span></span>  
  
 <span data-ttu-id="19bc7-145">RECURSIVE_TRIGGERS データベース オプションが OFF の場合は、AFTER トリガーの直接再帰呼び出しのみが回避されます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-145">Only direct recursion of AFTER triggers is prevented when the RECURSIVE_TRIGGERS database option is set to OFF.</span></span> <span data-ttu-id="19bc7-146">AFTER トリガーの間接再帰を無効にするには、 **nested triggers** サーバー オプションを **0**に設定します。</span><span class="sxs-lookup"><span data-stu-id="19bc7-146">To disable indirect recursion of AFTER triggers, also set the **nested triggers** server option to **0**.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="19bc7-147">例</span><span class="sxs-lookup"><span data-stu-id="19bc7-147">Examples</span></span>  
 <span data-ttu-id="19bc7-148">次の例では、再帰トリガーを使用して、自己参照型リレーションシップ (トランジティブ クロージャとも呼ばれます) を解決する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="19bc7-148">The following example shows using recursive triggers to solve a self-referencing relationship (also known as transitive closure).</span></span> <span data-ttu-id="19bc7-149">たとえば、 `emp_mgr` テーブルで、次のものが定義されているとします。</span><span class="sxs-lookup"><span data-stu-id="19bc7-149">For example, the table `emp_mgr` defines the following:</span></span>  
  
-   <span data-ttu-id="19bc7-150">会社内の従業員 (`emp`)</span><span class="sxs-lookup"><span data-stu-id="19bc7-150">An employee (`emp`) in a company.</span></span>  
  
-   <span data-ttu-id="19bc7-151">各従業員の管理者 (`mgr`)</span><span class="sxs-lookup"><span data-stu-id="19bc7-151">The manager for each employee (`mgr`).</span></span>  
  
-   <span data-ttu-id="19bc7-152">各従業員へ報告を行う、組織構成内の従業員の総数 (`NoOfReports`)</span><span class="sxs-lookup"><span data-stu-id="19bc7-152">The total number of employees in the organizational tree reporting to each employee (`NoOfReports`).</span></span>  
  
 <span data-ttu-id="19bc7-153">再帰的な UPDATE トリガーを使用すると、新しい従業員のレコードが挿入されたときに `NoOfReports` 列を最新の状態に更新できます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-153">A recursive UPDATE trigger can be used to keep the `NoOfReports` column up-to-date as new employee records are inserted.</span></span> <span data-ttu-id="19bc7-154">INSERT トリガーにより、その従業員の管理者のレコードの `NoOfReports` 列の値が更新されます。これにより組織構成の上部に向かって、その他のレコードの `NoOfReports` 列が再帰的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="19bc7-154">The INSERT trigger updates the `NoOfReports` column of the manager record, which recursively updates the `NoOfReports` column of other records up the management hierarchy.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
-- Turn recursive triggers ON in the database.  
ALTER DATABASE AdventureWorks2012  
   SET RECURSIVE_TRIGGERS ON;  
GO  
CREATE TABLE dbo.emp_mgr (  
   emp char(30) PRIMARY KEY,  
    mgr char(30) NULL FOREIGN KEY REFERENCES emp_mgr(emp),  
    NoOfReports int DEFAULT 0  
);  
GO  
CREATE TRIGGER dbo.emp_mgrins ON dbo.emp_mgr  
FOR INSERT  
AS  
DECLARE @e char(30), @m char(30);  
DECLARE c1 CURSOR FOR  
   SELECT emp_mgr.emp  
   FROM   emp_mgr, inserted  
   WHERE emp_mgr.emp = inserted.mgr;  
  
OPEN c1;  
FETCH NEXT FROM c1 INTO @e;  
WHILE @@fetch_status = 0  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Add 1 for newly  
   WHERE emp_mgr.emp = @e ;                           -- added employee.  
  
   FETCH NEXT FROM c1 INTO @e;  
END  
CLOSE c1;  
DEALLOCATE c1;  
GO  
-- This recursive UPDATE trigger works assuming:  
--   1. Only singleton updates on emp_mgr.  
--   2. No inserts in the middle of the org tree.  
CREATE TRIGGER dbo.emp_mgrupd ON dbo.emp_mgr FOR UPDATE  
AS  
IF UPDATE (mgr)  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Increment mgr's  
   FROM inserted                            -- (no. of reports) by  
   WHERE emp_mgr.emp = inserted.mgr;         -- 1 for the new report.  
  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports - 1 -- Decrement mgr's  
   FROM deleted                             -- (no. of reports) by 1  
   WHERE emp_mgr.emp = deleted.mgr;          -- for the new report.  
END  
GO  
-- Insert some test data rows.  
INSERT dbo.emp_mgr(emp, mgr) VALUES  
    ('Harry', NULL)  
    ,('Alice', 'Harry')  
    ,('Paul', 'Alice')  
    ,('Joe', 'Alice')  
    ,('Dave', 'Joe');  
GO  
SELECT emp,mgr,NoOfReports  
FROM dbo.emp_mgr;  
GO  
-- Change Dave's manager from Joe to Harry  
UPDATE dbo.emp_mgr SET mgr = 'Harry'  
WHERE emp = 'Dave';  
GO  
SELECT emp,mgr,NoOfReports FROM emp_mgr;  
  
GO  
```  
  
 <span data-ttu-id="19bc7-155">以下は、更新を行う前の状態です。</span><span class="sxs-lookup"><span data-stu-id="19bc7-155">Here are the results before the update.</span></span>  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Joe                            0  
Harry                          NULL                           1  
Joe                            Alice                          1  
Paul                           Alice                          0  
```  
  
 <span data-ttu-id="19bc7-156">以下は、更新を行った後の状態です。</span><span class="sxs-lookup"><span data-stu-id="19bc7-156">Here are the results after the update.</span></span>  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Harry                          0  
Harry                          NULL                           2  
Joe                            Alice                          0  
Paul                           Alice                          0  
```  
  
 <span data-ttu-id="19bc7-157">**入れ子になったトリガーのオプションを設定するには**</span><span class="sxs-lookup"><span data-stu-id="19bc7-157">**To set the nested triggers option**</span></span>  
  
-   [<span data-ttu-id="19bc7-158">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="19bc7-158">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 <span data-ttu-id="19bc7-159">**RECURSIVE_TRIGGERS データベース オプションを設定するには**</span><span class="sxs-lookup"><span data-stu-id="19bc7-159">**To set the RECURSIVE_TRIGGERS database option**</span></span>  
  
-   [<span data-ttu-id="19bc7-160">ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="19bc7-160">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a><span data-ttu-id="19bc7-161">参照</span><span class="sxs-lookup"><span data-stu-id="19bc7-161">See Also</span></span>  
 <span data-ttu-id="19bc7-162">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="19bc7-162">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 [<span data-ttu-id="19bc7-163">nested triggers サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="19bc7-163">Configure the nested triggers Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md)  
  
  
