---
title: SMO イベントの処理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- events [SMO]
- SQL Server Management Objects, events
- SMO [SQL Server], events
- events [SMO], about events
ms.assetid: b4f120dd-ba78-46ff-99c5-e47effac8544
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7ea438142ac283c5ad19670fa827b5e248e80f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644954"
---
# <a name="handling-smo-events"></a><span data-ttu-id="1c808-102">SMO イベントの処理</span><span class="sxs-lookup"><span data-stu-id="1c808-102">Handling SMO Events</span></span>
  <span data-ttu-id="1c808-103">サーバー イベントの型には、イベント ハンドラーおよび <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用してサブスクライブできるものがあります。</span><span class="sxs-lookup"><span data-stu-id="1c808-103">There are server event types that can be subscribed to by using an event handler and the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
 <span data-ttu-id="1c808-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) のインスタンス クラスの多くは、サーバー上で特定のアクションが発生した場合にイベントをトリガーすることができます。</span><span class="sxs-lookup"><span data-stu-id="1c808-104">Many of the instance classes in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) can trigger events when certain actions on the server occur.</span></span>  
  
 <span data-ttu-id="1c808-105">これらのイベントは、イベント ハンドラーを設定し、関連するイベントをサブスクライブすることで、プログラムを使用して処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1c808-105">These events can be handled programmatically by setting up an event handler and subscribing to the associated events.</span></span> <span data-ttu-id="1c808-106">サブスクリプションは SMO クライアント プログラムの終了時にすべて削除されるため、この種類のイベント ハンドリングは一時的なものです。</span><span class="sxs-lookup"><span data-stu-id="1c808-106">This type of event handling is transient because all the subscriptions are removed when the SMO client program exits.</span></span>  
  
## <a name="connectioncontext-event-handling"></a><span data-ttu-id="1c808-107">ConnectionContext イベント ハンドリング</span><span class="sxs-lookup"><span data-stu-id="1c808-107">ConnectionContext Event Handling</span></span>  
 <span data-ttu-id="1c808-108"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトは複数のイベントの種類をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="1c808-108">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object supports several event types.</span></span> <span data-ttu-id="1c808-109">イベント プロパティは、適切なイベント ハンドラーのインスタンスに対して設定されている必要があります。また、イベント ハンドラー オブジェクトは、イベントを処理するプロテクト関数として定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c808-109">The event property must be set to an instance of an appropriate event handler, and the event handler object must be defined as a protected function that handles the event.</span></span>  
  
## <a name="event-subscription"></a><span data-ttu-id="1c808-110">イベント サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="1c808-110">Event Subscription</span></span>  
 <span data-ttu-id="1c808-111">イベントを処理するには、イベント ハンドラー クラスを作成し、イベント ハンドラー クラスのインスタンスの作成して、イベント ハンドラーを親オブジェクトに割り当てて、イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="1c808-111">You handle events by writing an event handler class, creating an instance of it, assigning the event handler to the parent object, and then subscribing to the event.</span></span>  
  
 <span data-ttu-id="1c808-112">イベントを処理するためには、イベント ハンドラー クラスが作成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c808-112">An event handler class must be written to handle events.</span></span> <span data-ttu-id="1c808-113">イベント ハンドラー クラスは、2 つ以上のイベント ハンドラー関数を含めることができます。また、処理されるイベントに対してインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c808-113">The event handler class can contain more than one event handler function, and must be installed for the events to be handled.</span></span> <span data-ttu-id="1c808-114">イベントハンドラー関数は、イベントに関する情報をレポートするために使用できる*ServerEventNotificatificationArgs*パラメーターから、イベントに関する情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1c808-114">The event handler functions receive information about the event from the *ServerEventNotificatificationArgs* parameter that can be used to report information about the event.</span></span>  
  
 <span data-ttu-id="1c808-115">処理できるデータベースおよびサーバーイベントの種類は、クラスとクラスに一覧表示され <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet> ます。</span><span class="sxs-lookup"><span data-stu-id="1c808-115">The types of database and server events that can be handled are listed in the <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> class and the <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet>class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c808-116">例</span><span class="sxs-lookup"><span data-stu-id="1c808-116">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-basic"></a><span data-ttu-id="1c808-117">Visual Basic でのイベント ハンドラーの登録およびイベント ハンドリングのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="1c808-117">Registering Event Handlers and Subscribing to Event Handling in Visual Basic</span></span>  
 <span data-ttu-id="1c808-118">このコード例では、イベント ハンドラーを設定する方法およびデータベース イベントをサブスクライブする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1c808-118">This code example shows how to set up the event handler, and how to subscribe to the database events.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEvents1](SMO How to#SMO_VBEvents1)]  -->  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-c"></a><span data-ttu-id="1c808-119">Visual C# でのイベント ハンドラーの登録およびイベント ハンドリングのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="1c808-119">Registering Event Handlers and Subscribing to Event Handling in Visual C#</span></span>  
 <span data-ttu-id="1c808-120">このコード例では、イベント ハンドラーを設定する方法およびデータベース イベントをサブスクライブする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1c808-120">This code example shows how to set up the event handler, and how to subscribe to the database events.</span></span>  
  
```  
//Create an event handler subroutine that runs when a table is created.   
private void MyCreateEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been added to the AdventureWorks2012 database.");   
}   
//Create an event handler subroutine that runs when a table is deleted.   
private void MyDropEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been dropped from the AdventureWorks2012 database.");   
}   
public void Main()   
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Create a database event set that contains the CreateTable event only.   
DatabaseEventSet databaseCreateEventSet = new DatabaseEventSet();   
databaseCreateEventSet.CreateTable = true;   
//Create a server event handler and set it to the first event handler subroutine.   
ServerEventHandler serverCreateEventHandler;   
serverCreateEventHandler = new ServerEventHandler(MyCreateEventHandler);   
//Subscribe to the first server event handler when a CreateTable event occurs.   
db.Events.SubscribeToEvents(databaseCreateEventSet, serverCreateEventHandler);   
    //Create a database event set that contains the DropTable event only.   
DatabaseEventSet databaseDropEventSet = new DatabaseEventSet();   
databaseDropEventSet.DropTable = true;   
//Create a server event handler and set it to the second event handler subroutine.   
ServerEventHandler serverDropEventHandler;   
serverDropEventHandler = new ServerEventHandler(MyDropEventHandler);   
//Subscribe to the second server event handler when a DropTable event occurs.   
db.Events.SubscribeToEvents(databaseDropEventSet, serverDropEventHandler);   
//Start event handling.   
db.Events.StartEvents();   
//Create a table on the database.   
Table tb;   
tb = new Table(db, "Test_Table");   
Column mycol1;   
mycol1 = new Column(tb, "Name", DataType.NChar(50));   
mycol1.Collation = "Latin1_General_CI_AS";   
mycol1.Nullable = true;   
tb.Columns.Add(mycol1);   
tb.Create();   
//Remove the table.   
tb.Drop();   
//Wait until the events have occured.   
int x;   
int y;   
for (x = 1; x <= 1000000000; x++) {   
    y = x * 2;   
}   
//Stop event handling.   
db.Events.StopEvents();   
}  
```  
  
  
