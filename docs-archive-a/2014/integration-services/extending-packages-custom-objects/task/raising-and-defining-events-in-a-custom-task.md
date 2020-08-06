---
title: カスタム タスクでのイベントの発生と定義 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS events, custom
- status information [SQL Server], task events
- custom tasks [Integration Services], events
- SSIS custom tasks, events
- IDTSComponentEvents interface
- events [Integration Services], custom
- events [Integration Services], runtime
- custom events [Integration Services]
- SSIS events, runtime
- IDTSEvents interface
ms.assetid: e0898aa1-e90c-4c4e-99d4-708a76efddfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb41ee60543a05b6cf10b3acda43372e20288d13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642919"
---
# <a name="raising-and-defining-events-in-a-custom-task"></a><span data-ttu-id="5ead8-102">カスタム タスクでのイベントの発生と定義</span><span class="sxs-lookup"><span data-stu-id="5ead8-102">Raising and Defining Events in a Custom Task</span></span>
  <span data-ttu-id="5ead8-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイム エンジンには、タスクを検証および実行する際の進行状況の状態を示す、イベントのコレクションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5ead8-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine provides a collection of events that provide status on the progress of a task as the task is validated and executed.</span></span> <span data-ttu-id="5ead8-104"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> インターフェイスはこれらのイベントを定義し、<xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> および <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> メソッドに対するパラメーターとして、タスクに渡されます。</span><span class="sxs-lookup"><span data-stu-id="5ead8-104">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface defines these events, and is provided to tasks as a parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> methods.</span></span>  
  
 <span data-ttu-id="5ead8-105"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> インターフェイスでは、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> によってタスクの代わりに発生するイベントのセットが別に定義されています。</span><span class="sxs-lookup"><span data-stu-id="5ead8-105">There is another set of events, which are defined in the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface, that are raised on behalf of the task by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="5ead8-106"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> は、検証および実行の前後にイベントを発生させます。これに対してタスクは、実行および検証中にイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="5ead8-106">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> raises events that occur before and after validation and execution, whereas the task raises the events that occur during execution and validation.</span></span>  
  
## <a name="creating-custom-events"></a><span data-ttu-id="5ead8-107">カスタム イベントの作成</span><span class="sxs-lookup"><span data-stu-id="5ead8-107">Creating Custom Events</span></span>  
 <span data-ttu-id="5ead8-108">カスタム タスクの開発者は、オーバーライドした <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> メソッドの実装に新しい <xref:Microsoft.SqlServer.Dts.Runtime.Task.InitializeTask%2A> を作成することにより、新しいカスタム イベントを定義できます。</span><span class="sxs-lookup"><span data-stu-id="5ead8-108">Custom task developers can define new, custom events by creating a new <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> in their overridden implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Task.InitializeTask%2A> method.</span></span> <span data-ttu-id="5ead8-109"><xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> が作成されると、<xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> メソッドを使用して `EventInfos` コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5ead8-109">After the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> is created, it is added to the `EventInfos` collection by using the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> method.</span></span> <span data-ttu-id="5ead8-110">次に、<xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> メソッドのメソッド シグネチャを示します。</span><span class="sxs-lookup"><span data-stu-id="5ead8-110">The method signature of the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> method is as follows:</span></span>  
  
 `public void Add(string eventName, string description, bool allowEventHandlers, string[] parameterNames, TypeCode[] parameterTypes, string[] parameterDescriptions);`  
  
 <span data-ttu-id="5ead8-111">次のコード例では、カスタム タスクの `InitializeTask` メソッドを示します。ここでは、2 つのカスタム イベントが作成され、そのプロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="5ead8-111">The following code sample shows the `InitializeTask` method of a custom task, where two custom events are created and their properties are set.</span></span> <span data-ttu-id="5ead8-112">次に、新しいイベントが <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5ead8-112">The new events are then added to the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> collection.</span></span>  
  
 <span data-ttu-id="5ead8-113">最初のカスタム イベントの *eventName* は "**OnBeforeIncrement**" で、*description* は "**Fires after the initial value is updated**" です。</span><span class="sxs-lookup"><span data-stu-id="5ead8-113">The first custom event has an *eventName* of "**OnBeforeIncrement**" and *description* of "**Fires after the initial value is updated.**"</span></span> <span data-ttu-id="5ead8-114">次のパラメーターの値は `true` であり、イベントを処理するために、イベント ハンドラーのコンテナーの作成を許可する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="5ead8-114">The next parameter, the `true` value, indicates that this event should allow an event handler container to be created to handle the event.</span></span> <span data-ttu-id="5ead8-115">このイベント ハンドラーは、Package、Sequence、ForLoop、ForEachLoop などの他のコンテナーと同様、パッケージの構造およびサービスをタスクに提供するコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="5ead8-115">The event handler is a container that provides structure in a package and services to tasks, like other containers such as the package, Sequence, ForLoop, and ForEachLoop.</span></span> <span data-ttu-id="5ead8-116">*AllowEventHandlers*パラメーターがの場合 `true` 、 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> イベント用にオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5ead8-116">When the *allowEventHandlers* parameter is `true`, <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects are created for the event.</span></span> <span data-ttu-id="5ead8-117">これで、イベント用に定義された任意のパラメーターが、<xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> の変数コレクション内の <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ead8-117">Any parameters that were defined for the event are now available to the <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> in the variables collection of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>.</span></span>  
  
```csharp  
public override void InitializeTask(Connections connections,  
   VariableDispenser variables, IDTSInfoEvents events,  
   IDTSLogging log, EventInfos eventInfos,  
   LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
{  
    this.eventInfos = eventInfos;  
    string[] paramNames = new string[1];  
    TypeCode[] paramTypes = new TypeCode[1]{TypeCode.Int32};  
    string[] paramDescriptions = new string[1];  
  
    paramNames[0] = "InitialValue";  
    paramDescriptions[0] = "The value before it is incremented.";  
  
    this.eventInfos.Add("OnBeforeIncrement",   
      "Fires before the task increments the value.",  
      true,paramNames,paramTypes,paramDescriptions);  
    this.onBeforeIncrement = this.eventInfos["OnBeforeIncrement"];  
  
    paramDescriptions[0] = "The value after it has been incremented.";  
    this.eventInfos.Add("OnAfterIncrement",  
      "Fires after the initial value is updated.",  
      true,paramNames, paramTypes,paramDescriptions);  
    this.onAfterIncrement = this.eventInfos["OnAfterIncrement"];  
}  
```  
  
```vb  
Public Overrides Sub InitializeTask(ByVal connections As Connections, _  
ByVal variables As VariableDispenser, ByVal events As IDTSInfoEvents, _  
ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, _  
ByVal logEntryInfos As LogEntryInfos, ByVal refTracker As ObjectReferenceTracker)   
  
    Dim paramNames(0) As String  
    Dim paramTypes(0) As TypeCode = {TypeCode.Int32}  
    Dim paramDescriptions(0) As String  
  
    Me.eventInfos = eventInfos  
  
    paramNames(0) = "InitialValue"  
    paramDescriptions(0) = "The value before it is incremented."  
  
    Me.eventInfos.Add("OnBeforeIncrement", _  
      "Fires before the task increments the value.", _  
      True, paramNames, paramTypes, paramDescriptions)  
    Me.onBeforeIncrement = Me.eventInfos("OnBeforeIncrement")  
  
    paramDescriptions(0) = "The value after it has been incremented."  
    Me.eventInfos.Add("OnAfterIncrement", _  
      "Fires after the initial value is updated.", True, _  
      paramNames, paramTypes, paramDescriptions)  
    Me.onAfterIncrement = Me.eventInfos("OnAfterIncrement")  
  
End Sub  
```  
  
## <a name="raising-custom-events"></a><span data-ttu-id="5ead8-118">カスタム イベントの発生</span><span class="sxs-lookup"><span data-stu-id="5ead8-118">Raising Custom Events</span></span>  
 <span data-ttu-id="5ead8-119">カスタム イベントは、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> メソッドを呼び出すことにより発生します。</span><span class="sxs-lookup"><span data-stu-id="5ead8-119">Custom events are raised by calling the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> method.</span></span> <span data-ttu-id="5ead8-120">次のコード行では、カスタム イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="5ead8-120">The following line of code raises a custom event.</span></span>  
  
```csharp  
componentEvents.FireCustomEvent(this.onBeforeIncrement.Name,  
   this.onBeforeIncrement.Description, ref arguments,  
   null, ref bFireOnBeforeIncrement);  
```  
  
```vb  
componentEvents.FireCustomEvent(Me.onBeforeIncrement.Name, _  
Me.onBeforeIncrement.Description, arguments, _  
Nothing,  bFireOnBeforeIncrement)  
```  
  
## <a name="sample"></a><span data-ttu-id="5ead8-121">サンプル</span><span class="sxs-lookup"><span data-stu-id="5ead8-121">Sample</span></span>  
 <span data-ttu-id="5ead8-122">次の例では、`InitializeTask` メソッドでカスタム イベントを定義し、<xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> コレクションに追加するタスクを示します。このタスクは、次に <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> メソッドを呼び出して、`Execute` メソッドでカスタム イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="5ead8-122">The following example shows a task that defines a custom event in the `InitializeTask` method, adds the custom event to the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> collection, and then raises the custom event during its `Execute` method by calling the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> method.</span></span>  
  
```csharp  
[DtsTask(DisplayName = "CustomEventTask")]  
    public class CustomEventTask : Task  
    {  
        public override DTSExecResult Execute(Connections connections,   
          VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,  
           IDTSLogging log, object transaction)  
        {  
            bool fireAgain;  
            object[] args = new object[1] { "The value of the parameter." };  
            componentEvents.FireCustomEvent( "MyCustomEvent",   
              "Firing the custom event.", ref args,  
              "CustomEventTask" , ref fireAgain );  
            return DTSExecResult.Success;  
        }  
  
        public override void InitializeTask(Connections connections,  
          VariableDispenser variableDispenser, IDTSInfoEvents events,  
          IDTSLogging log, EventInfos eventInfos,  
          LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
        {  
            string[] names = new string[1] {"Parameter1"};  
            TypeCode[] types = new TypeCode[1] {TypeCode.String};  
            string[] descriptions = new string[1] {"Parameter description." };  
  
            eventInfos.Add("MyCustomEvent",  
             "Fires when my interesting event happens.",  
             true, names, types, descriptions);  
  
        }  
   }  
```  
  
```vb  
<DtsTask(DisplayName = "CustomEventTask")> _   
    Public Class CustomEventTask  
     Inherits Task  
        Public Overrides Function Execute(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser, _  
          ByVal componentEvents As IDTSComponentEvents, _  
          ByVal log As IDTSLogging, ByVal transaction As Object) _  
          As DTSExecResult  
  
            Dim fireAgain As Boolean  
            Dim args() As Object =  New Object(1) {"The value of the parameter."}  
  
            componentEvents.FireCustomEvent("MyCustomEvent", _  
              "Firing the custom event.", args, _  
              "CustomEventTask" ,  fireAgain)  
            Return DTSExecResult.Success  
        End Function  
  
        Public Overrides  Sub InitializeTask(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser,  
          ByVal events As IDTSInfoEvents,  
          ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, ByVal logEnTryInfos As LogEnTryInfos, ByVal refTracker As ObjectReferenceTracker)  
  
            Dim names() As String =  New String(1) {"Parameter1"}  
            Dim types() As TypeCode =  New TypeCode(1) {TypeCode.String}  
            Dim descriptions() As String =  New String(1) {"Parameter description."}  
  
            eventInfos.Add("MyCustomEvent", _  
              "Fires when my interesting event happens.", _  
              True, names, types, descriptions)  
  
        End Sub  
  
    End Class  
```  
  
<span data-ttu-id="5ead8-123">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="5ead8-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5ead8-124">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ead8-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5ead8-125">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="5ead8-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5ead8-126">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="5ead8-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ead8-127">参照</span><span class="sxs-lookup"><span data-stu-id="5ead8-127">See Also</span></span>  
 <span data-ttu-id="5ead8-128">[Integration Services &#40;SSIS&#41; のイベント ハンドラー](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="5ead8-128">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="5ead8-129">パッケージにイベント ハンドラーを追加する</span><span class="sxs-lookup"><span data-stu-id="5ead8-129">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
