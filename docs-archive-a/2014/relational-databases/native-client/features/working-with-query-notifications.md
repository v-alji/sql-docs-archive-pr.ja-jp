---
title: クエリ通知の操作 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], query notifications
- rowsets [SQL Server], notifications
- SQL Server Native Client, query notifications
- notifications [SQL Server Native Client]
- query notifications [SQL Server], SQL Server Native Client
- canceling rowset changes
- IRowsetNotify interface
- SQLNCLI, query notifications
- SQL Server Native Client OLE DB provider, query notifications
- consumer notification for rowset changes [SQL Server Native Client]
ms.assetid: 2f906fff-5ed9-4527-9fd3-9c0d27c3dff7
author: rothja
ms.author: jroth
ms.openlocfilehash: ba30bfc8df05a55e297ae8fcb8e2253de57e3ca6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643272"
---
# <a name="working-with-query-notifications"></a><span data-ttu-id="f3b02-102">クエリ通知の操作</span><span class="sxs-lookup"><span data-stu-id="f3b02-102">Working with Query Notifications</span></span>
  <span data-ttu-id="f3b02-103">クエリ通知は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で導入されました。</span><span class="sxs-lookup"><span data-stu-id="f3b02-103">Query notifications were introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="f3b02-104">クエリ通知は [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] に導入された Service Broker インフラストラクチャに基づいて構築されており、データが変更されたときにクエリ通知を使用してアプリケーションに通知できます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-104">Built upon the Service Broker infrastructure introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="f3b02-105">この機能は、Web アプリケーションなど、データベースから情報のキャッシュを提供し、ソース データが変更された場合に通知を必要とするアプリケーションに特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-105">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="f3b02-106">クエリ通知を使用すると、クエリの基になるデータが変更された場合に、指定されたタイムアウト期間内に通知を要求することができます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-106">Query notifications allow you to request notification within a specified time-out period when the underlying data of a query changes.</span></span> <span data-ttu-id="f3b02-107">通知を要求する際は、サービス名、メッセージ テキスト、サーバーのタイムアウト値などの通知オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-107">The request for notification specifies the notification options, which include the service name, message text, and time-out value to the server.</span></span> <span data-ttu-id="f3b02-108">通知は Service Broker キューを使用して配信されます。アプリケーションではこのキューにポーリングして、使用可能な通知を確認できます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-108">Notifications are delivered through a Service Broker queue that applications may poll for available notifications.</span></span>  
  
 <span data-ttu-id="f3b02-109">クエリ通知オプションの構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-109">The syntax of the query notifications options string is:</span></span>  
  
 `service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`  
  
 <span data-ttu-id="f3b02-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-110">For example:</span></span>  
  
 `service=mySSBService;local database=mydb`  
  
 <span data-ttu-id="f3b02-111">アプリケーションで通知サブスクリプションが作成された直後にそのアプリケーションが終了した場合、通知サブスクリプションを開始するプロセスが終了しても、通知サブスクリプションは有効です。</span><span class="sxs-lookup"><span data-stu-id="f3b02-111">Notification subscriptions outlive the process that initiates them, as an application may create a notification subscription and then terminate.</span></span> <span data-ttu-id="f3b02-112">通知サブスクリプションが有効なままなので、通知サブスクリプションの作成時に指定したタイムアウト期間内にデータが変更されると、通知が行われます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-112">The subscription remains valid, and the notification will occur if the data changes within the time-out period specified when the subscription was created.</span></span> <span data-ttu-id="f3b02-113">通知は、実行されるクエリ、通知オプション、およびメッセージ テキストによって識別されます。また、通知のタイムアウト値を 0 に設定して通知をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-113">A notification is identified by the query executed, the notification options, and the message text, and may be cancelled by setting its time-out value to zero.</span></span>  
  
 <span data-ttu-id="f3b02-114">通知は、一度だけ送信されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-114">Notifications are sent only once.</span></span> <span data-ttu-id="f3b02-115">データ変更の通知を連続して行う場合は、各通知が処理された後にクエリを再実行して、新しいサブスクリプションを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-115">For continuous notification of data change, a new subscription must be created by re-executing the query after each notification is processed.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="f3b02-116">ネイティブクライアントアプリケーションは、通常、通知 [!INCLUDE[tsql](../../../includes/tsql-md.md)] オプションで指定されたサービスに関連付けられているキューから通知を読み取るために、 [receive](/sql/t-sql/statements/receive-transact-sql)コマンドを使用して通知を受信します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-116">Native Client applications typically receive notifications by using the [!INCLUDE[tsql](../../../includes/tsql-md.md)] [RECEIVE](/sql/t-sql/statements/receive-transact-sql) command to read notifications from the queue associated with the service specified in the notification options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3b02-117">通知を必要とするクエリ内のテーブル名は、`dbo.myTable` のように、修飾された名前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-117">Table names must be qualified in queries for which notification is required, for example, `dbo.myTable`.</span></span> <span data-ttu-id="f3b02-118">テーブル名は、2 つの部分を持つ修飾名にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-118">Table names must be qualified with two part names.</span></span> <span data-ttu-id="f3b02-119">3 つまたは 4 つの部分を持つ名前を使用すると、サブスクリプションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-119">Subscription is invalid if three- or four-part names are used.</span></span>  
  
 <span data-ttu-id="f3b02-120">この通知インフラストラクチャは、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入されたキュー処理機能に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="f3b02-120">The notification infrastructure is built on top of a queuing feature introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="f3b02-121">一般的に、サーバーで生成された通知は、後で処理するためにキュー経由で送信されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-121">In general, notifications generated at the server are sent through these queues to be processed later.</span></span>  
  
 <span data-ttu-id="f3b02-122">クエリ通知を使用するには、クエリとサービスがサーバー上に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-122">To use query notifications a queue and a service must exist on the server.</span></span> <span data-ttu-id="f3b02-123">次のような [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用して、クエリやサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-123">These can be created using [!INCLUDE[tsql](../../../includes/tsql-md.md)] similar to the following:</span></span>  
  
```  
CREATE QUEUE myQueue  
CREATE SERVICE myService ON QUEUE myQueue   
  
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f3b02-124">上記のように、サービスでは定義済みのコントラクト `https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-124">The service must use the predefined contract `https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification` as shown above.</span></span>  
  
## <a name="sql-server-native-client-ole-db-provider"></a><span data-ttu-id="f3b02-125">SQL Server Native Client OLE DB プロバイダー</span><span class="sxs-lookup"><span data-stu-id="f3b02-125">SQL Server Native Client OLE DB Provider</span></span>  
 <span data-ttu-id="f3b02-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、行セットの変更に関するコンシューマー通知をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f3b02-126">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer notification on rowset modification.</span></span> <span data-ttu-id="f3b02-127">コンシューマーは、行セットの変更のすべてのフェーズで、任意の変更が試行されたときに通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-127">The consumer receives notification at every phase of rowset modification and on any attempted change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3b02-128">**ICommand:: Execute**を使用してサーバーに通知クエリを渡すことは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでクエリ通知をサブスクライブする唯一の有効な方法です。</span><span class="sxs-lookup"><span data-stu-id="f3b02-128">Passing a notifications query to the server with **ICommand::Execute** is the only valid way to subscribe to query notifications with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
### <a name="the-dbpropset_sqlserverrowset-property-set"></a><span data-ttu-id="f3b02-129">DBPROPSET_SQLSERVERROWSET プロパティ セット</span><span class="sxs-lookup"><span data-stu-id="f3b02-129">The DBPROPSET_SQLSERVERROWSET Property Set</span></span>  
 <span data-ttu-id="f3b02-130">OLE DB を使用したクエリ通知をサポートするために、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、DBPROPSET_SQLSERVERROWSET プロパティセットに次の新しいプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-130">In order to support query notifications through OLE DB, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client adds the following new properties to the DBPROPSET_SQLSERVERROWSET property set.</span></span>  
  
|<span data-ttu-id="f3b02-131">名前</span><span class="sxs-lookup"><span data-stu-id="f3b02-131">Name</span></span>|<span data-ttu-id="f3b02-132">Type</span><span class="sxs-lookup"><span data-stu-id="f3b02-132">Type</span></span>|<span data-ttu-id="f3b02-133">説明</span><span class="sxs-lookup"><span data-stu-id="f3b02-133">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="f3b02-134">SSPROP_QP_NOTIFICATION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f3b02-134">SSPROP_QP_NOTIFICATION_TIMEOUT</span></span>|<span data-ttu-id="f3b02-135">VT_UI4</span><span class="sxs-lookup"><span data-stu-id="f3b02-135">VT_UI4</span></span>|<span data-ttu-id="f3b02-136">クエリ通知をアクティブのままにしておく秒数。</span><span class="sxs-lookup"><span data-stu-id="f3b02-136">The number of seconds that the query notification is to remain active.</span></span><br /><br /> <span data-ttu-id="f3b02-137">既定値は 432,000 秒 (5 日) です。</span><span class="sxs-lookup"><span data-stu-id="f3b02-137">The default is 432000 seconds (5 days).</span></span> <span data-ttu-id="f3b02-138">最小値は 1 秒であり、最大値は 2^31-1 秒です。</span><span class="sxs-lookup"><span data-stu-id="f3b02-138">The minimum value is 1 second, and the maximum value is 2^31-1 seconds.</span></span>|  
|<span data-ttu-id="f3b02-139">SSPROP_QP_NOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="f3b02-139">SSPROP_QP_NOTIFICATION_MSGTEXT</span></span>|<span data-ttu-id="f3b02-140">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="f3b02-140">VT_BSTR</span></span>|<span data-ttu-id="f3b02-141">通知のメッセージ テキスト。</span><span class="sxs-lookup"><span data-stu-id="f3b02-141">The message text of the notification.</span></span> <span data-ttu-id="f3b02-142">これはユーザーが定義するため、あらかじめ定義済みの書式はありません。</span><span class="sxs-lookup"><span data-stu-id="f3b02-142">This is user defined, and has no predefined format.</span></span><br /><br /> <span data-ttu-id="f3b02-143">既定では、文字列は空です。</span><span class="sxs-lookup"><span data-stu-id="f3b02-143">By default, the string is empty.</span></span> <span data-ttu-id="f3b02-144">1 ～ 2,000 文字を使用してメッセージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-144">You can specify a message using 1-2000 characters.</span></span>|  
|<span data-ttu-id="f3b02-145">SSPROP_QP_NOTIFICATION_OPTIONS</span><span class="sxs-lookup"><span data-stu-id="f3b02-145">SSPROP_QP_NOTIFICATION_OPTIONS</span></span>|<span data-ttu-id="f3b02-146">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="f3b02-146">VT_BSTR</span></span>|<span data-ttu-id="f3b02-147">クエリ通知オプション。</span><span class="sxs-lookup"><span data-stu-id="f3b02-147">The query notification options.</span></span> <span data-ttu-id="f3b02-148">これらは、*名前*と値の構文を持つ文字列で指定され = *value*ます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-148">These are specified in a string with *name*=*value* syntax.</span></span> <span data-ttu-id="f3b02-149">ユーザーがサービスを作成して、キューから通知を読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-149">The user is responsible for creating the service and reading notifications off of the queue.</span></span><br /><br /> <span data-ttu-id="f3b02-150">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="f3b02-150">The default is an empty string.</span></span>|  
  
 <span data-ttu-id="f3b02-151">ステートメントがユーザー トランザクションで実行されたか自動コミットで実行されたか、また、ステートメントが実行されたトランザクションがコミットされたかロールバックされたかに関係なく、通知サブスクリプションは必ずコミットされます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-151">The notification subscription is always committed, regardless of whether the statement ran in a user transaction or in auto commit or whether the transaction in which the statement ran committed or rolled back.</span></span> <span data-ttu-id="f3b02-152">サーバー通知は、次の無効通知条件のいずれかが最初に発生したときに起動します。通知条件は、基になるデータまたはスキーマが変更されるか、タイムアウト期間に到達するかです。</span><span class="sxs-lookup"><span data-stu-id="f3b02-152">The server notification fires upon any of the following invalid notification conditions: change of underlying data or schema, or when the timeout period is reached; whichever is first.</span></span> <span data-ttu-id="f3b02-153">通知登録は、起動直後に削除されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-153">Notification registrations are deleted as soon as they are fired.</span></span> <span data-ttu-id="f3b02-154">したがって、通知を受け取った後も引き続き更新するには、アプリケーションで再度サブスクライブする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-154">Hence upon receiving notifications, the application must subscribe again in case they want to get further updates.</span></span>  
  
 <span data-ttu-id="f3b02-155">他の接続またはスレッドは、接続先キューに通知があるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-155">Another connection or thread can check the destination queue for notifications.</span></span> <span data-ttu-id="f3b02-156">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-156">For example:</span></span>  
  
```  
WAITFOR (RECEIVE * FROM MyQueue);   // Where MyQueue is the queue name.   
```  
  
 <span data-ttu-id="f3b02-157">SELECT \* を指定してもキューのエントリは削除されませんが、RECEIVE \* FROM を指定すると削除されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-157">Note that SELECT \* does not delete the entry from the Queue, however RECEIVE \* FROM does.</span></span> <span data-ttu-id="f3b02-158">このため、キューが空の場合は、サーバー スレッドが保留されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-158">This stalls a server thread if the queue is empty.</span></span> <span data-ttu-id="f3b02-159">呼び出し時にキュー エントリがあれば、それらがすぐに返されます。それ以外の場合、呼び出しは、キュー エントリが作成されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-159">If there are queue entries at the time of the call, they are returned immediately; otherwise the call waits until a queue entry is made.</span></span>  
  
```  
RECEIVE * FROM MyQueue  
```  
  
 <span data-ttu-id="f3b02-160">キューが空の場合、このステートメントは空の結果セットを直ちに返します。それ以外の場合、すべてのキュー通知を返します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-160">This statement immediately returns an empty result set if the queue is empty; otherwise it returns all queue notifications.</span></span>  
  
 <span data-ttu-id="f3b02-161">SSPROP_QP_NOTIFICATION_MSGTEXT と SSPROP_QP_NOTIFICATION_OPTIONS が NULL 以外で、かつ空ではない場合、上記で定義された 3 つのプロパティを含んでいるクエリ通知 TDS ヘッダーが、コマンドが実行されるたびにサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-161">If SSPROP_QP_NOTIFICATION_MSGTEXT and SSPROP_QP_NOTIFICATION_OPTIONS are non-NULL and non-empty, the query notifications TDS header containing the three properties defined above are sent to the server with each execution of the command.</span></span> <span data-ttu-id="f3b02-162">どちらかが NULL (または空) の場合、クエリ通知 TDS ヘッダーは送信されず、DB_E_ERRORSOCCURED (または、プロパティが両方とも省略可能に設定されている場合は DB_S_ERRORSOCCURED) が発生し、状態値が DBPROPSTATUS_BADVALUE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-162">If either of them is null (or empty), the header is not sent and DB_E_ERRORSOCCURRED is raised, (or DB_S_ERRORSOCCURRED if the properties are both marked as optional), and the status value is set to DBPROPSTATUS_BADVALUE.</span></span> <span data-ttu-id="f3b02-163">実行または準備の時点で検証が行われます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-163">The validation occurs on Execute/Prepare.</span></span> <span data-ttu-id="f3b02-164">同様に、クエリ通知プロパティが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] への接続に対して設定されている場合は、DB_S_ERRORSOCCURED が発生します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-164">Similarly, DB_S_ERRORSOCCURED is raised when the query notification properties are set for connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="f3b02-165">この場合の状態値は DBPROPSTATUS_NOTSUPPORTED です。</span><span class="sxs-lookup"><span data-stu-id="f3b02-165">The status value in this case is DBPROPSTATUS_NOTSUPPORTED.</span></span>  
  
 <span data-ttu-id="f3b02-166">サブスクリプションが開始されても、後続のメッセージが正常に配信されるかどうかは保証されません。</span><span class="sxs-lookup"><span data-stu-id="f3b02-166">Initiating a subscription does not guarantee that subsequent messages will be successfully delivered.</span></span> <span data-ttu-id="f3b02-167">また、指定されたサーバー名の妥当性に関するチェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="f3b02-167">In addition, no check is made as to the validity of the service name specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3b02-168">ステートメントの準備フェーズではサブスクリプションが開始されることはありません。サブスクリプションは、ステートメントを実行したときにのみ開始されます。また、OLE DB Core Services を使用してもクエリ通知は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="f3b02-168">Preparing statements will never cause the subscription to be initiated; only statement execution will achieve this and query notifications are not impacted by the use of OLE DB core services.</span></span>  
  
 <span data-ttu-id="f3b02-169">DBPROPSET_SQLSERVERROWSET プロパティセットの詳細については、「[行セットのプロパティと動作](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3b02-169">For more information about the DBPROPSET_SQLSERVERROWSET property set, see [Rowset Properties and Behaviors](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md).</span></span>  
  
## <a name="sql-server-native-client-odbc-driver"></a><span data-ttu-id="f3b02-170">SQL Server Native Client ODBC ドライバー</span><span class="sxs-lookup"><span data-stu-id="f3b02-170">SQL Server Native Client ODBC Driver</span></span>  
 <span data-ttu-id="f3b02-171">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md)関数と[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)関数に3つの新しい属性を追加することによって、クエリ通知をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f3b02-171">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports query notifications through the addition of three new attributes to the [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) and [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) functions:</span></span>  
  
-   <span data-ttu-id="f3b02-172">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="f3b02-172">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span></span>  
  
-   <span data-ttu-id="f3b02-173">SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS</span><span class="sxs-lookup"><span data-stu-id="f3b02-173">SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS</span></span>  
  
-   <span data-ttu-id="f3b02-174">SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f3b02-174">SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT</span></span>  
  
 <span data-ttu-id="f3b02-175">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT と SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS が NULL 以外の場合、上記で定義された 3 つの属性を含むクエリ通知 TDS ヘッダーが、コマンドを実行するたびにサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-175">If SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT and SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS are not NULL, the query notifications TDS header containing the three attributes defined above will be sent to the server each time the command is executed.</span></span> <span data-ttu-id="f3b02-176">どちらかが NULL の場合、クエリ通知 TDS ヘッダーは送信されず、SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-176">If either of them is null, the header is not sent, and SQL_SUCCESS_WITH_INFO is returned.</span></span> <span data-ttu-id="f3b02-177">検証は、 [SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)、 **SqlExecDirect**、および**sqlexecute**に対して行われ、属性が有効でない場合はすべて失敗します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-177">The validation occurs on [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360), **SqlExecDirect**, and **SqlExecute**, all of which fail if the attributes are not valid.</span></span> <span data-ttu-id="f3b02-178">同様に、これらのクエリ通知属性が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] に対して設定されている場合、SQL_SUCCESS_WITH_INFO によって実行が失敗します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-178">Similarly, when these query notification attributes are set for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the execution fails with SQL_SUCCESS_WITH_INFO.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3b02-179">ステートメントの準備段階では、サブスクリプションが開始されることはありません。サブスクリプションを開始できるのは、ステートメントを実行したときのみです。</span><span class="sxs-lookup"><span data-stu-id="f3b02-179">Prepare statements will never cause the subscription to be initiated; subscription can be initiated by statement execution.</span></span>  
  
## <a name="special-cases-and-restrictions"></a><span data-ttu-id="f3b02-180">特別なケースおよび制限</span><span class="sxs-lookup"><span data-stu-id="f3b02-180">Special Cases and Restrictions</span></span>  
 <span data-ttu-id="f3b02-181">通知では、次のデータ型がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f3b02-181">The following data types are not supported for notifications:</span></span>  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
 <span data-ttu-id="f3b02-182">これらのいずれかのデータ型を返すクエリに対して通知要求を作成すると、通知サブスクリプションが不可能であるという通知が、すぐに発行されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-182">If a notification request is made for a query which returns any of these types, the notification fires immediately, specifying that notification subscription was not possible.</span></span>  
  
 <span data-ttu-id="f3b02-183">バッチまたはストアド プロシージャに対するサブスクリプション要求を作成すると、そのバッチまたはストアド プロシージャ内で実行される各ステートメントに対して、別個のサブスクリプション要求が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-183">If a subscription request is made for a batch or stored procedure, a separate subscription request is made for each statement executed within the batch or stored procedure.</span></span> <span data-ttu-id="f3b02-184">EXECUTE ステートメントは通知を登録せず、実行されるコマンドへ通知要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-184">EXECUTE statements will not register a notification, but will send the notification request to the executed command.</span></span> <span data-ttu-id="f3b02-185">バッチの場合、実行されるステートメントに対してコンテキストが適用され、さらに同様のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="f3b02-185">If it is a batch, the context will be applied to the executed statements and the same rules described above apply.</span></span>  
  
 <span data-ttu-id="f3b02-186">同じデータベースコンテキストで同じユーザーによって送信され、同じテンプレート、同じパラメーター値、同じ通知 ID、および既存のアクティブなサブスクリプションと同じ配信場所を持つ通知のクエリを送信すると、既存のサブスクリプションが更新され、指定された新しいタイムアウトがリセットされます。これは、同一のクエリに対して通知が要求されると、1つの通知のみが送信されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f3b02-186">Submission of a query for notification that was submitted by the same user under the same database context and has the same template, same parameter values, same notification ID, and same delivery location of an existing active subscription, will renew the existing subscription, resetting the new specified time-out. This means that if notification is requested for identical queries, only one notification will be sent.</span></span> <span data-ttu-id="f3b02-187">バッチ内で重複するクエリや、ストアド プロシージャ内で複数回呼び出されたクエリにも、これが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="f3b02-187">This would apply to a query duplicated in a batch, or a query in a stored procedure that was called multiple times.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b02-188">参照</span><span class="sxs-lookup"><span data-stu-id="f3b02-188">See Also</span></span>  
 [<span data-ttu-id="f3b02-189">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="f3b02-189">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
