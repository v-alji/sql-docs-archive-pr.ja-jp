---
title: DML トリガーの変更または名前の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- renaming triggers
- modifying triggers
- DML triggers, modifying
ms.assetid: c7317eec-c0e9-479e-a4a7-83b6b6c58d59
author: rothja
ms.author: jroth
ms.openlocfilehash: 65bb13552b552d54b5547eadedc412977e423a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644879"
---
# <a name="modify-or-rename-dml-triggers"></a><span data-ttu-id="40587-102">DML トリガーの変更または名前の変更</span><span class="sxs-lookup"><span data-stu-id="40587-102">Modify or Rename DML Triggers</span></span>
  <span data-ttu-id="40587-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]の DML トリガーを変更したりその名前を変更したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40587-103">This topic describes how to modify or rename a DML trigger in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="40587-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="40587-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="40587-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="40587-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="40587-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="40587-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="40587-107">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="40587-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="40587-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="40587-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="40587-109">**DML トリガーに変更を加えたり名前を変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="40587-109">**To modify or rename a DML trigger, using:**</span></span>  
  
     [<span data-ttu-id="40587-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="40587-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="40587-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="40587-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="40587-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="40587-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="40587-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="40587-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="40587-114">トリガーの名前を変更する場合、トリガーは現在のデータベース内にある必要があり、新しい名前は [識別子](../databases/database-identifiers.md)に関するルールに従っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="40587-114">When you rename a trigger, the trigger must be in the current database, and the new name must follow the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="40587-115">推奨事項</span><span class="sxs-lookup"><span data-stu-id="40587-115">Recommendations</span></span>  
  
-   <span data-ttu-id="40587-116">[sp_rename](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) ストアド プロシージャを使用してトリガーの名前を変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="40587-116">We recommend you do not use the [sp_rename](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) stored procedure to rename a trigger.</span></span> <span data-ttu-id="40587-117">オブジェクト名の一部または全部を変更すると、スクリプトおよびストアド プロシージャが壊れる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="40587-117">Changing any part of an object name can break scripts and stored procedures.</span></span> <span data-ttu-id="40587-118">トリガーの名前を変更しても、 [sys.sql_modules](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) カタログ ビューの definition 列にある、対応するオブジェクトの名前は変更されません。</span><span class="sxs-lookup"><span data-stu-id="40587-118">Renaming a trigger does not change the name of the corresponding object name in the definition column of the [sys.sql_modules](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) catalog view.</span></span> <span data-ttu-id="40587-119">トリガーを削除してから再作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="40587-119">We recommend that you drop and re-create the trigger instead.</span></span>  
  
-   <span data-ttu-id="40587-120">DML トリガーで参照されるオブジェクトの名前を変更する際には、新しい名前を反映するようにトリガーを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40587-120">If you change the name of an object referenced by a DML trigger, you must modify the trigger so that its text reflects the new name.</span></span> <span data-ttu-id="40587-121">したがって、オブジェクトの名前を変更する前に、まずオブジェクトの依存関係を表示して、オブジェクト名の変更により影響を受けるトリガーがあるかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="40587-121">Therefore, before you rename an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.</span></span>  
  
-   <span data-ttu-id="40587-122">DML トリガーは、定義が暗号化されるように変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="40587-122">A DML trigger can also be modified to encrypt its definition.</span></span>  
  
-   <span data-ttu-id="40587-123">トリガーの依存関係を表示するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または次の関数およびカタログ ビューを使用できます。</span><span class="sxs-lookup"><span data-stu-id="40587-123">To view the dependencies of a trigger, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the following function and catalog views:</span></span>  
  
    -   [<span data-ttu-id="40587-124">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40587-124">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
    -   [<span data-ttu-id="40587-125">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40587-125">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
    -   [<span data-ttu-id="40587-126">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40587-126">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="40587-127">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="40587-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="40587-128">Permissions</span><span class="sxs-lookup"><span data-stu-id="40587-128">Permissions</span></span>  
 <span data-ttu-id="40587-129">DML トリガーを変更するには、トリガーが定義されているテーブルやビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="40587-129">To alter a DML trigger requires ALTER permission on the table or view on which the trigger is defined.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="40587-130">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="40587-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-dml-trigger"></a><span data-ttu-id="40587-131">DML トリガーを変更するには</span><span class="sxs-lookup"><span data-stu-id="40587-131">To modify a DML trigger</span></span>  
  
1.  <span data-ttu-id="40587-132">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="40587-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="40587-133">目的のデータベースを展開し、 **[テーブル]** を展開します。次に、変更するトリガーが格納されているテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="40587-133">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to modify.</span></span>  
  
3.  <span data-ttu-id="40587-134">**[トリガー]** を展開します。変更するトリガーを右クリックし、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40587-134">Expand **Triggers**, right-click the trigger to modify, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="40587-135">トリガーを変更し、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40587-135">Modify the trigger, and then click **Execute**.</span></span>  
  
#### <a name="to-rename-a-dml-trigger"></a><span data-ttu-id="40587-136">DML トリガーの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="40587-136">To rename a DML trigger</span></span>  
  
1.  <span data-ttu-id="40587-137">名前を変更する[トリガーを削除](../triggers/dml-triggers.md) します。</span><span class="sxs-lookup"><span data-stu-id="40587-137">[Delete the trigger](../triggers/dml-triggers.md) that you want to rename.</span></span>  
  
2.  <span data-ttu-id="40587-138">新しい名前を指定して、[トリガーを再作成](../triggers/create-dml-triggers.md)します。</span><span class="sxs-lookup"><span data-stu-id="40587-138">[Re-create the trigger](../triggers/create-dml-triggers.md), specifying the new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="40587-139">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="40587-139">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-trigger-using-alter-trigger"></a><span data-ttu-id="40587-140">ALTER TRIGGER を使用してトリガーを変更するには</span><span class="sxs-lookup"><span data-stu-id="40587-140">To modify a trigger using ALTER TRIGGER</span></span>  
  
1.  <span data-ttu-id="40587-141">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="40587-141">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="40587-142">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40587-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="40587-143">次の例をコピーし、クエリに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="40587-143">Copy and paste the following examples into the query.</span></span> <span data-ttu-id="40587-144">1 つ目の例を実行して、ユーザーが `SalesPersonQuotaHistory` テーブルのデータの追加や変更を行おうとしたときにユーザー定義のメッセージを出力する DML トリガーを作成します。</span><span class="sxs-lookup"><span data-stu-id="40587-144">Execute the first example to create a DML trigger that prints a user-defined message to the client when a user tries to add or change data in the `SalesPersonQuotaHistory` table.</span></span> <span data-ttu-id="40587-145">[ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) ステートメントを実行して、 `INSERT` アクティビティのときだけトリガーが発生するように変更します。</span><span class="sxs-lookup"><span data-stu-id="40587-145">Execute the [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) statement to modify the trigger to fire only on `INSERT` activities.</span></span> <span data-ttu-id="40587-146">このトリガーは、テーブルの更新や行の挿入を行うユーザーに対して、 `Compensation` 部門にも変更を知らせる必要があることを連絡できるので有用です。</span><span class="sxs-lookup"><span data-stu-id="40587-146">This trigger is helpful because it reminds the user that updates or inserts rows into this table to also notify the `Compensation` department.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```sql  
USE AdventureWorks2012;  
GO  
ALTER TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
AFTER INSERT  
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
#### <a name="to-rename-a-trigger-using-drop-trigger-and-alter-trigger"></a><span data-ttu-id="40587-147">DROP TRIGGER と ALTER TRIGGER を使用してトリガーの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="40587-147">To rename a trigger using DROP TRIGGER and ALTER TRIGGER</span></span>  
  
1.  <span data-ttu-id="40587-148">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="40587-148">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="40587-149">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40587-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="40587-150">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40587-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="40587-151">この例では、 [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) ステートメントと [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) ステートメントを使用して、 `Sales.bonus_reminder` トリガーの名前を `Sales.bonus_reminder_2`に変更します。</span><span class="sxs-lookup"><span data-stu-id="40587-151">This example use the [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) and [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) statements to rename the `Sales.bonus_reminder` trigger to `Sales.bonus_reminder_2`.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder_2  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="40587-152">参照</span><span class="sxs-lookup"><span data-stu-id="40587-152">See Also</span></span>  
 <span data-ttu-id="40587-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="40587-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="40587-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="40587-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="40587-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="40587-158">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-158">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span></span>  
 <span data-ttu-id="40587-159">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-159">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="40587-160">[DML トリガーに関する情報の取得](../triggers/get-information-about-dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="40587-160">[Get Information About DML Triggers](../triggers/get-information-about-dml-triggers.md) </span></span>  
 <span data-ttu-id="40587-161">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-161">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="40587-162">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-162">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="40587-163">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-163">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="40587-164">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-164">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="40587-165">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-165">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="40587-166">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-166">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="40587-167">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-167">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="40587-168">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-168">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="40587-169">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="40587-169">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 [<span data-ttu-id="40587-170">sys.server_assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="40587-170">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
