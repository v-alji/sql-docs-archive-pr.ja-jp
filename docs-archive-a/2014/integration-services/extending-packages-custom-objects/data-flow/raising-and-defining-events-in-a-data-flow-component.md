---
title: データ フロー コンポーネントのイベントの発生と定義 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25f4572f8a8af829145da4e4d685f5dddad4a29a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713322"
---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a><span data-ttu-id="cc60c-102">データ フロー コンポーネントのイベントの発生と定義</span><span class="sxs-lookup"><span data-stu-id="cc60c-102">Raising and Defining Events in a Data Flow Component</span></span>
  <span data-ttu-id="cc60c-103">コンポーネント開発者は、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> プロパティで公開されているメソッドを呼び出して、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> インターフェイスで定義されているイベントのサブセットを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-103">Component developers can raise a subset of the events defined in the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface by calling the methods exposed on the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property.</span></span> <span data-ttu-id="cc60c-104">また、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> コレクションを使用してカスタム イベントを定義し、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> メソッドを使用して、実行時にこのイベントを発生させることもできます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-104">You can also define custom events by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> collection, and raise them during execution by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method.</span></span> <span data-ttu-id="cc60c-105">このセクションでは、イベントを作成、発生させる方法について説明し、デザイン時にイベントを発生させるタイミングに関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="cc60c-105">This section describes how to create and raise an event, and provides guidelines on when you should raise events at design time.</span></span>

## <a name="raising-events"></a><span data-ttu-id="cc60c-106">イベントの発生</span><span class="sxs-lookup"><span data-stu-id="cc60c-106">Raising Events</span></span>
 <span data-ttu-id="cc60c-107">コンポーネントは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスの **Fire\<X>** メソッドを使用して、イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-107">Components raise events by using the **Fire\<X>** methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span> <span data-ttu-id="cc60c-108">イベントは、コンポーネントのデザイン時および実行時のどちらでも発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-108">You can raise events during component design and execution.</span></span> <span data-ttu-id="cc60c-109">通常、コンポーネントのデザイン時には、検証中に <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> メソッドや <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-109">Typically, during component design, the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> methods are called during validation.</span></span> <span data-ttu-id="cc60c-110">これらのイベントは、コンポーネントが正しく構成されていない場合、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] の **[エラー一覧]** ペインにメッセージを表示し、ユーザーにフィードバックを返します。</span><span class="sxs-lookup"><span data-stu-id="cc60c-110">These events display messages in the **Error List** pane of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] and provide feedback to users of the component when a component is incorrectly configured.</span></span>

 <span data-ttu-id="cc60c-111">コンポーネントは、実行時の任意のタイミングでもイベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-111">Components can also raise events at any point during execution.</span></span> <span data-ttu-id="cc60c-112">イベントを使用すると、コンポーネント開発者はユーザーに対して、コンポーネントの実行に伴うフィードバックを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-112">Events allow component developers to provide feedback to users of the component as it executes.</span></span> <span data-ttu-id="cc60c-113">実行時に <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> メソッドが呼び出された場合、パッケージが失敗したと考えられます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-113">Calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> method during execution is likely to fail the package.</span></span>

## <a name="defining-and-raising-custom-events"></a><span data-ttu-id="cc60c-114">カスタム イベントの定義と発生</span><span class="sxs-lookup"><span data-stu-id="cc60c-114">Defining and Raising Custom Events</span></span>

### <a name="defining-a-custom-event"></a><span data-ttu-id="cc60c-115">カスタム イベントの定義</span><span class="sxs-lookup"><span data-stu-id="cc60c-115">Defining a Custom Event</span></span>
 <span data-ttu-id="cc60c-116">カスタム イベントを作成するには、<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> コレクションの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cc60c-116">Custom events are created by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> collection.</span></span> <span data-ttu-id="cc60c-117">このコレクションはデータ フロー タスクによって設定され、コンポーネント開発者には、基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> を介したプロパティとして提供されます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-117">This collection is set by the data flow task and provided as a property to the component developer through the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class.</span></span> <span data-ttu-id="cc60c-118">このクラスには、データ フロー タスクによって定義されたカスタム イベントと、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> メソッド内でコンポーネントによって定義されたカスタム イベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc60c-118">This class contains custom events defined by the data flow task and custom events defined by the component during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method.</span></span>

 <span data-ttu-id="cc60c-119">コンポーネントのカスタム イベントは、パッケージ XML には保存されません。</span><span class="sxs-lookup"><span data-stu-id="cc60c-119">The custom events of a component are not persisted in the package XML.</span></span> <span data-ttu-id="cc60c-120">したがって、コンポーネントのデザイン時および実行時の両方で <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> メソッドが呼び出され、発生するイベントが定義されます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-120">Therefore, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method is called during both design and execution to allow the component to define the events it raises.</span></span>

 <span data-ttu-id="cc60c-121"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> メソッドのパラメーター *allowEventHandlers* は、コンポーネントがイベント用に <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> オブジェクトを作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cc60c-121">The *allowEventHandlers* parameter of the <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> method specifies whether the component allows <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects to be created for the event.</span></span> <span data-ttu-id="cc60c-122"><xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> は同期型であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cc60c-122">Note that <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> are synchronous.</span></span> <span data-ttu-id="cc60c-123">このため、カスタム イベントにアタッチされた <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> の実行が終了するまで、コンポーネントは実行を再開しません。</span><span class="sxs-lookup"><span data-stu-id="cc60c-123">Therefore the component does not resume execution until an <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> attached to the custom event has finished executing.</span></span> <span data-ttu-id="cc60c-124">*AllowEventHandlers*パラメーターがの場合 `true` 、イベントの各パラメーターは、 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> ランタイムによって自動的に作成および設定された変数を通じて、任意のオブジェクトに対して自動的に使用できるようになり [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-124">If the *allowEventHandlers* parameter is `true`, each parameter of the event is automatically made available to any <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects through variables that are created and populated automatically by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.</span></span>

### <a name="raising-a-custom-event"></a><span data-ttu-id="cc60c-125">カスタム イベントの発生</span><span class="sxs-lookup"><span data-stu-id="cc60c-125">Raising a Custom Event</span></span>
 <span data-ttu-id="cc60c-126">コンポーネントは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> メソッドを呼び出し、イベントの名前、テキスト、パラメーターを渡して、カスタム イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-126">Components raise custom events by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method, and providing the name, text, and parameters of the event.</span></span> <span data-ttu-id="cc60c-127">*AllowEventHandlers*パラメーターがの場合 `true` 、 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> カスタムイベント用に作成されたは、ランタイムエンジンによって実行され [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="cc60c-127">If the *allowEventHandlers* parameter is `true`, any <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> that are created for the custom event are executed by the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] run-time engine.</span></span>

### <a name="custom-event-sample"></a><span data-ttu-id="cc60c-128">カスタム イベントのサンプル</span><span class="sxs-lookup"><span data-stu-id="cc60c-128">Custom Event Sample</span></span>
 <span data-ttu-id="cc60c-129">次のコード例では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> メソッドの実行中にカスタム イベントを定義し、実行時に <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> メソッドを呼び出してこのイベントを発生させるコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="cc60c-129">The following code example shows a component that defines a custom event during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method, and then raises the event at run time by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method.</span></span>

```csharp
public override void RegisterEvents()
{
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref parameterTypes, ref parameterDescriptions);
}
public override void ProcessInput(int inputID, PipelineBuffer buffer)
{
    while (buffer.NextRow())
    {
       // Process buffer rows.
    }

    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);
}
```

```vb
Public  Overrides Sub RegisterEvents() 
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"} 
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)} 
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."} 
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, parameterTypes, parameterDescriptions) 
End Sub 

Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer) 
  While buffer.NextRow 
  End While 
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort") 
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now} 
  ComponentMetaData.FireCustomEvent("StartingSort", _
    "Beginning sort operation.", arguments, _
    ComponentMetaData.Name, FireSortEventAgain) 
End Sub
```

<span data-ttu-id="cc60c-130">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="cc60c-130">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="cc60c-131">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc60c-131">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="cc60c-132">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="cc60c-132">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="cc60c-133">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="cc60c-133">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc60c-134">参照</span><span class="sxs-lookup"><span data-stu-id="cc60c-134">See Also</span></span>
 <span data-ttu-id="cc60c-135">[SSIS&#41; イベントハンドラーの Integration Services &#40;](../../integration-services-ssis-event-handlers.md) [パッケージへのイベントハンドラーの追加](../../add-an-event-handler-to-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="cc60c-135">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) [Add an Event Handler to a Package](../../add-an-event-handler-to-a-package.md)</span></span>


