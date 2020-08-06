---
title: DML トリガーに関する情報の取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- viewing DML triggers
- DML triggers, metadata
- displaying DML triggers
- status information [SQL Server], triggers
- DML triggers, viewing
ms.assetid: 37574aac-181d-4aca-a2cc-8abff64237dc
author: rothja
ms.author: jroth
ms.openlocfilehash: 2f65976d2f517137e23bd9e5e1c98cc76324bc49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644892"
---
# <a name="get-information-about-dml-triggers"></a><span data-ttu-id="3560a-102">DML トリガーに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="3560a-102">Get Information About DML Triggers</span></span>
  <span data-ttu-id="3560a-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して DML トリガーに関する情報を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3560a-103">This topic describes how to get information about DML triggers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3560a-104">この情報には、テーブルに設定されたトリガーの種類、名前、所有者、および作成日または変更日を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3560a-104">This information can include the types of triggers on a table, the name of a trigger, its owner and the date it was created or modified.</span></span> <span data-ttu-id="3560a-105">トリガーが作成時に暗号化されていない場合は、トリガーの定義を取得します。</span><span class="sxs-lookup"><span data-stu-id="3560a-105">If the trigger was not encrypted when it was created, you obtain the definition of the trigger.</span></span> <span data-ttu-id="3560a-106">定義は、トリガーを定義しているテーブルに対してそのトリガーがどのように作用するかを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3560a-106">You can use the definition to help you understand how a trigger affects the table up on which it is defined.</span></span> <span data-ttu-id="3560a-107">また、特定のトリガーが使用しているオブジェクトを見つけることもできます。</span><span class="sxs-lookup"><span data-stu-id="3560a-107">Also, you can find out the objects that a specific trigger uses.</span></span> <span data-ttu-id="3560a-108">この情報を使用すると、データベースで変更または削除された場合にトリガーに影響を及ぼすオブジェクトを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3560a-108">With this information, you can identify the objects that affect the trigger if they are changed or deleted in the database.</span></span>  
  
 <span data-ttu-id="3560a-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="3560a-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3560a-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="3560a-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3560a-111">Security</span><span class="sxs-lookup"><span data-stu-id="3560a-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3560a-112">**DML トリガーに関する情報を取得するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="3560a-112">**To get information about DML triggers, using:**</span></span>  
  
     [<span data-ttu-id="3560a-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3560a-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3560a-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3560a-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3560a-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="3560a-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3560a-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3560a-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3560a-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="3560a-117">Permissions</span></span>  
 <span data-ttu-id="3560a-118">**sys.sql.modules**、 **sys.object**、 **sys.triggers**、 **sys.events**、 **sys.trigger_events**</span><span class="sxs-lookup"><span data-stu-id="3560a-118">**sys.sql.modules**, **sys.object**, **sys.triggers**, **sys.events**, **sys.trigger_events**</span></span>  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] <span data-ttu-id="3560a-119">詳細については、「 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3560a-119">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
 <span data-ttu-id="3560a-120">OBJECT_DEFINITION、OBJECTPROPERTY、 **sp_helptext**</span><span class="sxs-lookup"><span data-stu-id="3560a-120">OBJECT_DEFINITION, OBJECTPROPERTY, **sp_helptext**</span></span>  
 <span data-ttu-id="3560a-121">ロール **public** のメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="3560a-121">Requires membership in the **public** role.</span></span> <span data-ttu-id="3560a-122">ユーザー オブジェクトの定義は、オブジェクトの所有者、または次のいずれかの権限を許可された人が表示できます。ALTER、CONTROL、TAKE OWNERSHIP、VIEW DEFINITION。</span><span class="sxs-lookup"><span data-stu-id="3560a-122">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span> <span data-ttu-id="3560a-123">これらの権限は **db_owner**、 **db_ddladmin**、および **db_securityadmin** 固定データベース ロールのメンバーが暗黙的に保有します。</span><span class="sxs-lookup"><span data-stu-id="3560a-123">These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.</span></span>  
  
 <span data-ttu-id="3560a-124">**sys.sql_expression_dependencies**</span><span class="sxs-lookup"><span data-stu-id="3560a-124">**sys.sql_expression_dependencies**</span></span>  
 <span data-ttu-id="3560a-125">データベースに対する VIEW DEFINITION 権限およびデータベースの **sys.sql_expression_dependencies** に対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3560a-125">Requires VIEW DEFINITION permission on the database and SELECT permission on **sys.sql_expression_dependencies** for the database.</span></span> <span data-ttu-id="3560a-126">既定では、SELECT 権限は **db_owner** 固定データベース ロールのメンバーだけに与えられます。</span><span class="sxs-lookup"><span data-stu-id="3560a-126">By default, SELECT permission is granted only to members of the **db_owner** fixed database role.</span></span> <span data-ttu-id="3560a-127">SELECT 権限と VIEW DEFINITION 権限が別のユーザーに与えられている場合、権限が許可されているユーザーはデータベース内のすべての依存関係を表示できます。</span><span class="sxs-lookup"><span data-stu-id="3560a-127">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3560a-128">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3560a-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-definition-of-a-dml-trigger"></a><span data-ttu-id="3560a-129">DML トリガーの定義を表示するには</span><span class="sxs-lookup"><span data-stu-id="3560a-129">To view the definition of a DML trigger</span></span>  
  
1.  <span data-ttu-id="3560a-130">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="3560a-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3560a-131">目的のデータベースを展開し、 **[テーブル]** を展開します。次に、定義を表示するトリガーが格納されているテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="3560a-131">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger for which you want to view the definition.</span></span>  
  
3.  <span data-ttu-id="3560a-132">**[トリガー]** を展開します。目的のトリガーを右クリックし、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-132">Expand **Triggers**, right-click the trigger you want, and then click **Modify**.</span></span> <span data-ttu-id="3560a-133">DML トリガーの定義がクエリ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3560a-133">The definition of the DML trigger appears in the query window.</span></span>  
  
#### <a name="to-view-the-dependencies-of-a-dml-trigger"></a><span data-ttu-id="3560a-134">DML トリガーの依存関係を表示するには</span><span class="sxs-lookup"><span data-stu-id="3560a-134">To view the dependencies of a DML trigger</span></span>  
  
1.  <span data-ttu-id="3560a-135">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="3560a-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3560a-136">目的のデータベースを展開し、 **[テーブル]** を展開します。次に、表示するトリガーとその依存関係が格納されているテーブルを展開します。</span><span class="sxs-lookup"><span data-stu-id="3560a-136">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger and its dependencies that you want to view.</span></span>  
  
3.  <span data-ttu-id="3560a-137">**[トリガー]** を展開します。目的のトリガーを右クリックし、 **[依存関係の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-137">Expand **Triggers**, right-click the trigger you want, and then click **View Dependencies**.</span></span>  
  
4.  <span data-ttu-id="3560a-138">**[オブジェクトの依存関係]** ウィンドウで DML トリガーに依存するオブジェクトを表示するには、 **[\<DML trigger name> に依存するオブジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3560a-138">In the **Object Dependencies** window, to view the objects that depend on the DML trigger, select **Objects that depend on \<DML trigger name>**.</span></span> <span data-ttu-id="3560a-139">オブジェクトが **[依存関係]** 領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3560a-139">The objects appear in the **Dependencies** area.</span></span>  
  
     <span data-ttu-id="3560a-140">DML が依存するオブジェクトを表示するには、 **[\<DML trigger name> が依存するオブジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3560a-140">To view the objects on which the DML depends, select **Objects on which \<DML trigger name> depends**.</span></span> <span data-ttu-id="3560a-141">オブジェクトが **[依存関係]** 領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3560a-141">The objects appear in the **Dependencies** area.</span></span> <span data-ttu-id="3560a-142">すべてのオブジェクトを表示するには、各ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="3560a-142">Expand each node to see all the objects.</span></span>  
  
5.  <span data-ttu-id="3560a-143">**[依存関係]** 領域に表示されたオブジェクトに関する情報を取得するには、そのオブジェクトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-143">To obtain information about an object that appears in the **Dependencies** area, click the object.</span></span> <span data-ttu-id="3560a-144">**[選択したオブジェクト]** フィールドの **[名前]** 、 **[種類]** 、および **[依存関係の種類]** の各ボックスに情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3560a-144">In the **Selected object** field, information is provided in the **Name**, **Type**, and **Dependency type** boxes.</span></span>  
  
6.  <span data-ttu-id="3560a-145">**[オブジェクトの依存関係]** ウィンドウを閉じるには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-145">To close the **Object Dependencies** window, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3560a-146">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3560a-146">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-definition-of-a-dml-trigger"></a><span data-ttu-id="3560a-147">DML トリガーの定義を表示するには</span><span class="sxs-lookup"><span data-stu-id="3560a-147">To view the definition of a DML trigger</span></span>  
  
1.  <span data-ttu-id="3560a-148">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3560a-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3560a-149">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3560a-150">次のいずれかの例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-150">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="3560a-151">それぞれの例は、 `iuPerson` トリガーの定義を表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3560a-151">Each example shows how you can view the definition of the `iuPerson` trigger.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT definition   
FROM sys.sql_modules  
WHERE object_id = OBJECT_ID(N'Person.iuPerson');   
GO  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'Person.iuPerson')) AS ObjectDefinition;   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
EXEC sp_helptext 'Person.iuPerson'  
GO  
  
```  
  
#### <a name="to-view-the-dependencies-of-a-dml-trigger"></a><span data-ttu-id="3560a-152">DML トリガーの依存関係を表示するには</span><span class="sxs-lookup"><span data-stu-id="3560a-152">To view the dependencies of a DML trigger</span></span>  
  
1.  <span data-ttu-id="3560a-153">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3560a-153">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3560a-154">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-154">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3560a-155">次のいずれかの例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-155">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="3560a-156">それぞれの例は、 `iuPerson` トリガーの依存関係を表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3560a-156">Each example shows how you can view the dependencies of `iuPerson` trigger.</span></span>  
  
```  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
    o.type_desc AS referencing_desciption,   
    COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
    referencing_class_desc, referenced_class_desc,   
    referenced_server_name, referenced_database_name, referenced_schema_name,   
    referenced_entity_name,   
    COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,   
    is_caller_dependent, is_ambiguous  
FROM sys.sql_expression_dependencies AS sed  
INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
WHERE referencing_id = OBJECT_ID(N'Person.iuPerson');   
GO  
  
```  
  
#### <a name="to-view-information-about-dml-triggers-in-the-database"></a><span data-ttu-id="3560a-157">データベース内の DML トリガーに関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="3560a-157">To view information about DML triggers in the database</span></span>  
  
1.  <span data-ttu-id="3560a-158">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3560a-158">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3560a-159">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-159">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3560a-160">次のいずれかの例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-160">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="3560a-161">それぞれの例は、データベース内の DML トリガー (`TR`) に関する情報を表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3560a-161">Each example shows how you can view information about DML triggers (`TR`) in the database.</span></span>  
  
```  
USE AdventureWorks2012;   
GO  
SELECT  name, parent_id, create_date, modify_date, is_instead_of_trigger  
FROM sys.triggers  
WHERE type = 'TR';   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT  name, object_id, schema_id, parent_object_id, type_desc, create_date, modify_date, is_published  
FROM sys.objects  
WHERE type = 'TR';   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT OBJECTPROPERTY(OBJECT_ID(N'Person.iuPerson'), 'ExecIsInsteadOfTrigger');   
GO  
  
```  
  
#### <a name="to-view-information-about-events-that-fire-a-dml-trigger"></a><span data-ttu-id="3560a-162">DML トリガーを起動するイベントに関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="3560a-162">To view information about events that fire a DML trigger</span></span>  
  
1.  <span data-ttu-id="3560a-163">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="3560a-163">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3560a-164">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-164">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3560a-165">次のいずれかの例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3560a-165">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="3560a-166">それぞれの例は、 `iuPerson` トリガーを起動するイベントを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3560a-166">Each example shows how you can view the events that fire the `iuPerson` trigger.</span></span>  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT object_id, type, type_desc, is_trigger_event, event_group_type, event_group_type_desc   
FROM sys.events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
GO  
```  
  
```sql  
USE AdventureWorks2012;   
GO   
SELECT object_id, type,is_first, is_last  
FROM sys.trigger_events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="3560a-167">参照</span><span class="sxs-lookup"><span data-stu-id="3560a-167">See Also</span></span>  
 <span data-ttu-id="3560a-168">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-168">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="3560a-169">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-169">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="3560a-170">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-170">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="3560a-171">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-171">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="3560a-172">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-172">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="3560a-173">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-173">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span></span>  
 <span data-ttu-id="3560a-174">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-174">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="3560a-175">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-175">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="3560a-176">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-176">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="3560a-177">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-177">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="3560a-178">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-178">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="3560a-179">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-179">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="3560a-180">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-180">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="3560a-181">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-181">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="3560a-182">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-182">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="3560a-183">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-183">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="3560a-184">[sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-184">[sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="3560a-185">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3560a-185">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span></span>  
 [<span data-ttu-id="3560a-186">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3560a-186">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-definition-transact-sql)  
  
  
