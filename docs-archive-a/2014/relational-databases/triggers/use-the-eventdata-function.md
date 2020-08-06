---
title: EVENTDATA 関数の使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- EVENTDATA function
- DDL triggers, EVENTDATA function
ms.assetid: 675b8320-9c73-4526-bd2f-91ba42c1b604
author: rothja
ms.author: jroth
ms.openlocfilehash: 57fb59a3954fb00ab943944c58cccd352c7270d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644878"
---
# <a name="use-the-eventdata-function"></a><span data-ttu-id="4b574-102">EVENTDATA 関数の使用</span><span class="sxs-lookup"><span data-stu-id="4b574-102">Use the EVENTDATA Function</span></span>
  <span data-ttu-id="4b574-103">DDL トリガーを起動するイベントに関する情報は、EVENTDATA 関数を使用してキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="4b574-103">Information about an event that fires a DDL trigger is captured by using the EVENTDATA function.</span></span> <span data-ttu-id="4b574-104">この関数は、`xml` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="4b574-104">This function returns an `xml` value.</span></span> <span data-ttu-id="4b574-105">XML スキーマには、次の項目に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b574-105">The XML schema includes information about the following:</span></span>  
  
-   <span data-ttu-id="4b574-106">イベントの時刻。</span><span class="sxs-lookup"><span data-stu-id="4b574-106">The time of the event.</span></span>  
  
-   <span data-ttu-id="4b574-107">トリガーが実行されたときの接続のシステム プロセス ID (SPID)。</span><span class="sxs-lookup"><span data-stu-id="4b574-107">The System Process ID (SPID) of the connection when the trigger executed.</span></span>  
  
-   <span data-ttu-id="4b574-108">トリガーを起動したイベントの種類。</span><span class="sxs-lookup"><span data-stu-id="4b574-108">The type of event that fired the trigger.</span></span>  
  
 <span data-ttu-id="4b574-109">イベントの種類に応じて、イベントが発生したデータベース、イベントが発生したオブジェクト、イベントの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントなどの追加情報がスキーマに含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b574-109">Depending on the event type, the schema then includes additional information such as the database in which the event occurred, the object against which the event occurred, and the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement of the event.</span></span> <span data-ttu-id="4b574-110">詳細については、「 [DDL トリガー](ddl-triggers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b574-110">For more information, see [DDL Triggers](ddl-triggers.md).</span></span>  
  
 <span data-ttu-id="4b574-111">たとえば、次の DDL トリガーが [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースに作成されたとします。</span><span class="sxs-lookup"><span data-stu-id="4b574-111">For example, the following DDL trigger is created in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database:</span></span>  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR CREATE_TABLE   
AS   
    PRINT 'CREATE TABLE Issued.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
   RAISERROR ('New tables cannot be created in this database.', 16, 1)   
   ROLLBACK  
;  
```  
  
 <span data-ttu-id="4b574-112">次に、以下の `CREATE TABLE` ステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="4b574-112">The following `CREATE TABLE` statement is then run:</span></span>  
  
 `CREATE TABLE NewTable (Column1 int);`  
  
 <span data-ttu-id="4b574-113">DDL トリガーの `EVENTDATA()` ステートメントにより、 `CREATE TABLE` ステートメントでは許可されないテキストがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="4b574-113">The `EVENTDATA()` statement in the DDL trigger captures the text of the `CREATE TABLE` statement that is not allowed.</span></span> <span data-ttu-id="4b574-114">これは、 `xml` EVENTDATA によって生成されたデータに対して XQuery ステートメントを使用し、要素を取得することで実現され \<CommandText> ます。</span><span class="sxs-lookup"><span data-stu-id="4b574-114">This is achieved by using an XQuery statement against the `xml` data that is generated by EVENTDATA and retrieving the \<CommandText> element.</span></span> <span data-ttu-id="4b574-115">詳細については、「[XQuery 言語リファレンス &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b574-115">For more information, see [XQuery Language Reference &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="4b574-116">EVENTDATA は、CREATE_SCHEMA イベントのデータをキャプチャします。対応する CREATE SCHEMA 定義の <schema_element> がある場合にはそれもキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="4b574-116">EVENTDATA captures the data of CREATE_SCHEMA events as well as the <schema_element> of the corresponding CREATE SCHEMA definition, if any exists.</span></span> <span data-ttu-id="4b574-117">さらに、EVENTDATA は <schema_element> 定義を別のイベントとして認識します。</span><span class="sxs-lookup"><span data-stu-id="4b574-117">Additionally, EVENTDATA recognizes the <schema_element> definition as a separate event.</span></span> <span data-ttu-id="4b574-118">したがって、CREATE_SCHEMA イベント、および CREATE SCHEMA 定義の <schema_element> によって表されるイベントの両方で作成される DDL トリガーは、`TSQLCommand` データのように同じイベント データを 2 回返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="4b574-118">Therefore, a DDL trigger created on both a CREATE_SCHEMA event, and an event represented by the <schema_element> of the CREATE SCHEMA definition, may return the same event data twice, such as the `TSQLCommand` data.</span></span> <span data-ttu-id="4b574-119">たとえば、CREATE_SCHEMA イベントと CREATE_TABLE イベントの両方で DDL トリガーが作成され、次のバッチを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="4b574-119">For example, consider a DDL trigger that is created on both the CREATE_SCHEMA and CREATE_TABLE events and the following batch is run:</span></span>  
>   
>  `CREATE SCHEMA s`  
>   
>  `CREATE TABLE t1 (col1 int)`  
>   
>  <span data-ttu-id="4b574-120">アプリケーションで CREATE_TABLE イベントの `TSQLCommand` データを取得する場合は、このデータが 2 回発生する可能性があることに注意してください。つまり、CREATE_SCHEMA イベントの発生時と、CREATE_TABLE イベントの発生時です。</span><span class="sxs-lookup"><span data-stu-id="4b574-120">If the application retrieves the `TSQLCommand` data of the CREATE_TABLE event, be aware that this data may appear two times: once when the CREATE_SCHEMA event occurs, and again when the CREATE_TABLE event occurs.</span></span> <span data-ttu-id="4b574-121">CREATE_SCHEMA イベントと、対応する CREATE SCHEMA 定義の <schema_element> テキストの両方で DDL トリガーを作成しないようにするか、または同じイベントを 2 回処理しないようにアプリケーションのロジックを作成します。</span><span class="sxs-lookup"><span data-stu-id="4b574-121">Avoid creating DDL triggers on both the CREATE_SCHEMA events and the <schema_element> texts of any corresponding CREATE SCHEMA definitions, or build logic into your application so that the same event is not processed twice.</span></span>  
  
## <a name="alter-table-and-alter-database-events"></a><span data-ttu-id="4b574-122">ALTER TABLE イベントと ALTER DATABASE イベント</span><span class="sxs-lookup"><span data-stu-id="4b574-122">ALTER TABLE and ALTER DATABASE Events</span></span>  
 <span data-ttu-id="4b574-123">ALTER_TABLE および ALTER_DATABASE イベントのイベント データには、DDL ステートメントの影響を受けた他のオブジェクトの名前と種類、およびそれらのオブジェクトで実行されたアクションも含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b574-123">The event data for the ALTER_TABLE and ALTER_DATABASE events also includes the names and types of other objects affected by the DDL statement and the action performed on these objects.</span></span> <span data-ttu-id="4b574-124">ALTER_TABLE イベント データには、ALTER TABLE ステートメントの影響を受けた列、制約、またはトリガーの名前と、それらのオブジェクトで実行されたアクション (作成、変更、削除、有効化、または無効化) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b574-124">The ALTER_TABLE event data includes the names of the columns, constraints, or triggers affected by the ALTER TABLE statement and the action (create, alter, drop, enable, or disable) performed on the affected objects.</span></span> <span data-ttu-id="4b574-125">ALTER_DATABASE イベント データには、ALTER DATABASE ステートメントの影響を受けたファイルまたはファイル グループの名前と、それらのオブジェクトで実行されたアクション (作成、変更、または削除) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4b574-125">The ALTER_DATABASE event data includes the names of any files or filegroups affected by the ALTER DATABASE statement and the action (create, alter, or drop) performed on the affected objects.</span></span>  
  
 <span data-ttu-id="4b574-126">たとえば、次の DDL トリガーを AdventureWorks サンプル データベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="4b574-126">For example, create the following DDL trigger in the AdventureWorks sample database:</span></span>  
  
```  
CREATE TRIGGER ColumnChanges  
ON DATABASE   
FOR ALTER_TABLE  
AS  
-- Detect whether a column was created/altered/dropped.  
SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]', 'nvarchar(max)')  
RAISERROR ('Table schema cannot be modified in this database.', 16, 1);  
ROLLBACK;  
```  
  
 <span data-ttu-id="4b574-127">次に、制約に違反する次の ALTER TABLE ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="4b574-127">Then execute the following ALTER TABLE statement that violates a constraint:</span></span>  
  
```  
ALTER TABLE Person.Address ALTER COLUMN ModifiedDate date;   
```  
  
 <span data-ttu-id="4b574-128">DDL トリガーの EVENTDATA() ステートメントにより、 `ALTER TABLE` ステートメントでは許可されないテキストがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="4b574-128">The EVENTDATA() statement in the DDL trigger captures the text of the `ALTER TABLE` statement that is not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b574-129">例</span><span class="sxs-lookup"><span data-stu-id="4b574-129">Example</span></span>  
 <span data-ttu-id="4b574-130">EVENTDATA 関数を使用して、イベントのログを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4b574-130">You can use the EVENTDATA function to create a log of events.</span></span> <span data-ttu-id="4b574-131">次の例では、イベント情報を格納するためのテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4b574-131">In the following example, a table is created to store event information.</span></span> <span data-ttu-id="4b574-132">次に、現在のデータベースに DDL トリガーが作成されます。この DDL トリガーにより、データベース レベルの DDL イベントが発生するたびに、次の情報がテーブルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="4b574-132">A DDL trigger is then created on the current database that populates the table with the following information whenever any database-level DDL event occurs:</span></span>  
  
-   <span data-ttu-id="4b574-133">イベントの時刻 (GETDATE 関数を使用)。</span><span class="sxs-lookup"><span data-stu-id="4b574-133">The time of the event (using the GETDATE function).</span></span>  
  
-   <span data-ttu-id="4b574-134">イベントが発生したセッションのデータベース ユーザー (CURRENT_USER 関数を使用)。</span><span class="sxs-lookup"><span data-stu-id="4b574-134">The database user against whose session the event occurred (using the CURRENT_USER function).</span></span>  
  
-   <span data-ttu-id="4b574-135">イベントの種類。</span><span class="sxs-lookup"><span data-stu-id="4b574-135">The type of the event.</span></span>  
  
-   <span data-ttu-id="4b574-136">イベントが含まれる [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント。</span><span class="sxs-lookup"><span data-stu-id="4b574-136">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that comprised the event.</span></span>  
  
 <span data-ttu-id="4b574-137">最後の 2 つの項目は、EVENTDATA によって生成された `xml` データに対して XQuery を使用することによってキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="4b574-137">Again, the last two items are captured by using XQuery against the `xml` data that is generated by EVENTDATA.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE ddl_log (PostTime datetime, DB_User nvarchar(100), Event nvarchar(100), TSQL nvarchar(2000));  
GO  
CREATE TRIGGER log   
ON DATABASE   
FOR DDL_DATABASE_LEVEL_EVENTS   
AS  
DECLARE @data XML  
SET @data = EVENTDATA()  
INSERT ddl_log   
   (PostTime, DB_User, Event, TSQL)   
   VALUES   
   (GETDATE(),   
   CONVERT(nvarchar(100), CURRENT_USER),   
   @data.value('(/EVENT_INSTANCE/EventType)[1]', 'nvarchar(100)'),   
   @data.value('(/EVENT_INSTANCE/TSQLCommand)[1]', 'nvarchar(2000)') ) ;  
GO  
--Test the trigger  
CREATE TABLE TestTable (a int)  
DROP TABLE TestTable ;  
GO  
SELECT * FROM ddl_log ;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4b574-138">イベント データを返す場合は、`value()` メソッドの代わりに XQuery の `query()` メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="4b574-138">To return event data, we recommend that you use the XQuery `value()` method instead of the `query()` method.</span></span> <span data-ttu-id="4b574-139">`query()` メソッドでは、出力として XML の他に、アンパサンド記号でエスケープされたキャリッジ リターンとライン フィード (CRLF) の組み合わせが返されます。それに対して `value()` メソッドの出力には、CRLF の組み合わせが表示されません。</span><span class="sxs-lookup"><span data-stu-id="4b574-139">The `query()` method returns XML and ampersand-escaped carriage return and line-feed (CRLF) instances in the output, while the `value()` method renders CRLF instances invisible in the output.</span></span>  
  
 <span data-ttu-id="4b574-140">同様の DDL トリガーの例を、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースで提供しています。</span><span class="sxs-lookup"><span data-stu-id="4b574-140">A similar DDL trigger example is provided with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="4b574-141">この例を入手するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して Database Triggers フォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="4b574-141">To obtain the example, locate the Database Triggers folder by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4b574-142">このフォルダーは **データベースの** [プログラミング] [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="4b574-142">This folder is located under the **Programmability** folder of the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="4b574-143">**ddlDatabaseTriggerLog** を右クリックし、 **[データベース トリガーをスクリプト化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b574-143">Right-click **ddlDatabaseTriggerLog** and select **Script Database Trigger as**.</span></span> <span data-ttu-id="4b574-144">既定では、DDL トリガー **ddlDatabaseTriggerLog** は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="4b574-144">By default, DDL trigger **ddlDatabaseTriggerLog** is disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b574-145">参照</span><span class="sxs-lookup"><span data-stu-id="4b574-145">See Also</span></span>  
 <span data-ttu-id="4b574-146">[DDL イベント](../triggers/ddl-events.md) </span><span class="sxs-lookup"><span data-stu-id="4b574-146">[DDL Events](../triggers/ddl-events.md) </span></span>  
 [<span data-ttu-id="4b574-147">DDL イベント グループ</span><span class="sxs-lookup"><span data-stu-id="4b574-147">DDL Event Groups</span></span>](../triggers/ddl-event-groups.md)  
  
  