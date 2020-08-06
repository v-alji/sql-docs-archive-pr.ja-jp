---
title: DDL トリガー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL triggers, about DDL triggers
ms.assetid: 1a4a6564-9820-4a14-9305-2c0e9ea37454
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cbcc9f1efc477b8c54ad131f9efa9ff49cc5845
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644895"
---
# <a name="ddl-triggers"></a><span data-ttu-id="edb17-102">DDL トリガー</span><span class="sxs-lookup"><span data-stu-id="edb17-102">DDL Triggers</span></span>
  <span data-ttu-id="edb17-103">DDL トリガーは、さまざまなデータ定義言語 (DDL) イベントに対応して起動されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-103">DDL triggers fire in response to a variety of Data Definition Language (DDL) events.</span></span> <span data-ttu-id="edb17-104">これらのイベントは主に、CREATE、ALTER、DROP、GRANT、DENY、REVOKE、UPDATE STATISTICS のいずれかのキーワードで始まる [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに対応します。</span><span class="sxs-lookup"><span data-stu-id="edb17-104">These events primarily correspond to [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that start with the keywords CREATE, ALTER, DROP, GRANT, DENY, REVOKE or UPDATE STATISTICS.</span></span> <span data-ttu-id="edb17-105">DDL と同様の操作を実行する特定のシステム ストアド プロシージャも DDL トリガーを起動できます。</span><span class="sxs-lookup"><span data-stu-id="edb17-105">Certain system stored procedures that perform DDL-like operations can also fire DDL triggers.</span></span>  
  
 <span data-ttu-id="edb17-106">DDL トリガーは、次のような場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="edb17-106">Use DDL triggers when you want to do the following:</span></span>  
  
-   <span data-ttu-id="edb17-107">データベース スキーマへの特定の変更を回避する。</span><span class="sxs-lookup"><span data-stu-id="edb17-107">Prevent certain changes to your database schema.</span></span>  
  
-   <span data-ttu-id="edb17-108">データベース スキーマの変更に対して、データベース内でなんらかの処理を実行する。</span><span class="sxs-lookup"><span data-stu-id="edb17-108">Have something occur in the database in response to a change in your database schema.</span></span>  
  
-   <span data-ttu-id="edb17-109">データベース スキーマの変更またはイベントを記録する。</span><span class="sxs-lookup"><span data-stu-id="edb17-109">Record changes or events in the database schema.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="edb17-110">DDL トリガーはテストして、実行されているシステム ストアド プロシージャに応答するかどうか、確認してください。</span><span class="sxs-lookup"><span data-stu-id="edb17-110">Test your DDL triggers to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="edb17-111">たとえば、CREATE TYPE ステートメントおよび **sp_addtype** ストアド プロシージャはどちらも、CREATE_TYPE イベントで作成される DDL トリガーを起動します。</span><span class="sxs-lookup"><span data-stu-id="edb17-111">For example, the CREATE TYPE statement and the **sp_addtype** stored procedure will both fire a DDL trigger that is created on a CREATE_TYPE event.</span></span>  
  
## <a name="types-of-ddl-triggers"></a><span data-ttu-id="edb17-112">DDL トリガーの種類</span><span class="sxs-lookup"><span data-stu-id="edb17-112">Types of DDL Triggers</span></span>  
 <span data-ttu-id="edb17-113">Transact-SQL DDL トリガー</span><span class="sxs-lookup"><span data-stu-id="edb17-113">Transact-SQL DDL Trigger</span></span>  
 <span data-ttu-id="edb17-114">サーバー スコープまたはデータベース スコープのイベントに応答して [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント (複数可) を実行する特殊な [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="edb17-114">A special type of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure that executes one or more [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in response to a server-scoped or database-scoped event.</span></span> <span data-ttu-id="edb17-115">たとえば、ALTER SERVER CONFIGURATION などのステートメントが実行されたときや、DROP TABLE を使用してテーブルが削除されたときに、DDL トリガーを起動させることができます。</span><span class="sxs-lookup"><span data-stu-id="edb17-115">For example, a DDL Trigger may fire if a statement such as ALTER SERVER CONFIGURATION is executed or if a table is deleted by using DROP TABLE.</span></span>  
  
 <span data-ttu-id="edb17-116">CLR DDL トリガー</span><span class="sxs-lookup"><span data-stu-id="edb17-116">CLR DDL Trigger</span></span>  
 <span data-ttu-id="edb17-117">CLR トリガーは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを実行するのではなく、.NET Framework で作成され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でアップロードされたアセンブリのメンバーであるマネージド コードに記述されている、1 つ以上のメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="edb17-117">Instead of executing a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, a CLR trigger executes one or more methods written in managed code that are members of an assembly created in the .NET Framework and uploaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="edb17-118">DDL トリガーは、起動元の DDL ステートメントが実行されるまで、起動されません。</span><span class="sxs-lookup"><span data-stu-id="edb17-118">DDL triggers fire only after the DDL statements that trigger them are run.</span></span> <span data-ttu-id="edb17-119">DDL トリガーを INSTEAD OF トリガーの代わりに使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="edb17-119">DDL triggers cannot be used as INSTEAD OF triggers.</span></span> <span data-ttu-id="edb17-120">DDL トリガーは、ローカルまたはグローバルの一時テーブルおよびストアド プロシージャに影響するイベントに応答して起動されることはありません。</span><span class="sxs-lookup"><span data-stu-id="edb17-120">DDL triggers do not fire in response to events that affect local or global temporary tables and stored procedures.</span></span>  
  
 <span data-ttu-id="edb17-121">DDL トリガーでは、特殊な `inserted` テーブルや `deleted` テーブルは作成されません。</span><span class="sxs-lookup"><span data-stu-id="edb17-121">DDL triggers do not create the special `inserted` and `deleted` tables.</span></span>  
  
 <span data-ttu-id="edb17-122">DDL トリガーを起動するイベントの情報と、起動したトリガーにより加えられる変更は、EVENTDATA 関数を使用してキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="edb17-122">The information about an event that fires a DDL trigger, and the subsequent changes caused by the trigger, is captured by using the EVENTDATA function.</span></span>  
  
 <span data-ttu-id="edb17-123">DDL イベントごとに作成される複数のトリガー。</span><span class="sxs-lookup"><span data-stu-id="edb17-123">Multiple triggers to be created for each DDL event.</span></span>  
  
 <span data-ttu-id="edb17-124">DML トリガーと異なり、DDL トリガーのスコープはスキーマに設定されません。</span><span class="sxs-lookup"><span data-stu-id="edb17-124">Unlike DML triggers, DDL triggers are not scoped to schemas.</span></span> <span data-ttu-id="edb17-125">このため、DDL トリガーに関するメタデータのクエリに、OBJECT_ID、OBJECT_NAME、OBJECTPROPERTY、OBJECTPROPERTYEX などの関数を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="edb17-125">Therefore, functions such as OBJECT_ID, OBJECT_NAME, OBJECTPROPERTY, and OBJECTPROPERTYEX cannot be used for querying metadata about DDL triggers.</span></span> <span data-ttu-id="edb17-126">代わりに、カタログ ビューを使用してください。</span><span class="sxs-lookup"><span data-stu-id="edb17-126">Use the catalog views instead.</span></span>  
  
 <span data-ttu-id="edb17-127">サーバー スコープの DDL トリガーは、SQL Server Management Studio のオブジェクト エクスプローラーの **[Triggers]** フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-127">Server-scoped DDL triggers appear in the SQL Server Management Studio Object Explorer in the **Triggers** folder.</span></span> <span data-ttu-id="edb17-128">このフォルダーは、 **[Server Objects]** フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="edb17-128">This folder is located under the **Server Objects** folder.</span></span> <span data-ttu-id="edb17-129">データベース スコープの DDL トリガーは、 **[データベース トリガー]** フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-129">Database-scoped DDL triggers appear in the **Database Triggers** folder.</span></span> <span data-ttu-id="edb17-130">このフォルダーは対応するデータベースの **[Programmability]** フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="edb17-130">This folder is located under the **Programmability** folder of the corresponding database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="edb17-131">上位の特権の下では、トリガー内の悪意のあるコードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="edb17-131">Malicious code inside triggers can run under escalated privileges.</span></span> <span data-ttu-id="edb17-132">この脅威の軽減方法の詳細については、「 [トリガーのセキュリティの管理](manage-trigger-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edb17-132">For more information about how to help reduce this threat, see [Manage Trigger Security](manage-trigger-security.md).</span></span>  
  
## <a name="ddl-trigger-scope"></a><span data-ttu-id="edb17-133">DDL トリガーのスコープ</span><span class="sxs-lookup"><span data-stu-id="edb17-133">DDL Trigger Scope</span></span>  
 <span data-ttu-id="edb17-134">DDL トリガーは、現在のデータベースまたは現在のサーバーで処理されている [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントに応答して起動されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-134">DDL triggers can fire in response to a [!INCLUDE[tsql](../../includes/tsql-md.md)] event processed in the current database, or on the current server.</span></span> <span data-ttu-id="edb17-135">トリガーのスコープは、イベントによって異なります。</span><span class="sxs-lookup"><span data-stu-id="edb17-135">The scope of the trigger depends on the event.</span></span> <span data-ttu-id="edb17-136">たとえば、CREATE_TABLE イベントに応答して起動されるように作成された DDL トリガーは、データベース、またはサーバー インスタンスで CREATE_TABLE イベントが発生するたびに起動されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-136">For example, a DDL trigger created to fire in response to a CREATE_TABLE event can do so whenever a CREATE_TABLE event occurs in the database, or on the server instance.</span></span> <span data-ttu-id="edb17-137">CREATE_LOGIN イベントに応答して起動されるように作成された DDL トリガーは、サーバー インスタンスで CREATE_LOGIN イベントが発生した場合にのみ起動できます。</span><span class="sxs-lookup"><span data-stu-id="edb17-137">A DDL trigger created to fire in response to a CREATE_LOGIN event can do so only when a CREATE_LOGIN event occurs in the server instance.</span></span>  
  
 <span data-ttu-id="edb17-138">次の例では、データベースで `safety` イベントまたは `DROP_TABLE` イベントが発生するたびに、DDL トリガー `ALTER_TABLE` が起動されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-138">In the following example, DDL trigger `safety` will fire whenever a `DROP_TABLE` or `ALTER_TABLE` event occurs in the database.</span></span>  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_TABLE, ALTER_TABLE   
AS   
   PRINT 'You must disable Trigger "safety" to drop or alter tables!'   
   ROLLBACK;  
```  
  
 <span data-ttu-id="edb17-139">次の例では、現在のサーバー インスタンスで `CREATE_DATABASE` イベントが発生した場合に、DDL トリガーによってメッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-139">In the following example, a DDL trigger prints a message if any `CREATE_DATABASE` event occurs on the current server instance.</span></span> <span data-ttu-id="edb17-140">この例では、対応する `EVENTDATA` ステートメントのテキストを取得するために [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="edb17-140">The example uses the `EVENTDATA` function to retrieve the text of the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="edb17-141">DDL トリガーで EVENTDATA を使用する方法の詳細については、「 [EVENTDATA 関数の使用](use-the-eventdata-function.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edb17-141">For more information about how to use EVENTDATA with DDL triggers, see [Use the EVENTDATA Function](use-the-eventdata-function.md).</span></span>  
  
```  
IF EXISTS (SELECT * FROM sys.server_triggers  
    WHERE name = 'ddl_trig_database')  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
CREATE TRIGGER ddl_trig_database   
ON ALL SERVER   
FOR CREATE_DATABASE   
AS   
    PRINT 'Database Created.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
GO  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
  
```  
  
 <span data-ttu-id="edb17-142">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに指定できるスコープをそのステートメントに対応付けた一覧については、「DDL トリガーを起動するための、特定の DDL ステートメントの選択」に記載されたリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="edb17-142">The lists that map the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to the scopes that can be specified for them are available through the links provided in the section "Selecting a Particular DDL Statement to Fire a DDL Trigger," later in this topic.</span></span>  
  
 <span data-ttu-id="edb17-143">データベース スコープが設定された DDL トリガーは、DDL トリガーが作成されたデータベースにオブジェクトとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-143">Database-scoped DDL triggers are stored as objects in the database in which they are created.</span></span> <span data-ttu-id="edb17-144">DDL トリガーを **master** データベースに作成することもでき、ユーザーが設計したデータベースで作成されたトリガーと同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="edb17-144">DDL triggers can be created in the **master** database and behave just like those created in user-designed databases.</span></span> <span data-ttu-id="edb17-145">**sys.triggers** カタログ ビューにクエリを実行することで、DDL トリガーに関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="edb17-145">You can obtain information about DDL triggers by querying the **sys.triggers** catalog view.</span></span> <span data-ttu-id="edb17-146">トリガーが作成されたデータベース コンテキスト内の **sys.triggers** に対してクエリを実行できます。または、識別子 (たとえば、 **master.sys.triggers**) としてデータベース名を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="edb17-146">You can query **sys.triggers** within the database context in which the triggers are created or by specifying the database name as an identifier, such as **master.sys.triggers**.</span></span>  
  
 <span data-ttu-id="edb17-147">サーバー スコープが設定された DDL トリガーは、 **master** データベースにオブジェクトとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-147">Server-scoped DDL triggers are stored as objects in the **master** database.</span></span> <span data-ttu-id="edb17-148">ただし、サーバー スコープが設定された DDL トリガーに関する情報は、任意のデータベース コンテキストの **sys.server_triggers** カタログ ビューから取得できます。</span><span class="sxs-lookup"><span data-stu-id="edb17-148">However, you can obtain information about server-scoped DDL triggers by querying the **sys.server_triggers** catalog view in any database context.</span></span>  
  
## <a name="specifying-a-transact-sql-statement-or-group-of-statements"></a><span data-ttu-id="edb17-149">Transact-SQL ステートメントまたはステートメントのグループの指定</span><span class="sxs-lookup"><span data-stu-id="edb17-149">Specifying a Transact-SQL Statement or Group of Statements</span></span>  
  
### <a name="selecting-a-particular-ddl-statement-to-fire-a-ddl-trigger"></a><span data-ttu-id="edb17-150">DDL トリガーを起動するための、特定の DDL ステートメントの選択</span><span class="sxs-lookup"><span data-stu-id="edb17-150">Selecting a Particular DDL Statement to Fire a DDL Trigger</span></span>  
 <span data-ttu-id="edb17-151">DDL トリガーは、1 つ以上の特定の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが実行された後に起動されるように設計できます。</span><span class="sxs-lookup"><span data-stu-id="edb17-151">DDL triggers can be designed to fire after one or more particular [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are run.</span></span> <span data-ttu-id="edb17-152">前の例では、 `safety` イベント、または `DROP_TABLE` イベントの後に `ALTER_TABLE` トリガーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-152">In the previous example, trigger `safety` fires after any `DROP_TABLE` or `ALTER_TABLE` event.</span></span> <span data-ttu-id="edb17-153">DDL トリガーを起動するために指定できる各 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、および DDL トリガーを起動できるスコープの一覧については、「 [DDL イベント](ddl-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edb17-153">For lists of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that can be specified to fire a DDL trigger, and the scope at which the trigger can fire, see [DDL Events](ddl-events.md).</span></span>  
  
### <a name="selecting-a-predefined-group-of-ddl-statements-to-fire-a-ddl-trigger"></a><span data-ttu-id="edb17-154">DDL トリガーを起動するための、事前定義済み DDL ステートメントのグループの選択</span><span class="sxs-lookup"><span data-stu-id="edb17-154">Selecting a Predefined Group of DDL Statements to Fire a DDL Trigger</span></span>  
 <span data-ttu-id="edb17-155">類似したイベントの事前定義済みのグループに所属する [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントを実行した後に、DDL トリガーを起動できます。</span><span class="sxs-lookup"><span data-stu-id="edb17-155">A DDL trigger can fire after execution of any [!INCLUDE[tsql](../../includes/tsql-md.md)] event that belongs to a predefined grouping of similar events.</span></span> <span data-ttu-id="edb17-156">たとえば、CREATE TABLE ステートメント、ALTER TABLE ステートメント、または DROP TABLE ステートメントのいずれかの実行後に DDL トリガーを発生させる場合、CREATE TRIGGER ステートメントで FOR DDL_TABLE_EVENTS を指定できます。</span><span class="sxs-lookup"><span data-stu-id="edb17-156">For example, if you want a DDL trigger to fire after any CREATE TABLE, ALTER TABLE, or DROP TABLE statement is run, you can specify FOR DDL_TABLE_EVENTS in the CREATE TRIGGER statement.</span></span> <span data-ttu-id="edb17-157">CREATE TRIGGER の実行後、イベント グループで対応されるイベントが **sys.trigger_events** カタログ ビューに追加されます。</span><span class="sxs-lookup"><span data-stu-id="edb17-157">After CREATE TRIGGER is run, the events that are covered by an event group are added to the **sys.trigger_events** catalog view.</span></span>  
  
 <span data-ttu-id="edb17-158">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]で、イベント グループに対してトリガーを作成した場合、 **sys.trigger_events** にはイベント グループについての情報が含まれず、 **sys.trigger_events** にはそのグループで対応される個々のイベントについての情報のみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="edb17-158">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if a trigger is created on an event group, **sys.trigger_events** does not include information about the event group, **sys.trigger_events** includes information only about the individual events covered by that group.</span></span> <span data-ttu-id="edb17-159">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、 **sys.trigger_events** が、トリガーが作成されたイベント グループに関するメタデータ、およびイベント グループが対応する個々のイベントに関するメタデータも保持します。</span><span class="sxs-lookup"><span data-stu-id="edb17-159">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and higher, **sys.trigger_events** persists metadata about the event group on which the triggers is created, and also about the individual events that the event group covers.</span></span> <span data-ttu-id="edb17-160">したがって、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のイベント グループで対応されたイベントに変更を加えても、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]のイベント グループに対して作成される DDL トリガーには適用されません。</span><span class="sxs-lookup"><span data-stu-id="edb17-160">Therefore, changes to the events that are covered by event groups in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and higher do not apply to DDL triggers that are created on those event groups in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="edb17-161">DDL トリガーで使用できる事前定義済みの DDL ステートメントのグループ、そのグループが対応する特定のステートメント、およびこれらのイベント グループをプログラミングできるスコープの一覧については、「 [DDL イベント グループ](ddl-event-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edb17-161">For a list of the predefined groups of DDL statements that are available for DDL triggers, the particular statements the event groups cover, and the scopes at which these event groups can be programmed, see [DDL Event Groups](ddl-event-groups.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="edb17-162">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="edb17-162">Related Tasks</span></span>  
  
|<span data-ttu-id="edb17-163">タスク</span><span class="sxs-lookup"><span data-stu-id="edb17-163">Task</span></span>|<span data-ttu-id="edb17-164">トピック</span><span class="sxs-lookup"><span data-stu-id="edb17-164">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="edb17-165">DDL トリガーを作成、変更、削除、または無効化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="edb17-165">Describes how to create, modify, delete or disable DDL triggers.</span></span>|[<span data-ttu-id="edb17-166">DDL トリガーの実装</span><span class="sxs-lookup"><span data-stu-id="edb17-166">Implement DDL Triggers</span></span>](implement-ddl-triggers.md)|  
|<span data-ttu-id="edb17-167">CLR DDL トリガーの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="edb17-167">Describes how to create a CLR DDL trigger.</span></span>|[<span data-ttu-id="edb17-168">CLR トリガーの作成</span><span class="sxs-lookup"><span data-stu-id="edb17-168">Create CLR Triggers</span></span>](create-clr-triggers.md)|  
|<span data-ttu-id="edb17-169">DDL トリガーに関する情報を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="edb17-169">Describes how to return information about DDL triggers.</span></span>|[<span data-ttu-id="edb17-170">DDL トリガーに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="edb17-170">Get Information About DDL Triggers</span></span>](get-information-about-ddl-triggers.md)|  
|<span data-ttu-id="edb17-171">DDL トリガーを起動するイベントの情報を、EVENTDATA 関数を使用して取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="edb17-171">Describes how to return information about an event that fires a DDL trigger by using the EVENTDATA function.</span></span>|[<span data-ttu-id="edb17-172">EVENTDATA 関数の使用</span><span class="sxs-lookup"><span data-stu-id="edb17-172">Use the EVENTDATA Function</span></span>](use-the-eventdata-function.md)|  
|<span data-ttu-id="edb17-173">トリガーのセキュリティを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="edb17-173">Describes how to manage trigger security.</span></span>|[<span data-ttu-id="edb17-174">トリガーのセキュリティの管理</span><span class="sxs-lookup"><span data-stu-id="edb17-174">Manage Trigger Security</span></span>](manage-trigger-security.md)|  
  
## <a name="see-also"></a><span data-ttu-id="edb17-175">参照</span><span class="sxs-lookup"><span data-stu-id="edb17-175">See Also</span></span>  
 <span data-ttu-id="edb17-176">[DML トリガー](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="edb17-176">[DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="edb17-177">[ログオン トリガー](logon-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="edb17-177">[Logon Triggers](logon-triggers.md) </span></span>  
 [<span data-ttu-id="edb17-178">CREATE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="edb17-178">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
  
