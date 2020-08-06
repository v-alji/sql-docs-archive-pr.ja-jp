---
title: WMI Provider for Server Events での WQL の使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Server Events, WQL
ms.assetid: 58b67426-1e66-4445-8e2c-03182e94c4be
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: df2bbf5c6031781494695f95116441fde34bf4f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640801"
---
# <a name="using-wql-with-the-wmi-provider-for-server-events"></a><span data-ttu-id="7018e-102">WMI Provider for Server Events と WQL の使用</span><span class="sxs-lookup"><span data-stu-id="7018e-102">Using WQL with the WMI Provider for Server Events</span></span>
  <span data-ttu-id="7018e-103">管理アプリケーションは WQL (WMI Query Language) ステートメントを実行することにより、WMI Provider for Server Events を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="7018e-103">Management applications access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events using the WMI Provider for Server Events by issuing WMI Query Language (WQL) statements.</span></span> <span data-ttu-id="7018e-104">WQL は、WMI 特有の拡張機能を複数持つ、構造化照会言語 (SQL) の単純化されたサブセットです。</span><span class="sxs-lookup"><span data-stu-id="7018e-104">WQL is a simplified subset of structured query language (SQL), with some WMI-specific extensions.</span></span> <span data-ttu-id="7018e-105">WQL を使用した場合、アプリケーションは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンス、データベース、またはデータベース オブジェクト (現在サポートされているオブジェクトはキューのみ) に対してイベントの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="7018e-105">In using WQL, an application retrieves an event type against a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a database, or a database object (the only object currently supported is queue).</span></span> <span data-ttu-id="7018e-106">WMI Provider for Server Events は、データベーススコープまたはオブジェクトスコープのイベント通知の対象データベースで作成されたイベント通知、またはサーバースコープのイベント通知の**master**データベースにクエリを変換します。</span><span class="sxs-lookup"><span data-stu-id="7018e-106">The WMI Provider for Server Events translates the query into an event notification that is created in the target database for database-scoped or object-scoped event notifications, or in the **master** database for server-scoped event notifications.</span></span>  
  
 <span data-ttu-id="7018e-107">たとえば、次の WQL クエリについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="7018e-107">For example, consider the following WQL query:</span></span>  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS WHERE DatabaseName = 'AdventureWorks'  
```  
  
 <span data-ttu-id="7018e-108">このクエリから、WMI プロバイダーは、このイベント通知と同等のものをターゲット サーバー上に生成しようとします。</span><span class="sxs-lookup"><span data-stu-id="7018e-108">From this query, the WMI Provider tries to produce the equivalent of this event notification on the target server:</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE   
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',  
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 <span data-ttu-id="7018e-109">WQL クエリ (`FROM`) の `DDL_DATABASE_LEVEL_EVENTS` 句の引数には、イベント通知を作成できる有効なイベントを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="7018e-109">The argument in the `FROM` clause of the WQL query (`DDL_DATABASE_LEVEL_EVENTS`) can be any valid event upon which an event notification can be created.</span></span> <span data-ttu-id="7018e-110">`SELECT` 句および `WHERE` 句の引数は、イベントまたはその親イベントに関連付けられたイベント プロパティを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="7018e-110">The arguments in the `SELECT` and `WHERE` clauses can specify any event property associated with an event or its parent event.</span></span> <span data-ttu-id="7018e-111">有効なイベントおよびイベントプロパティの一覧については、「[イベント通知 (データベースエンジン)](https://technet.microsoft.com/library/ms182602.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-111">For a list of valid events and event properties, see [Event Notifications (Database Engine)](https://technet.microsoft.com/library/ms182602.aspx).</span></span>  
  
 <span data-ttu-id="7018e-112">次の WQL 構文は、WMI Provider for Server Events によって明示的にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7018e-112">The following WQL syntax is supported explicitly by the WMI Provider for Server Events.</span></span> <span data-ttu-id="7018e-113">追加の WQL 構文を指定することもできますが、このプロバイダーに特有ではないため、代わりに WMI ホスト サービスによって解析されます。</span><span class="sxs-lookup"><span data-stu-id="7018e-113">Additional WQL syntax may be specified, but it is not specific to this provider and is parsed instead by the WMI host service.</span></span> <span data-ttu-id="7018e-114">WMI Query Language の詳細については、Microsoft Developer Network (MSDN) の WQL のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-114">For more information about the WMI Query Language, see the WQL documentation on the Microsoft Developer Network (MSDN).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7018e-115">構文</span><span class="sxs-lookup"><span data-stu-id="7018e-115">Syntax</span></span>  
  
```  
  
SELECT { event_property [ ,...n ] | * }  
FROM event_type   
WHERE where_condition  
```  
  
## <a name="arguments"></a><span data-ttu-id="7018e-116">引数</span><span class="sxs-lookup"><span data-stu-id="7018e-116">Arguments</span></span>  
 <span data-ttu-id="7018e-117">*event_property*</span><span class="sxs-lookup"><span data-stu-id="7018e-117">*event_property*</span></span>  
 <span data-ttu-id="7018e-118">イベントのプロパティ。</span><span class="sxs-lookup"><span data-stu-id="7018e-118">Is a property of an event.</span></span> <span data-ttu-id="7018e-119">例には、`PostTime`、`SPID`、および `LoginName` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7018e-119">Examples include `PostTime`, `SPID`, and `LoginName`.</span></span> <span data-ttu-id="7018e-120">「 [WMI Provider For Server Events のクラスとプロパティ](wmi-provider-for-server-events-classes-and-properties.md)」に記載されている各イベントを参照して、どのプロパティが保持されているかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7018e-120">Look up each event listed in [WMI Provider for Server Events Classes and Properties](wmi-provider-for-server-events-classes-and-properties.md) to determine which properties it holds.</span></span> <span data-ttu-id="7018e-121">たとえば、DDL_DATABASE_LEVEL_EVENTS イベントには、`DatabaseName` プロパティおよび `UserName` プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7018e-121">For example, the DDL_DATABASE_LEVEL_EVENTS event holds the `DatabaseName` and `UserName` properties.</span></span> <span data-ttu-id="7018e-122">また、親イベントから `SQLInstance` プロパティ、`LoginName` プロパティ、`PostTime` プロパティ、`SPID` プロパティ、および `ComputerName` プロパティを継承しています。</span><span class="sxs-lookup"><span data-stu-id="7018e-122">It also inherits the `SQLInstance`, `LoginName`, `PostTime`, `SPID`, and `ComputerName` properties from its parent events.</span></span>  
  
 <span data-ttu-id="7018e-123">**,** *...n*</span><span class="sxs-lookup"><span data-stu-id="7018e-123">**,** *...n*</span></span>  
 <span data-ttu-id="7018e-124">*Event_property*をコンマで区切って複数回照会できることを示します。</span><span class="sxs-lookup"><span data-stu-id="7018e-124">Indicates that *event_property* can be queried multiple times, separated by commas.</span></span>  
  
 \*  
 <span data-ttu-id="7018e-125">イベントに関連付けられたすべてのプロパティを照会することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7018e-125">Specifies that all properties associated with an event are queried.</span></span>  
  
 <span data-ttu-id="7018e-126">*event_type*</span><span class="sxs-lookup"><span data-stu-id="7018e-126">*event_type*</span></span>  
 <span data-ttu-id="7018e-127">イベント通知を作成できるイベント。</span><span class="sxs-lookup"><span data-stu-id="7018e-127">Is any event against which an event notification can be created.</span></span> <span data-ttu-id="7018e-128">使用できるイベントの一覧については、「 [WMI Provider For Server events のクラスとプロパティ](https://technet.microsoft.com/library/ms186449.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-128">For a list of available events, see [WMI Provider for Server Events Classes and Properties](https://technet.microsoft.com/library/ms186449.aspx).</span></span> <span data-ttu-id="7018e-129">イベントの*種類*名は、 *event_type*  |  create event notification を使用して手動でイベント通知を作成するときに指定できるのと同じ event_type*event_group*に対応していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-129">Note that *event type* names correspond to the same *event_type* | *event_group* that can be specified when you manually create an event notification by using CREATE EVENT NOTIFICATION.</span></span> <span data-ttu-id="7018e-130">イベントの*種類*の例としては、CREATE_TABLE、LOCK_DEADLOCK、DDL_USER_EVENTS、TRC_DATABASE などがあります。</span><span class="sxs-lookup"><span data-stu-id="7018e-130">Examples of *event type* include CREATE_TABLE, LOCK_DEADLOCK, DDL_USER_EVENTS, and TRC_DATABASE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7018e-131">DDL に似た操作を実行する一部のシステム ストアド プロシージャもイベント通知を起動することができます。</span><span class="sxs-lookup"><span data-stu-id="7018e-131">Certain system stored procedures that perform DDL-like operations can also fire event notifications.</span></span> <span data-ttu-id="7018e-132">イベント通知はテストして、実行されているシステム ストアド プロシージャに応答するかどうか、確認してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-132">Test your event notifications to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="7018e-133">たとえば、CREATE TYPE ステートメントと**sp_addtype**ストアドプロシージャはどちらも、CREATE_TYPE イベントで作成されたイベント通知を起動します。</span><span class="sxs-lookup"><span data-stu-id="7018e-133">For example, the CREATE TYPE statement and **sp_addtype** stored procedure will both fire an event notification that is created on a CREATE_TYPE event.</span></span> <span data-ttu-id="7018e-134">ただし、 **sp_rename**ストアドプロシージャでは、イベント通知は発生しません。</span><span class="sxs-lookup"><span data-stu-id="7018e-134">However, the **sp_rename** stored procedure does not fire any event notifications.</span></span> <span data-ttu-id="7018e-135">詳細については、「[DDL イベント](../triggers/ddl-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-135">For more information, see[DDL Events](../triggers/ddl-events.md).</span></span>  
  
 <span data-ttu-id="7018e-136">*where_condition*</span><span class="sxs-lookup"><span data-stu-id="7018e-136">*where_condition*</span></span>  
 <span data-ttu-id="7018e-137">*Event_property*名および論理演算子と比較演算子で構成される WHERE 句のクエリ述語です。</span><span class="sxs-lookup"><span data-stu-id="7018e-137">Is a WHERE clause query predicate made up of *event_property* names and logical and comparison operators.</span></span> <span data-ttu-id="7018e-138">*Where_condition*によって、対応するイベント通知が対象のデータベースに登録されるスコープが決まります。</span><span class="sxs-lookup"><span data-stu-id="7018e-138">The *where_condition* determines the scope in which the corresponding event notification is registered in the target database.</span></span> <span data-ttu-id="7018e-139">また、event_type のクエリを実行する特定のスキーマまたはオブジェクトを対象とするフィルターとしても機能し*ます。*</span><span class="sxs-lookup"><span data-stu-id="7018e-139">It can also act as a filter to target a particular schema or object from which to query *event_type.*</span></span> <span data-ttu-id="7018e-140">詳細については、このトピックで後述する「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-140">For more information, see the Remarks section later in this topic.</span></span>  
  
 <span data-ttu-id="7018e-141">`DatabaseName`、`SchemaName`、および `ObjectName` と共に使用できるのは、`=` オペランドのみです。</span><span class="sxs-lookup"><span data-stu-id="7018e-141">Only the `=` operand can be used together with `DatabaseName`, `SchemaName`, and `ObjectName`.</span></span> <span data-ttu-id="7018e-142">その他の式は、これらのイベント プロパティと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="7018e-142">Other expressions cannot be used with these event properties.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7018e-143">解説</span><span class="sxs-lookup"><span data-stu-id="7018e-143">Remarks</span></span>  
 <span data-ttu-id="7018e-144">WMI Provider for Server Events 構文の*where_condition*によって、次のことが決定されます。</span><span class="sxs-lookup"><span data-stu-id="7018e-144">The *where_condition* of the WMI Provider for Server Events syntax determines the following:</span></span>  
  
-   <span data-ttu-id="7018e-145">プロバイダーが指定された*event_type*を取得しようとするスコープ。サーバーレベル、データベースレベル、またはオブジェクトレベル (現在サポートされている唯一のオブジェクトは queue) です。</span><span class="sxs-lookup"><span data-stu-id="7018e-145">The scope by which the provider tries to retrieve the specified *event_type*: the server level, database level, or object level (the only object currently supported is queue).</span></span> <span data-ttu-id="7018e-146">最終的に、このスコープは対象データベースで作成されたイベント通知の種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="7018e-146">Ultimately, this scope determines the type of event notification created in the target database.</span></span> <span data-ttu-id="7018e-147">このプロセスは、イベント通知登録と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7018e-147">This process called event notification registration.</span></span>  
  
-   <span data-ttu-id="7018e-148">データベース、スキーマ、オブジェクトのうちの適切な登録場所。</span><span class="sxs-lookup"><span data-stu-id="7018e-148">The database, schema, and object, where appropriate, on which to register.</span></span>  
  
 <span data-ttu-id="7018e-149">WMI Provider for Server Events は、bottom-up および first-fit アルゴリズムを使用して、基になる EVENT NOTIFICATION に対してできるだけ小さなスコープを生成します。</span><span class="sxs-lookup"><span data-stu-id="7018e-149">The WMI Provider for Server Events uses a bottom-up, first-fit algorithm to produce the narrowest possible scope for the underlying EVENT NOTIFICATION.</span></span> <span data-ttu-id="7018e-150">アルゴリズムにより、サーバーの内部的な利用状況、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスと WMI ホスト プロセス間のネットワーク トラフィックが最小になるように試行されます。</span><span class="sxs-lookup"><span data-stu-id="7018e-150">The algorithm tries to minimize internal activity on the server and network traffic between the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the WMI host process.</span></span> <span data-ttu-id="7018e-151">プロバイダーは、FROM 句で指定された*event_type*と WHERE 句の条件を調べ、基になるイベント通知を最も狭いスコープで登録しようとします。</span><span class="sxs-lookup"><span data-stu-id="7018e-151">The provider examines the *event_type* specified in the FROM clause and the conditions in the WHERE clause, and tries to register the underlying EVENT NOTIFICATION with the narrowest possible scope.</span></span> <span data-ttu-id="7018e-152">プロバイダーが最も狭いスコープで登録できない場合は、登録が正常に終了するまで、順次より高いスコープでの登録が試行されます。</span><span class="sxs-lookup"><span data-stu-id="7018e-152">If the provider cannot register at the narrowest scope, it tries to register at successively higher scopes until a registration finally succeeds.</span></span> <span data-ttu-id="7018e-153">最も高いスコープ (サーバーレベル) に到達して失敗した場合、エラーがコンシューマーに返されます。</span><span class="sxs-lookup"><span data-stu-id="7018e-153">If it reaches the highest scope the server-level) and fails, it returns an error to the consumer.</span></span>  
  
 <span data-ttu-id="7018e-154">たとえば、WHERE 句で DatabaseName =**'** AdventureWorks **'** が指定されている場合、プロバイダーはデータベースにイベント通知を登録しようとし [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7018e-154">For example, if DatabaseName=**'** AdventureWorks **'** is specified in the WHERE clause, the provider tries to register an event notification in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="7018e-155">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースが存在し、呼び出し側クライアントが、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] のイベント通知を作成するために必要な権限を持っている場合、登録は正常に完了します。</span><span class="sxs-lookup"><span data-stu-id="7018e-155">If the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database exists and the calling client has the required permissions to create an event notification in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], the registration is successful.</span></span> <span data-ttu-id="7018e-156">それ以外の場合は、イベント通知をサーバー レベルで登録しようとします。</span><span class="sxs-lookup"><span data-stu-id="7018e-156">Otherwise, an attempt is made to register the event notification at the server level.</span></span> <span data-ttu-id="7018e-157">WMI クライアントが必要な権限を持っている場合、登録は正常に終了します。</span><span class="sxs-lookup"><span data-stu-id="7018e-157">The registration succeeds if the WMI client has the required permissions.</span></span> <span data-ttu-id="7018e-158">ただし、このシナリオでは、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースが作成されるまで、イベントはクライアントに返されません。</span><span class="sxs-lookup"><span data-stu-id="7018e-158">However, under this scenario, events are not returned to the client until the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database has been created.</span></span>  
  
 <span data-ttu-id="7018e-159">また、 *where_condition*をフィルターとして使用して、特定のデータベース、スキーマ、またはオブジェクトに対してクエリをさらに制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="7018e-159">The *where_condition* can also act as a filter to additionally limit the query to a specific database, schema, or object.</span></span> <span data-ttu-id="7018e-160">たとえば、次の WQL クエリについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="7018e-160">For example, consider the following WQL query:</span></span>  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
 <span data-ttu-id="7018e-161">登録プロセスの結果によっては、この WQL クエリは、データベース レベルまたはサーバー レベルのどちらかに登録されます。</span><span class="sxs-lookup"><span data-stu-id="7018e-161">Depending on the outcome of the registration process, this WQL query may be registered either at the database or server level.</span></span> <span data-ttu-id="7018e-162">ただし、サーバー レベルに登録された場合でも、プロバイダーは、`ALTER_TABLE` テーブルには適用されない `AdventureWorks.Sales.SalesOrderDetail` イベントを最終的にフィルターします。</span><span class="sxs-lookup"><span data-stu-id="7018e-162">However, even if it is registered at the server level, the provider ultimately filters any `ALTER_TABLE` events that do not apply to the `AdventureWorks.Sales.SalesOrderDetail` table.</span></span> <span data-ttu-id="7018e-163">つまり、プロバイダーは、この特定のテーブル上で発生した `ALTER_TABLE` イベントのプロパティのみを返します。</span><span class="sxs-lookup"><span data-stu-id="7018e-163">In other words, the provider returns only the properties of the `ALTER_TABLE` events that occur on that specific table.</span></span>  
  
 <span data-ttu-id="7018e-164">`DatabaseName='AW1'` OR `DatabaseName='AW2'` などの複合式が指定された場合、2 つの異なるイベント通知ではなく、サーバー スコープで 1 つのイベント通知の登録が試行されます。</span><span class="sxs-lookup"><span data-stu-id="7018e-164">If a compound expression such as `DatabaseName='AW1'` OR `DatabaseName='AW2'` is specified, an attempt is made to register a single event notification at the server scope instead of two separate event notifications.</span></span> <span data-ttu-id="7018e-165">呼び出し側クライアントが権限を持っている場合、登録は正常に終了します。</span><span class="sxs-lookup"><span data-stu-id="7018e-165">The registration succeeds if the calling client has permissions.</span></span>  
  
 <span data-ttu-id="7018e-166">`SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'`句でが指定されている場合は `WHERE` 、スキーマのオブジェクトに直接イベント通知を登録しようとし `Z` `X` ます。</span><span class="sxs-lookup"><span data-stu-id="7018e-166">If `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` are all specified in the `WHERE` clause, an attempt is made to register the event notification directly on object `Z` in schema `X`.</span></span> <span data-ttu-id="7018e-167">クライアントが権限を持っている場合、登録は正常に終了します。</span><span class="sxs-lookup"><span data-stu-id="7018e-167">The registration succeeds if the client has permissions.</span></span> <span data-ttu-id="7018e-168">現時点では、オブジェクトレベルのイベントはキューでのみサポートされており、QUEUE_ACTIVATION *event_type*に対してのみサポートされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-168">Note that currently, object-level events are supported only on queues, and only for the QUEUE_ACTIVATION *event_type*.</span></span>  
  
 <span data-ttu-id="7018e-169">ある特定のスコープでは、すべてのイベントを照会できるわけではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-169">Note that not all events can be queried at any particular scope.</span></span> <span data-ttu-id="7018e-170">たとえば、Lock_Deadlock など、トレース イベント上の WQL クエリ、または TRC_LOCKS などのトレース イベント グループは、サーバー レベルでのみ登録できます。</span><span class="sxs-lookup"><span data-stu-id="7018e-170">For example, a WQL query on a trace event such as Lock_Deadlock, or a trace event group such as TRC_LOCKS, can only be registered at the server level.</span></span> <span data-ttu-id="7018e-171">同様に、CREATE_ENDPOINT イベントおよび DDL_ENDPOINT_EVENTS イベント グループも、サーバー レベルでのみ登録できます。</span><span class="sxs-lookup"><span data-stu-id="7018e-171">Similarly, the CREATE_ENDPOINT event and the DDL_ENDPOINT_EVENTS event group can also be registered only at the server level.</span></span> <span data-ttu-id="7018e-172">イベントを登録するための適切なスコープの詳細については、「[イベント通知のデザイン](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7018e-172">For more information about the appropriate scope for registering events, see [Designing Event Notifications](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx).</span></span> <span data-ttu-id="7018e-173">*Event_type*をサーバーレベルでしか登録できない WQL クエリを登録しようとすると、常にサーバーレベルで作成されます。</span><span class="sxs-lookup"><span data-stu-id="7018e-173">An attempt to register a WQL query whose *event_type* can only be registered at the server level is always made at the server level.</span></span> <span data-ttu-id="7018e-174">WMI クライアントが権限を持っている場合、登録は正常に終了します。</span><span class="sxs-lookup"><span data-stu-id="7018e-174">Registration succeeds if the WMI client has permissions.</span></span> <span data-ttu-id="7018e-175">それ以外の場合は、クライアントにエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="7018e-175">Otherwise, an error is returned to the client.</span></span> <span data-ttu-id="7018e-176">ただし、WHERE 句は、イベントに対応するプロパティに基づいたサーバー レベル イベントに対するフィルターとして使用できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7018e-176">In some cases, however, you can still use the WHERE clause as a filter for server-level events based on the properties that correspond to the event.</span></span> <span data-ttu-id="7018e-177">たとえば、多くのトレース イベントに含まれている `DatabaseName` プロパティは、WHERE 句でフィルターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="7018e-177">For example, many trace events have a `DatabaseName` property that can be used in the WHERE clause as a filter.</span></span>  
  
 <span data-ttu-id="7018e-178">サーバースコープのイベント通知は、 **master**データベースに作成され、 [server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)カタログビューを使用してメタデータを照会できます。</span><span class="sxs-lookup"><span data-stu-id="7018e-178">Server-scoped event notifications are created in the **master** database and can be queried for metadata by using the [sys.server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="7018e-179">データベーススコープまたはオブジェクトスコープのイベント通知は、指定されたデータベースに作成され、 [event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)カタログビューを使用してメタデータを照会できます。</span><span class="sxs-lookup"><span data-stu-id="7018e-179">Database-scoped or object-scoped event notifications are created in the specified database and can be queried for metadata by using the [sys.event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql) catalog view.</span></span> <span data-ttu-id="7018e-180">(カタログ ビューのプレフィックスには、対応するデータベース名を使用する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="7018e-180">(You must prefix the catalog view with the corresponding database name.)</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7018e-181">例</span><span class="sxs-lookup"><span data-stu-id="7018e-181">Examples</span></span>  
  
### <a name="a-querying-for-events-at-the-server-scope"></a><span data-ttu-id="7018e-182">A.</span><span class="sxs-lookup"><span data-stu-id="7018e-182">A.</span></span> <span data-ttu-id="7018e-183">サーバー スコープのイベントを照会する</span><span class="sxs-lookup"><span data-stu-id="7018e-183">Querying for events at the server scope</span></span>  
 <span data-ttu-id="7018e-184">次の WQL クエリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス上で発生する `SERVER_MEMORY_CHANGE` トレース イベントのイベント プロパティをすべて取得します。</span><span class="sxs-lookup"><span data-stu-id="7018e-184">The following WQL query retrieves all event properties for any `SERVER_MEMORY_CHANGE` trace event that occurs on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
SELECT * FROM SERVER_MEMORY_CHANGE  
```  
  
### <a name="b-querying-for-events-at-the-database-scope"></a><span data-ttu-id="7018e-185">B.</span><span class="sxs-lookup"><span data-stu-id="7018e-185">B.</span></span> <span data-ttu-id="7018e-186">データベース スコープのイベントを照会する</span><span class="sxs-lookup"><span data-stu-id="7018e-186">Querying for events at the database scope</span></span>  
 <span data-ttu-id="7018e-187">次の WQL クエリは、`AdventureWorks` データベース内で発生し、`DDL_DATABASE_LEVEL_EVENTS` イベント グループに存在するイベントの特定のイベント プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="7018e-187">The following WQL query retrieves specific event properties for any event that occurs in the `AdventureWorks` database and exists under the `DDL_DATABASE_LEVEL_EVENTS` event group.</span></span>  
  
```  
SELECT SPID, SQLInstance, DatabaseName FROM DDL_DATABASE_LEVEL_EVENTS   
WHERE DatabaseName = 'AdventureWorks'   
```  
  
### <a name="c-querying-for-events-at-the-database-scope-filtering-by-schema-and-object"></a><span data-ttu-id="7018e-188">C.</span><span class="sxs-lookup"><span data-stu-id="7018e-188">C.</span></span> <span data-ttu-id="7018e-189">データベース スコープのイベントを照会し、スキーマおよびオブジェクトでフィルター処理を行う</span><span class="sxs-lookup"><span data-stu-id="7018e-189">Querying for events at the database scope, filtering by schema and object</span></span>  
 <span data-ttu-id="7018e-190">次のクエリは、テーブル `ALTER_TABLE` 上で発生する `AdventureWorks.Sales.SalesOrderDetail` イベントのイベント プロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="7018e-190">The following query retrieves all event properties for any `ALTER_TABLE` event that occurs on table `AdventureWorks.Sales.SalesOrderDetail`.</span></span>  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
## <a name="see-also"></a><span data-ttu-id="7018e-191">参照</span><span class="sxs-lookup"><span data-stu-id="7018e-191">See Also</span></span>  
 <span data-ttu-id="7018e-192">[WMI Provider for Server Events の概念](https://technet.microsoft.com/library/ms180560.aspx) </span><span class="sxs-lookup"><span data-stu-id="7018e-192">[WMI Provider for Server Events Concepts](https://technet.microsoft.com/library/ms180560.aspx) </span></span>  
 [<span data-ttu-id="7018e-193">イベント通知 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="7018e-193">Event Notifications (Database Engine)</span></span>](https://technet.microsoft.com/library/ms182602.aspx)  
  
  
