---
title: DML トリガーの削除または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, disabling
- removing DML triggers
- disabling DML triggers
- dropping DML triggers
- deleting DML triggers
- DML triggers, removing
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 39b345ade1258987df06938791ac0024e8612365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644896"
---
# <a name="delete-or-disable-dml-triggers"></a><span data-ttu-id="ae88a-102">DML トリガーの削除または無効化</span><span class="sxs-lookup"><span data-stu-id="ae88a-102">Delete or Disable DML Triggers</span></span>
  <span data-ttu-id="ae88a-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、DML トリガーを削除または無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-103">This topic describes how to delete or disable a DML trigger in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ae88a-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="ae88a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ae88a-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ae88a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ae88a-106">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="ae88a-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ae88a-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ae88a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ae88a-108">**DML トリガーを削除または無効にするために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="ae88a-108">**To delete or disable a DML trigger, using:**</span></span>  
  
     [<span data-ttu-id="ae88a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ae88a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ae88a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ae88a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ae88a-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="ae88a-111">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ae88a-112">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ae88a-112">Recommendations</span></span>  
  
-   <span data-ttu-id="ae88a-113">トリガーを削除すると、現在のデータベースから削除されます。</span><span class="sxs-lookup"><span data-stu-id="ae88a-113">When a trigger is deleted, it is dropped from the current database.</span></span> <span data-ttu-id="ae88a-114">トリガーの基になっているテーブルとデータは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="ae88a-114">The table and the data upon which it is based are not affected.</span></span> <span data-ttu-id="ae88a-115">テーブルを削除すると、そのテーブルについて設定されたトリガーはすべて自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="ae88a-115">Deleting a table automatically deletes any triggers on the table.</span></span>  
  
-   <span data-ttu-id="ae88a-116">トリガーは、作成時に既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="ae88a-116">A trigger is enabled by default when it is created.</span></span>  
  
-   <span data-ttu-id="ae88a-117">トリガーを無効にしてもトリガーは削除されず、</span><span class="sxs-lookup"><span data-stu-id="ae88a-117">Disabling a trigger does not drop it.</span></span> <span data-ttu-id="ae88a-118">オブジェクトとして現在のデータベースに残りますが、</span><span class="sxs-lookup"><span data-stu-id="ae88a-118">The trigger still exists as an object in the current database.</span></span> <span data-ttu-id="ae88a-119">ただし、トリガーを起動するようにプログラミングされている INSERT、UPDATE、DELETE のいずれかのステートメントを実行してもトリガーは起動されません。</span><span class="sxs-lookup"><span data-stu-id="ae88a-119">However, the trigger will not fire when any INSERT, UPDATE, or DELETE statement on which it was programmed is executed.</span></span> <span data-ttu-id="ae88a-120">無効になったトリガーは、再度有効にできます。</span><span class="sxs-lookup"><span data-stu-id="ae88a-120">Triggers that are disabled can be reenabled.</span></span> <span data-ttu-id="ae88a-121">トリガーを有効化しても、トリガーが再作成されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ae88a-121">Enabling a trigger does not re-create it.</span></span> <span data-ttu-id="ae88a-122">トリガーは、最初に作成したときと同じ動作で起動されます。</span><span class="sxs-lookup"><span data-stu-id="ae88a-122">The trigger fires in the same manner as when it was originally created.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ae88a-123">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ae88a-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ae88a-124">Permissions</span><span class="sxs-lookup"><span data-stu-id="ae88a-124">Permissions</span></span>  
 <span data-ttu-id="ae88a-125">DML トリガーを削除するには、そのトリガーが定義されているテーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ae88a-125">To delete a DML trigger requires ALTER permission on the table or view on which the trigger is defined.</span></span>  
  
 <span data-ttu-id="ae88a-126">DML トリガーを無効または有効にするには、少なくともトリガーが作成されたテーブルまたはビューに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ae88a-126">To disable or enable a DML trigger, at a minimum, a user must have ALTER permission on the table or view on which the trigger was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ae88a-127">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ae88a-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-dml-trigger"></a><span data-ttu-id="ae88a-128">DML トリガーを削除するには</span><span class="sxs-lookup"><span data-stu-id="ae88a-128">To delete a DML trigger</span></span>  
  
1.  <span data-ttu-id="ae88a-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ae88a-130">目的のデータベースを展開し、 **[テーブル]** を展開します。次に、削除するトリガーが格納されているテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-130">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to delete.</span></span>  
  
3.  <span data-ttu-id="ae88a-131">**[トリガー]** を展開し、削除するトリガーを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae88a-131">Expand **Triggers**, right-click the trigger to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="ae88a-132">**[オブジェクトの削除]** ダイアログ ボックスで、削除対象のトリガーを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae88a-132">In the **Delete Object** dialog box, verify the trigger to delete, and then click **OK**.</span></span>  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a><span data-ttu-id="ae88a-133">DML トリガーを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="ae88a-133">To disable and enable a DML trigger</span></span>  
  
1.  <span data-ttu-id="ae88a-134">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ae88a-135">目的のデータベースを展開し、 **[テーブル]** を展開します。次に、無効にするトリガーが格納されているテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-135">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to disable.</span></span>  
  
3.  <span data-ttu-id="ae88a-136">**[トリガー]** を展開し、無効にするトリガーを右クリックして、 **[無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae88a-136">Expand **Triggers**, right-click the trigger to disable, and then click **Disable**.</span></span>  
  
4.  <span data-ttu-id="ae88a-137">トリガーを有効にするには、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae88a-137">To enable the trigger, click **Enable**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ae88a-138">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ae88a-138">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-dml-trigger"></a><span data-ttu-id="ae88a-139">DML トリガーを削除するには</span><span class="sxs-lookup"><span data-stu-id="ae88a-139">To delete a DML trigger</span></span>  
  
1.  <span data-ttu-id="ae88a-140">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-140">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ae88a-141">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae88a-141">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ae88a-142">次の例をコピーし、クエリ ウィンドウに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="ae88a-142">Copy and paste the following examples into the query window.</span></span> <span data-ttu-id="ae88a-143">[トリガーを作成するには、](/sql/t-sql/statements/create-trigger-transact-sql) CREATE TRIGGER `Sales.bonus_reminder` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-143">Execute the [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) statement to create the `Sales.bonus_reminder` trigger.</span></span> <span data-ttu-id="ae88a-144">トリガーを削除するには、 [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-144">To delete the trigger, execute the [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) statement.</span></span>  
  
```sql  
--Create the trigger.  
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
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a><span data-ttu-id="ae88a-145">DML トリガーを有効または無効にするには</span><span class="sxs-lookup"><span data-stu-id="ae88a-145">To disable and enable a DML trigger</span></span>  
  
1.  <span data-ttu-id="ae88a-146">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-146">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ae88a-147">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae88a-147">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ae88a-148">次の例をコピーし、クエリ ウィンドウに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="ae88a-148">Copy and paste the following examples into the query window.</span></span> <span data-ttu-id="ae88a-149">[トリガーを作成するには、](/sql/t-sql/statements/create-trigger-transact-sql) CREATE TRIGGER `Sales.bonus_reminder` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-149">Execute the [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) statement to create the `Sales.bonus_reminder` trigger.</span></span> <span data-ttu-id="ae88a-150">トリガーを無効または有効にするには、それぞれ、 [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) ステートメントおよび [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="ae88a-150">To disable and enable the trigger, execute the [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) and [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) statements, respectively.</span></span>  
  
```sql  
--Create the trigger.  
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
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```sql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae88a-151">参照</span><span class="sxs-lookup"><span data-stu-id="ae88a-151">See Also</span></span>  
 <span data-ttu-id="ae88a-152">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-152">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-158">[DML トリガーに関する情報の取得](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="ae88a-158">[Get Information About DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="ae88a-159">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-159">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-160">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-160">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-161">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-161">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-162">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-162">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-163">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-163">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-164">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-164">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-165">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-165">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-166">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-166">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="ae88a-167">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ae88a-167">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 [<span data-ttu-id="ae88a-168">sys.server_assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ae88a-168">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
