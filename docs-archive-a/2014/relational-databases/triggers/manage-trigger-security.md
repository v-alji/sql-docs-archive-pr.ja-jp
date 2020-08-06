---
title: トリガーのセキュリティの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], security
ms.assetid: e94720a8-a3a2-4364-b0a3-bbe86e3ce4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: fdc176dcad50c3bf28f058c3724a01267975bfc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644880"
---
# <a name="manage-trigger-security"></a><span data-ttu-id="c73b7-102">トリガーのセキュリティの管理</span><span class="sxs-lookup"><span data-stu-id="c73b7-102">Manage Trigger Security</span></span>
  <span data-ttu-id="c73b7-103">既定では、DML トリガーも DDL トリガーも、トリガーを呼び出したユーザーのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c73b7-103">By default, both DML and DDL triggers execute under the context of the user that calls the trigger.</span></span> <span data-ttu-id="c73b7-104">トリガーの呼び出し元は、トリガーが実行される原因となったステートメントを実行したユーザーです。</span><span class="sxs-lookup"><span data-stu-id="c73b7-104">The caller of a trigger is the user that executes the statement that causes the trigger to run.</span></span> <span data-ttu-id="c73b7-105">たとえば、ユーザー **Mary** が DELETE ステートメントを実行し、このために DML トリガー **DML_trigMary** が実行された場合、 **DML_trigMary** 内のコードは、 **Mary**のユーザー権限のコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c73b7-105">For example, if user **Mary** executes a DELETE statement that causes DML trigger **DML_trigMary** to run, the code inside **DML_trigMary** executes in the context of the user privileges for **Mary**.</span></span> <span data-ttu-id="c73b7-106">この既定の動作は、悪意のあるコードをデータベースやサーバー インスタンスに組み込もうとするユーザーによって悪用される危険性があります。</span><span class="sxs-lookup"><span data-stu-id="c73b7-106">This default behavior can be exploited by users who want to introduce malicious code in the database or server instance.</span></span> <span data-ttu-id="c73b7-107">たとえば、次の DDL トリガーがユーザー `JohnDoe`により作成されたとします。</span><span class="sxs-lookup"><span data-stu-id="c73b7-107">For example, the following DDL trigger is created by user `JohnDoe`:</span></span>  
  
 `CREATE TRIGGER DDL_trigJohnDoe`  
  
 `ON DATABASE`  
  
 `FOR ALTER_TABLE`  
  
 `AS`  
  
 `GRANT CONTROL SERVER TO JohnDoe ;`  
  
 `GO`  
  
 <span data-ttu-id="c73b7-108">このトリガーの内容は、 `GRANT CONTROL SERVER` sysadmin **固定サーバー ロールのメンバーなど、** ステートメントを実行する権限を持ったユーザーが `ALTER TABLE` ステートメントを実行した直後に、 `JohnDoe` に `CONTROL SERVER` 権限を付与するようにしています。</span><span class="sxs-lookup"><span data-stu-id="c73b7-108">What this trigger means is that as soon as a user that has permission to execute a `GRANT CONTROL SERVER` statement, such as a member of the **sysadmin** fixed server role, executes an `ALTER TABLE` statement, `JohnDoe` is granted `CONTROL SERVER` permission.</span></span> <span data-ttu-id="c73b7-109">つまり、 `JohnDoe` 自身は `CONTROL SERVER` 権限を自分に付与することはできませんが、トリガー コードを利用して、上位の特権の下での実行権限を獲得しています。</span><span class="sxs-lookup"><span data-stu-id="c73b7-109">In other words, although `JohnDoe` cannot grant `CONTROL SERVER` permission to himself, he enabled the trigger code that grants him this permission to execute under escalated privileges.</span></span> <span data-ttu-id="c73b7-110">DML トリガーも DDL トリガーも、このようなセキュリティの脅威にさらされています。</span><span class="sxs-lookup"><span data-stu-id="c73b7-110">Both DML and DDL triggers are open to this kind of security threat.</span></span>  
  
## <a name="trigger-security-best-practices"></a><span data-ttu-id="c73b7-111">トリガーのセキュリティに関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="c73b7-111">Trigger Security Best Practices</span></span>  
 <span data-ttu-id="c73b7-112">次の方法を使用することで、トリガー コードが上位の特権の下で実行されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="c73b7-112">You can take the following measures to prevent trigger code from executing under escalated privileges:</span></span>  
  
-   <span data-ttu-id="c73b7-113">[sys.triggers](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) カタログ ビューと [sys.server_triggers](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) カタログ ビューをクエリし、データベースとサーバー インスタンスに存在する DML トリガーおよび DDL トリガーを認識します。</span><span class="sxs-lookup"><span data-stu-id="c73b7-113">Be aware of the DML and DDL triggers that exist in the database and on the server instance by querying the [sys.triggers](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) and [sys.server_triggers](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) catalog views.</span></span> <span data-ttu-id="c73b7-114">次のクエリは、現在のデータベースにあるすべての DML とデータベースレベルのすべての DDL トリガーと、サーバー インスタンスにあるすべてのサーバー レベルの DDL トリガーを返します。</span><span class="sxs-lookup"><span data-stu-id="c73b7-114">The following query returns all DML and database-level DDL triggers in the current database, and all server-level DDL triggers on the server instance:</span></span>  
  
    ```  
    SELECT type, name, parent_class_desc FROM sys.triggers  
    UNION  
    SELECT type, name, parent_class_desc FROM sys.server_triggers ;  
    ```  
  
-   <span data-ttu-id="c73b7-115">[DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) を使用して、トリガーが上位の特権の下で実行された場合に、データベースやサーバーの整合性に支障をきたす可能性のあるトリガーを無効にします。</span><span class="sxs-lookup"><span data-stu-id="c73b7-115">Use [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) to disable triggers that can harm the integrity of the database or server if the triggers execute under escalated privileges.</span></span> <span data-ttu-id="c73b7-116">次のステートメントは、現在のデータベースにあるすべてのデータベースレベルの DDL トリガーを無効にします。</span><span class="sxs-lookup"><span data-stu-id="c73b7-116">The following statement disables all database-level DDL triggers in the current database:</span></span>  
  
    ```  
    DISABLE TRIGGER ALL ON DATABASE  
    ```  
  
     <span data-ttu-id="c73b7-117">このステートメントは、サーバー インスタンスにあるすべてのサーバーレベルの DDL トリガーを無効にします。</span><span class="sxs-lookup"><span data-stu-id="c73b7-117">This statement disables all server-level DDL triggers on the server instance:</span></span>  
  
    ```  
    DISABLE TRIGGER ALL ON ALL SERVER  
    ```  
  
     <span data-ttu-id="c73b7-118">このステートメントは、現在のデータベースにあるすべての DML トリガーを無効にします。</span><span class="sxs-lookup"><span data-stu-id="c73b7-118">This statement disables all DML triggers in the current database:</span></span>  
  
    ```  
    DECLARE @schema_name sysname, @trigger_name sysname, @object_name sysname ;  
    DECLARE @sql nvarchar(max) ;  
    DECLARE trig_cur CURSOR FORWARD_ONLY READ_ONLY FOR  
        SELECT SCHEMA_NAME(schema_id) AS schema_name,  
            name AS trigger_name,  
            OBJECT_NAME(parent_object_id) as object_name  
        FROM sys.objects WHERE type in ('TR', 'TA') ;  
  
    OPEN trig_cur ;  
    FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        SELECT @sql = 'DISABLE TRIGGER ' + QUOTENAME(@schema_name) + '.'  
            + QUOTENAME(@trigger_name) +  
            ' ON ' + QUOTENAME(@schema_name) + '.'   
            + QUOTENAME(@object_name) + ' ; ' ;  
        EXEC (@sql) ;  
        FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
    END  
    GO  
  
    -- Verify triggers are disabled. Should return an empty result set.  
    SELECT * FROM sys.triggers WHERE is_disabled = 0 ;  
    GO  
  
    CLOSE trig_cur ;  
    DEALLOCATE trig_cur;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c73b7-119">参照</span><span class="sxs-lookup"><span data-stu-id="c73b7-119">See Also</span></span>  
 <span data-ttu-id="c73b7-120">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c73b7-120">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="c73b7-121">[DML トリガー](../triggers/dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="c73b7-121">[DML Triggers](../triggers/dml-triggers.md) </span></span>  
 [<span data-ttu-id="c73b7-122">DDL トリガー</span><span class="sxs-lookup"><span data-stu-id="c73b7-122">DDL Triggers</span></span>](../triggers/ddl-triggers.md)  
  
  
