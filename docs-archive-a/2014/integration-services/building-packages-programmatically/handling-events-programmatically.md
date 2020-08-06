---
title: プログラムによるイベントの処理 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Integration Services packages, events
- SQL Server Integration Services packages, events
- SSIS events, programmatically handling
- packages [Integration Services], events
- DtsEventHandler object
- SSIS packages, events
- SSIS events
- events [Integration Services], programmatically
- tasks [Integration Services], events
- IDTSEvents interface
ms.assetid: 0f00bd66-efd5-4f12-9e1c-36195f739332
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c70d2d8909df65f775fc3a3034931bb599597068
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634600"
---
# <a name="handling-events-programmatically"></a><span data-ttu-id="61829-102">プログラムによるイベントの処理</span><span class="sxs-lookup"><span data-stu-id="61829-102">Handling Events Programmatically</span></span>
  <span data-ttu-id="61829-103">[!INCLUDE[ssIS](../../includes/ssis-md.md)] のランタイムには、パッケージの検証や実行の処理前、処理中、処理後に発生する一連のイベントがあります。</span><span class="sxs-lookup"><span data-stu-id="61829-103">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] runtime provides a collection of events that occur before, during, and after the validation and execution of a package.</span></span> <span data-ttu-id="61829-104">これらのイベントをキャプチャするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="61829-104">These events can be captured in two ways.</span></span> <span data-ttu-id="61829-105">1 つは、あるクラスに <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> インターフェイスを実装し、このクラスをパラメーターとして、パッケージの `Execute` メソッドおよび `Validate` メソッドに渡す方法です。</span><span class="sxs-lookup"><span data-stu-id="61829-105">The first method is by implementing the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface in a class, and supplying the class as a parameter to the `Execute` and `Validate` methods of the package.</span></span> <span data-ttu-id="61829-106">もう 1 つは <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> オブジェクトを作成する方法です。このオブジェクトには、タスクやループなど、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> に属するイベントが発生したときに実行される、他の [!INCLUDE[ssIS](../../includes/ssis-md.md)] オブジェクトを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="61829-106">The second method is by creating <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects, which can contain other [!INCLUDE[ssIS](../../includes/ssis-md.md)] objects, such as tasks and loops, that are executed when an event in <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> occurs.</span></span> <span data-ttu-id="61829-107">ここでは、この 2 つの方法について説明し、その使用法をコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="61829-107">This section describes these two methods and provides code examples to demonstrate their use.</span></span>  
  
## <a name="receiving-idtsevents-callbacks"></a><span data-ttu-id="61829-108">IDTSEvents コールバックの受信</span><span class="sxs-lookup"><span data-stu-id="61829-108">Receiving IDTSEvents Callbacks</span></span>  
 <span data-ttu-id="61829-109">プログラムによってパッケージを構築し、実行する開発者は、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> インターフェイスを使用して、検証中や実行中に発生したイベント通知を受信することができます。</span><span class="sxs-lookup"><span data-stu-id="61829-109">Developers who build and execute packages programmatically can receive event notifications during the validation and execution process using the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface.</span></span> <span data-ttu-id="61829-110">これを行うには、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> インターフェイスを実装したクラスを作成し、このクラスをパラメーターとして、パッケージの `Validate` メソッドおよび `Execute` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="61829-110">This is done by creating a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface and providing this class as a parameter to the `Validate` and `Execute` methods of a package.</span></span> <span data-ttu-id="61829-111">イベントが発生すると、ランタイム エンジンによってこのクラスのメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="61829-111">The methods of the class are then called by the run-time engine when the events occur.</span></span>  
  
 <span data-ttu-id="61829-112"><xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> クラスにはあらかじめ <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> インターフェイスが実装されています。したがって、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> インターフェイスを直接実装する代わりに、<xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> から派生するクラスを作成し、応答を受ける特定のイベントをオーバーライドする方法を取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="61829-112">The <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class is a class that already implements the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface; therefore, another alternative to implementing <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> directly is to derive from <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> and override the specific events that you want to respond to.</span></span> <span data-ttu-id="61829-113">その後、このクラスをパラメーターとして、<xref:Microsoft.SqlServer.Dts.Runtime.Package> の `Validate` メソッドおよび `Execute` メソッドに渡し、イベントのコールバックを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="61829-113">You then provide your class as a parameter to the `Validate` and `Execute` methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Package> to receive event callbacks.</span></span>  
  
 <span data-ttu-id="61829-114">次のコード サンプルは、<xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> から派生するクラスを示し、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnPreExecute%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="61829-114">The following code sample demonstrates a class that derives from <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents>, and overrides the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnPreExecute%2A> method.</span></span> <span data-ttu-id="61829-115">このクラスは、 `Validate` パッケージのメソッドおよびメソッドにパラメーターとして提供され `Execute` ます。</span><span class="sxs-lookup"><span data-stu-id="61829-115">The class is then provided as aparameter to the `Validate` and `Execute` methods of the package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      MyEventsClass eventsClass = new MyEventsClass();  
  
      p.Validate(null, null, eventsClass, null);  
      p.Execute(null, null, eventsClass, null, null);  
  
      Console.Read();  
    }  
  }  
  class MyEventsClass : DefaultEvents  
  {  
    public override void OnPreExecute(Executable exec, ref bool fireAgain)  
    {  
      // TODO: Add custom code to handle the event.  
      Console.WriteLine("The PreExecute event of the " +  
        exec.ToString() + " has been raised.");  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim eventsClass As MyEventsClass = New MyEventsClass()  
  
    p.Validate(Nothing, Nothing, eventsClass, Nothing)  
    p.Execute(Nothing, Nothing, eventsClass, Nothing, Nothing)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
Class MyEventsClass  
  Inherits DefaultEvents  
  
  Public Overrides Sub OnPreExecute(ByVal exec As Executable, ByRef fireAgain As Boolean)  
  
    ' TODO: Add custom code to handle the event.  
    Console.WriteLine("The PreExecute event of the " & _  
      exec.ToString() & " has been raised.")  
  
  End Sub  
  
End Class  
```  
  
## <a name="creating-dtseventhandler-objects"></a><span data-ttu-id="61829-116">DtsEventHandler オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="61829-116">Creating DtsEventHandler Objects</span></span>  
 <span data-ttu-id="61829-117">ランタイム エンジンには、<xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> オブジェクトを介した、堅牢で柔軟性の高いイベント処理/通知システムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="61829-117">The run-time engine provides a robust, highly flexible event handling and notification system through the <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> object.</span></span> <span data-ttu-id="61829-118">このオブジェクトを使用すると、イベント ハンドラー内のワークフロー全体をデザインして、そのイベント ハンドラーが属するイベントが発生したときにのみ、ワークフローを実行させることができます。</span><span class="sxs-lookup"><span data-stu-id="61829-118">These objects let you design whole workflows within the event handler, which execute only when the event that the event handler belongs to occurs.</span></span> <span data-ttu-id="61829-119"><xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> はコンテナー オブジェクトで、親オブジェクト内の対応するイベントが発生すると実行されます。</span><span class="sxs-lookup"><span data-stu-id="61829-119">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> object is a container that is executed when the corresponding event on its parent object fires.</span></span> <span data-ttu-id="61829-120">したがって、コンテナー上で発生したイベントに応答して実行されるワークフローを、他のワークフローとは独立して作成できます。</span><span class="sxs-lookup"><span data-stu-id="61829-120">This architecture lets you create isolated workflows that are executed in response to events that occur on a container.</span></span> <span data-ttu-id="61829-121"><xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> オブジェクトは同期型であるため、イベントにアタッチされたイベント ハンドラーが返されるまで、実行は再開されません。</span><span class="sxs-lookup"><span data-stu-id="61829-121">Because <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects are synchronous, execution does not resume until the event handlers that are attached to the event have returned.</span></span>  
  
 <span data-ttu-id="61829-122">次のコードは、<xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> オブジェクトの作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="61829-122">The following code demonstrates how to create a <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> object.</span></span> <span data-ttu-id="61829-123">コードは、<xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> をパッケージの <xref:Microsoft.SqlServer.Dts.Runtime.Package.Executables%2A> コレクションに追加し、次にタスクの <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> イベント用の <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="61829-123">The code adds a <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> to the <xref:Microsoft.SqlServer.Dts.Runtime.Package.Executables%2A> collection of the package, and then creates a <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> object for the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> event of the task.</span></span> <span data-ttu-id="61829-124"><xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> がイベント ハンドラーに追加されます。これは、最初の <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> に対する <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> イベントが発生したときに行われます。</span><span class="sxs-lookup"><span data-stu-id="61829-124">A <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> is added to the event handler, which is executed when the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> event occurs for the first <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>.</span></span> <span data-ttu-id="61829-125">この例では、C:\Windows\Temp\DemoFile.txt という名前のファイルをテストに使用することを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="61829-125">This example assumes that you have a file that is named C:\Windows\Temp\DemoFile.txt for testing.</span></span> <span data-ttu-id="61829-126">サンプルを初めて実行するとき、ファイルが正常にコピーされていれば、イベント ハンドラーは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="61829-126">The first time that you run the sample, if copies the file successfully and the event handler is not called.</span></span> <span data-ttu-id="61829-127">2 回目にサンプルを実行すると、最初の <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> はファイルのコピーに失敗し (<xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask.OverwriteDestinationFile%2A> の値が `false` であるため)、イベント ハンドラーが呼び出され、2 番目の <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> によって変換元ファイルが削除され、エラーの発生が原因でパッケージによって失敗が報告されます。</span><span class="sxs-lookup"><span data-stu-id="61829-127">The second time you run the sample, the first <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> fails to copy the file (because the value of <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask.OverwriteDestinationFile%2A> is `false`), the event handler is called, the second <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> deletes the source file, and the package reports failure because of the error that occurred.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61829-128">例</span><span class="sxs-lookup"><span data-stu-id="61829-128">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string f = "DemoFile.txt";  
      Executable e;  
      TaskHost th;  
      FileSystemTask fst;  
  
      Package p = new Package();  
  
      p.Variables.Add("sourceFile", true, String.Empty,  
        @"C:\Windows\Temp\" + f);  
      p.Variables.Add("destinationFile", true, String.Empty,  
        Path.Combine(Directory.GetCurrentDirectory(), f));  
  
      // Create a first File System task and add it to the package.  
      // This task tries to copy a file from one folder to another.  
      e = p.Executables.Add("STOCK:FileSystemTask");  
      th = e as TaskHost;  
      th.Name = "FileSystemTask1";  
      fst = th.InnerObject as FileSystemTask;  
  
      fst.Operation = DTSFileSystemOperation.CopyFile;  
      fst.OverwriteDestinationFile = false;  
      fst.Source = "sourceFile";  
      fst.IsSourcePathVariable = true;  
      fst.Destination = "destinationFile";  
      fst.IsDestinationPathVariable = true;  
  
      // Add an event handler for the FileSystemTask's OnError event.  
      DtsEventHandler ehOnError = (DtsEventHandler)th.EventHandlers.Add("OnError");  
  
      // Create a second File System task and add it to the event handler.  
      // This task deletes the source file if the event handler is called.  
      e = ehOnError.Executables.Add("STOCK:FileSystemTask");  
      th = e as TaskHost;  
      th.Name = "FileSystemTask2";  
      fst = th.InnerObject as FileSystemTask;  
  
      fst.Operation = DTSFileSystemOperation.DeleteFile;  
      fst.Source = "sourceFile";  
      fst.IsSourcePathVariable = true;  
  
      DTSExecResult vr = p.Validate(null, null, null, null);  
      Console.WriteLine("ValidationResult = " + vr.ToString());  
      if (vr == DTSExecResult.Success)  
      {  
        DTSExecResult er = p.Execute(null, null, null, null, null);  
        Console.WriteLine("ExecutionResult = " + er.ToString());  
        if (er == DTSExecResult.Failure)  
          if (!File.Exists(@"C:\Windows\Temp\" + f))  
            Console.WriteLine("Source file has been deleted by the event handler.");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim f As String = "DemoFile.txt"  
    Dim e As Executable  
    Dim th As TaskHost  
    Dim fst As FileSystemTask  
  
    Dim p As Package = New Package()  
  
    p.Variables.Add("sourceFile", True, String.Empty, _  
      "C:\Windows\Temp\" & f)  
    p.Variables.Add("destinationFile", True, String.Empty, _  
      Path.Combine(Directory.GetCurrentDirectory(), f))  
  
    ' Create a first File System task and add it to the package.  
    ' This task tries to copy a file from one folder to another.  
    e = p.Executables.Add("STOCK:FileSystemTask")  
    th = CType(e, TaskHost)  
    th.Name = "FileSystemTask1"  
    fst = CType(th.InnerObject, FileSystemTask)  
  
    fst.Operation = DTSFileSystemOperation.CopyFile  
    fst.OverwriteDestinationFile = False  
    fst.Source = "sourceFile"  
    fst.IsSourcePathVariable = True  
    fst.Destination = "destinationFile"  
    fst.IsDestinationPathVariable = True  
  
    ' Add an event handler for the FileSystemTask's OnError event.  
    Dim ehOnError As DtsEventHandler = CType(th.EventHandlers.Add("OnError"), DtsEventHandler)  
  
    ' Create a second File System task and add it to the event handler.  
    ' This task deletes the source file if the event handler is called.  
    e = ehOnError.Executables.Add("STOCK:FileSystemTask")  
    th = CType(e, TaskHost)  
    th.Name = "FileSystemTask1"  
    fst = CType(th.InnerObject, FileSystemTask)  
  
    fst.Operation = DTSFileSystemOperation.DeleteFile  
    fst.Source = "sourceFile"  
    fst.IsSourcePathVariable = True  
  
    Dim vr As DTSExecResult = p.Validate(Nothing, Nothing, Nothing, Nothing)  
    Console.WriteLine("ValidationResult = " + vr.ToString())  
    If vr = DTSExecResult.Success Then  
      Dim er As DTSExecResult = p.Execute(Nothing, Nothing, Nothing, Nothing, Nothing)  
      Console.WriteLine("ExecutionResult = " + er.ToString())  
      If er = DTSExecResult.Failure Then  
        If Not File.Exists("C:\Windows\Temp\" + f) Then  
          Console.WriteLine("Source file has been deleted by the event handler.")  
        End If  
      End If  
    End If  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="61829-129">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="61829-129">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="61829-130">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="61829-130">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="61829-131">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="61829-131">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="61829-132">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="61829-132">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61829-133">参照</span><span class="sxs-lookup"><span data-stu-id="61829-133">See Also</span></span>  
 <span data-ttu-id="61829-134">[Integration Services &#40;SSIS&#41; のイベント ハンドラー](../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="61829-134">[Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="61829-135">パッケージにイベント ハンドラーを追加する</span><span class="sxs-lookup"><span data-stu-id="61829-135">Add an Event Handler to a Package</span></span>](../add-an-event-handler-to-a-package.md)  
  
  
