---
title: プログラムによるタスクの追加 | Microsoft Docs
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
- tasks [Integration Services], packages
- adding package tasks
ms.assetid: 5d4652d5-228c-4238-905c-346dd8503fdf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa61eb2fb87f45fe5b534b96280b8b4e2c21788d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639613"
---
# <a name="adding-tasks-programmatically"></a><span data-ttu-id="d2dec-102">プログラムによるタスクの追加</span><span class="sxs-lookup"><span data-stu-id="d2dec-102">Adding Tasks Programmatically</span></span>
  <span data-ttu-id="d2dec-103">ランタイム エンジン内の次の種類のオブジェクトに、タスクを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-103">Tasks can be added to the following types of objects in the run-time engine:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Package>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Sequence>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>  
  
 <span data-ttu-id="d2dec-104">これらのクラスはコンテナーと見なされ、すべて <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSequence.Executables%2A> プロパティを継承します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-104">These classes are considered containers, and they all inherit the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSequence.Executables%2A> property.</span></span> <span data-ttu-id="d2dec-105">コンテナーにはタスクのコレクションを含めることができます。これらのタスクは、コンテナーの実行中にランタイムによって処理される実行可能オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="d2dec-105">Containers can contain a collection of tasks, which are executable objects processed by the runtime during execution of the container.</span></span> <span data-ttu-id="d2dec-106">コレクション内のオブジェクトの実行順序は、コンテナー内の各タスクに設定された <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> によって決まります。</span><span class="sxs-lookup"><span data-stu-id="d2dec-106">The order of execution of the objects in the collection is determined any <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> set on each task in the containers.</span></span> <span data-ttu-id="d2dec-107">優先順位制約によって、コレクション内の <xref:Microsoft.SqlServer.Dts.Runtime.Executable> の成功、失敗、または完了に基づく、実行の分岐ができます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-107">Precedence constraints enable execution branching based on the success, failure, or completion of an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> in the collection.</span></span>  
  
 <span data-ttu-id="d2dec-108">各コンテナーには、個々の <xref:Microsoft.SqlServer.Dts.Runtime.Executables> オブジェクトを含んでいる <xref:Microsoft.SqlServer.Dts.Runtime.Executable> コレクションがあります。</span><span class="sxs-lookup"><span data-stu-id="d2dec-108">Each container has an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> collection that contains the individual <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects.</span></span> <span data-ttu-id="d2dec-109">各実行可能タスクは <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> メソッドを継承して実装します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-109">Each executable task inherits and implements the <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> method and <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> method.</span></span> <span data-ttu-id="d2dec-110">これらの 2 つのメソッドはランタイム エンジンによって呼び出され、各 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> を処理します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-110">These two methods are called by the run-time engine to process each <xref:Microsoft.SqlServer.Dts.Runtime.Executable>.</span></span>  
  
 <span data-ttu-id="d2dec-111">パッケージにタスクを追加するには、<xref:Microsoft.SqlServer.Dts.Runtime.Executables> の既存のコレクションを持つコンテナーが必要です。</span><span class="sxs-lookup"><span data-stu-id="d2dec-111">To add a task to a package, you need a container with an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> existing collection.</span></span> <span data-ttu-id="d2dec-112">ほとんどの場合、コレクションに追加するタスクはパッケージです。</span><span class="sxs-lookup"><span data-stu-id="d2dec-112">Most of the time, the task that you will add to the collection is a package.</span></span> <span data-ttu-id="d2dec-113">新しいタスクの実行可能ファイルをそのコンテナーのコレクションに追加するには、<xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-113">To add the new task executable into the collection for that container, you call the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method .</span></span> <span data-ttu-id="d2dec-114">このメソッドには単一の文字列パラメーターがあり、CLSID、PROGID、STOCK モニカー、または、追加するタスクの <xref:Microsoft.SqlServer.Dts.Runtime.TaskInfo.CreationName%2A> が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-114">The method has a single parameter, a string, that contains the CLSID, PROGID, STOCK moniker, or <xref:Microsoft.SqlServer.Dts.Runtime.TaskInfo.CreationName%2A> of the task you are adding.</span></span>  
  
## <a name="task-names"></a><span data-ttu-id="d2dec-115">タスク名</span><span class="sxs-lookup"><span data-stu-id="d2dec-115">Task Names</span></span>  
 <span data-ttu-id="d2dec-116">名前または ID でタスクを指定できますが、<xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> メソッドで最もよく使用されるパラメーターは `STOCK` モニカーです。</span><span class="sxs-lookup"><span data-stu-id="d2dec-116">Although you can specify a task by name or by ID, the `STOCK` moniker is the parameter used most often in the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method.</span></span> <span data-ttu-id="d2dec-117">`STOCK` モニカーによって識別される実行可能ファイルにタスクを追加するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-117">To add a task to an executable identified by the `STOCK` moniker, use the following syntax:</span></span>  
  
```csharp  
Executable exec = package.Executables.Add("STOCK:BulkInsertTask");  
  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add("STOCK:BulkInsertTask")  
  
```  
  
 <span data-ttu-id="d2dec-118">次の一覧は、`STOCK` モニカーの後に使用する各タスクの名前を示したものです。</span><span class="sxs-lookup"><span data-stu-id="d2dec-118">The following list shows the names for each task that are used after the `STOCK` moniker.</span></span>  
  
-   <span data-ttu-id="d2dec-119">ActiveXScriptTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-119">ActiveXScriptTask</span></span>  
  
-   <span data-ttu-id="d2dec-120">BulkInsertTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-120">BulkInsertTask</span></span>  
  
-   <span data-ttu-id="d2dec-121">ExecuteProcessTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-121">ExecuteProcessTask</span></span>  
  
-   <span data-ttu-id="d2dec-122">ExecutePackageTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-122">ExecutePackageTask</span></span>  
  
-   <span data-ttu-id="d2dec-123">Exec80PackageTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-123">Exec80PackageTask</span></span>  
  
-   <span data-ttu-id="d2dec-124">FileSystemTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-124">FileSystemTask</span></span>  
  
-   <span data-ttu-id="d2dec-125">FTPTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-125">FTPTask</span></span>  
  
-   <span data-ttu-id="d2dec-126">MSMQTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-126">MSMQTask</span></span>  
  
-   <span data-ttu-id="d2dec-127">PipelineTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-127">PipelineTask</span></span>  
  
-   <span data-ttu-id="d2dec-128">ScriptTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-128">ScriptTask</span></span>  
  
-   <span data-ttu-id="d2dec-129">SendMailTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-129">SendMailTask</span></span>  
  
-   <span data-ttu-id="d2dec-130">SQLTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-130">SQLTask</span></span>  
  
-   <span data-ttu-id="d2dec-131">TransferStoredProceduresTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-131">TransferStoredProceduresTask</span></span>  
  
-   <span data-ttu-id="d2dec-132">TransferLoginsTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-132">TransferLoginsTask</span></span>  
  
-   <span data-ttu-id="d2dec-133">TransferErrorMessagesTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-133">TransferErrorMessagesTask</span></span>  
  
-   <span data-ttu-id="d2dec-134">TransferJobsTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-134">TransferJobsTask</span></span>  
  
-   <span data-ttu-id="d2dec-135">TransferObjectsTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-135">TransferObjectsTask</span></span>  
  
-   <span data-ttu-id="d2dec-136">TransferDatabaseTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-136">TransferDatabaseTask</span></span>  
  
-   <span data-ttu-id="d2dec-137">WebServiceTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-137">WebServiceTask</span></span>  
  
-   <span data-ttu-id="d2dec-138">WmiDataReaderTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-138">WmiDataReaderTask</span></span>  
  
-   <span data-ttu-id="d2dec-139">WmiEventWatcherTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-139">WmiEventWatcherTask</span></span>  
  
-   <span data-ttu-id="d2dec-140">XMLTask</span><span class="sxs-lookup"><span data-stu-id="d2dec-140">XMLTask</span></span>  
  
 <span data-ttu-id="d2dec-141">明示的な構文を使用する場合、または追加しようとするタスクに STOCK モニカーがない場合は、長い名前を使用して実行可能ファイルにタスクを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-141">If you prefer a more explicit syntax, or if the task that you want to add does not have a STOCK moniker, you can add the task to the executable using its long name.</span></span> <span data-ttu-id="d2dec-142">この構文では、タスクのバージョン番号も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2dec-142">This syntax requires that you also specify the version number of the task.</span></span>  
  
```csharp  
Executable exec = package.Executables.Add(  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " +  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " +  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91");  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add( _  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " & _  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " & _  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91")  
```  
  
 <span data-ttu-id="d2dec-143">タスクのバージョンを指定しないで、次の例のようにクラスの **AssemblyQualifiedName** プロパティを使用して、プログラムによってタスクの長い名前を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-143">You can obtain the long name for the task programmatically, without having to specify the task version, by using the **AssemblyQualifiedName** property of the class, as shown in the following example.</span></span> <span data-ttu-id="d2dec-144">この例では、Microsoft.SqlServer.SQLTask アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="d2dec-144">This example requires a reference to the Microsoft.SqlServer.SQLTask assembly.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask;  
...  
      Executable exec = package.Executables.Add(  
        typeof(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName);  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask  
...  
    Dim exec As Executable = package.Executables.Add( _  
      GetType(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName)  
```  
  
 <span data-ttu-id="d2dec-145">次のコード例は、新しいパッケージから <xref:Microsoft.SqlServer.Dts.Runtime.Executables> コレクションを作成し、`STOCK` モニカーを使用してファイル システム タスクと一括挿入タスクをコレクションに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d2dec-145">The following code example shows how to create an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> collection from a new package, and then add a File System task and a Bulk Insert task to the collection, by using their `STOCK` monikers.</span></span> <span data-ttu-id="d2dec-146">この例では、Microsoft.SqlServer.FileSystemTask および Microsoft.SqlServer.BulkInsertTask アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="d2dec-146">This example requires a reference to the Microsoft.SqlServer.FileSystemTask and Microsoft.SqlServer.BulkInsertTask assemblies.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thBulkInsertTask = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        Console.WriteLine("Type {0}", taskHost.InnerObject.ToString());  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thBulkInsertTask As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      Console.WriteLine("Type {0}", taskHost.InnerObject.ToString())  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="d2dec-147">**サンプル出力:**</span><span class="sxs-lookup"><span data-stu-id="d2dec-147">**Sample Output:**</span></span>  
  
 `Type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
## <a name="taskhost-container"></a><span data-ttu-id="d2dec-148">TaskHost コンテナー</span><span class="sxs-lookup"><span data-stu-id="d2dec-148">TaskHost Container</span></span>  
 <span data-ttu-id="d2dec-149"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> クラスは、グラフィカル ユーザー インターフェイスには出現しないコンテナーですが、プログラムを作成する際には非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="d2dec-149">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> class is a container that does not appear in the graphical user interface, but is very important in programming.</span></span> <span data-ttu-id="d2dec-150">このクラスは、すべてのタスク用のラッパーです。</span><span class="sxs-lookup"><span data-stu-id="d2dec-150">This class is a wrapper for every task.</span></span> <span data-ttu-id="d2dec-151"><xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> メソッドを <xref:Microsoft.SqlServer.Dts.Runtime.Executable> オブジェクトとして使用してパッケージに追加されたタスクは、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> オブジェクトとしてキャストできます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-151">Tasks that are added to the package by using the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method as an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> object can be cast as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object.</span></span> <span data-ttu-id="d2dec-152">タスクが <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> としてキャストされる場合は、タスクの追加プロパティおよびメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-152">When a task is cast as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, you can use additional properties and methods on the task.</span></span> <span data-ttu-id="d2dec-153">また、タスク自体には、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> プロパティをとおしてアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-153">Also, the task itself can be accessed through the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="d2dec-154">必要に応じて、タスクを <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> オブジェクトとして保持し、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> コレクションをとおしてタスクのプロパティを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-154">Depending on your needs, you may decide to keep the task as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object so that you can use the properties of the task through the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> collection.</span></span> <span data-ttu-id="d2dec-155"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> を使用する利点は、汎用性の高いコードを記述できることです。</span><span class="sxs-lookup"><span data-stu-id="d2dec-155">The advantage of using the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> is that you can write more generic code.</span></span> <span data-ttu-id="d2dec-156">タスク固有のコードが必要な場合は、タスクを適切なオブジェクトにキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2dec-156">If you need very specific code for a task, then you should cast the task to its appropriate object.</span></span>  
  
 <span data-ttu-id="d2dec-157">次のコード例は、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> を含む <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>、thBulkInsertTask を <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> オブジェクトにキャストする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d2dec-157">The following code example shows how to cast a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, thBulkInsertTask, that contains a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>, to a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> object.</span></span>  
  
```csharp  
BulkInsertTask myTask = thBulkInsertTask.InnerObject as BulkInsertTask;  
```  
  
```vb  
Dim myTask As BulkInsertTask = CType(thBulkInsertTask.InnerObject, BulkInsertTask)  
```  
  
 <span data-ttu-id="d2dec-158">次のコード例は、実行可能ファイルを <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> にキャストし、次に <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> プロパティを使用して、ホストに含まれている実行可能ファイルの種類を特定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d2dec-158">The following code example shows how to cast the executable to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, and then use the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> property to determine which type of executable is contained by the host.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask1 = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thFileSystemTask2 = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask)  
        {  
          // Do work with FileSystemTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        else if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask)  
        {  
          // Do work with BulkInsertTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        // Add additional statements to check InnerObject, if desired.  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask1 As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thFileSystemTask2 As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      If TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask Then  
        ' Do work with FileSystemTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      ElseIf TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask Then  
        ' Do work with BulkInsertTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      End If  
      ' Add additional statements to check InnerObject, if desired.  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="d2dec-159">**サンプル出力:**</span><span class="sxs-lookup"><span data-stu-id="d2dec-159">**Sample Output:**</span></span>  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
 <span data-ttu-id="d2dec-160"><xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> ステートメントは、新しく作成された <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> オブジェクトから <xref:Microsoft.SqlServer.Dts.Runtime.Executable> オブジェクトにキャストされる実行可能ファイルを返します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-160">The <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> statement returns an executable that is cast to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object from the newly created <xref:Microsoft.SqlServer.Dts.Runtime.Executable> object.</span></span>  
  
 <span data-ttu-id="d2dec-161">新しいオブジェクトのプロパティの設定またはメソッドの呼び出しを行う場合、2 つのオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-161">To set properties or to call methods on the new object, you have two options:</span></span>  
  
1.  <span data-ttu-id="d2dec-162"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> コレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-162">Use the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="d2dec-163">たとえば、オブジェクトからプロパティを取得するには、`th.Properties["propertyname"].GetValue(th))` を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-163">For example, to obtain a property from the object, use `th.Properties["propertyname"].GetValue(th))`.</span></span> <span data-ttu-id="d2dec-164">プロパティを設定するには、`th.Properties["propertyname"].SetValue(th, <value>);` を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-164">To set a property, use `th.Properties["propertyname"].SetValue(th, <value>);`.</span></span>  
  
2.  <span data-ttu-id="d2dec-165"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> をタスク クラスにキャストします。</span><span class="sxs-lookup"><span data-stu-id="d2dec-165">Cast the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> to the task class.</span></span> <span data-ttu-id="d2dec-166">たとえば、一括挿入タスクが <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> としてパッケージに追加され、その後 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> にキャストされた後で、このタスクを <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> にキャストするには、`BulkInsertTask myTask = th.InnerObject as BulkInsertTask;` を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-166">For example, to cast the Bulk Insert task to a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> after it has been added to a package as an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> and subsequently cast to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, use `BulkInsertTask myTask = th.InnerObject as BulkInsertTask;`.</span></span>  
  
 <span data-ttu-id="d2dec-167">タスク固有のクラスにキャストする代わりに <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> クラスをコードで使用する場合、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="d2dec-167">Using the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> class in code, instead of casting to the task-specific class has the following advantages:</span></span>  
  
-   <span data-ttu-id="d2dec-168"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> プロバイダーは、コード内でアセンブリを参照する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="d2dec-168">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> provider does not require a reference to the assembly in the code.</span></span>  
  
-   <span data-ttu-id="d2dec-169">コンパイル時にタスクの名前を知る必要がないため、すべてのタスクで動作する汎用ルーチンをコーディングできます。</span><span class="sxs-lookup"><span data-stu-id="d2dec-169">You can code generic routines that work for any task, because you do not have to know the name of the task at compile time.</span></span> <span data-ttu-id="d2dec-170">このような汎用ルーチンには、タスク名を引数として受け取るメソッドが含まれます。このメソッド コードはすべてのタスクで動作します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-170">Such generic routines include methods where you pass in the name of the task to the method, and the method code works for all tasks.</span></span> <span data-ttu-id="d2dec-171">これは、テスト コードを記述するのに適したメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d2dec-171">This is a good method for writing test code.</span></span>  
  
 <span data-ttu-id="d2dec-172"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> からタスク固有のクラスにキャストする場合、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="d2dec-172">Casting from the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> to the task-specific class has the following advantages:</span></span>  
  
-   <span data-ttu-id="d2dec-173">Visual Studio プロジェクトからステートメントの完了が提供されます (IntelliSense)。</span><span class="sxs-lookup"><span data-stu-id="d2dec-173">The Visual Studio project gives you statement completion (IntelliSense).</span></span>  
  
-   <span data-ttu-id="d2dec-174">コードの実行が高速化する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d2dec-174">The code may run faster.</span></span>  
  
-   <span data-ttu-id="d2dec-175">タスク固有のオブジェクトを使用すると、事前バインドおよび結果の最適化が有効になります。</span><span class="sxs-lookup"><span data-stu-id="d2dec-175">Task-specific objects enable early binding and the resulting optimizations.</span></span> <span data-ttu-id="d2dec-176">事前バインドおよび遅延バインドの詳細については、「Visual Basic 言語の概念」の「事前バインドと遅延バインド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2dec-176">For more information about early and late binding, see the topic "Early and Late Binding" in Visual Basic Language Concepts.</span></span>  
  
 <span data-ttu-id="d2dec-177">次のコード例は、タスク コードの再利用の概念について、詳細を示しています。</span><span class="sxs-lookup"><span data-stu-id="d2dec-177">The following code example expands on the concept of reusing task code.</span></span> <span data-ttu-id="d2dec-178">このコード例では、タスクを同等のクラスにキャストせず、代わりに実行可能ファイルを <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> にキャストしてから、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> を使用してすべてのタスクに対する汎用コードを記述する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d2dec-178">Instead of casting tasks to their specific class equivalents, the code example shows how to cast the executable to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, and then uses the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> to write generic code against all the tasks.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
  
      string[] tasks = { "STOCK:SQLTask", "STOCK:ScriptTask",   
        "STOCK:ExecuteProcessTask", "STOCK:PipelineTask",   
        "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask" };  
  
      foreach (string s in tasks)  
      {  
        TaskHost taskhost = package.Executables.Add(s) as TaskHost;  
        DtsProperties props = taskhost.Properties;  
        Console.WriteLine("Enumerating properties on " + taskhost.Name);  
        Console.WriteLine(" TaskHost.InnerObject is " + taskhost.InnerObject.ToString());  
        Console.WriteLine();  
  
        foreach (DtsProperty prop in props)  
        {  
          Console.WriteLine("Properties for " + prop.Name);  
          Console.WriteLine("Name : " + prop.Name);  
          Console.WriteLine("Type : " + prop.Type.ToString());  
          Console.WriteLine("Readable : " + prop.Get.ToString());  
          Console.WriteLine("Writable : " + prop.Set.ToString());  
          Console.WriteLine();  
        }  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package = New Package()  
  
    Dim tasks() As String = New String() {"STOCK:SQLTask", "STOCK:ScriptTask", _  
              "STOCK:ExecuteProcessTask", "STOCK:PipelineTask", _  
              "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask"}  
  
    For Each s As String In tasks  
  
      Dim taskhost As TaskHost = CType(package.Executables.Add(s), TaskHost)  
      Dim props As DtsProperties = taskhost.Properties  
      Console.WriteLine("Enumerating properties on " & taskhost.Name)  
      Console.WriteLine(" TaskHost.InnerObject is " & taskhost.InnerObject.ToString())  
      Console.WriteLine()  
  
      For Each prop As DtsProperty In props  
        Console.WriteLine("Properties for " + prop.Name)  
        Console.WriteLine(" Name : " + prop.Name)  
        Console.WriteLine(" Type : " + prop.Type.ToString())  
        Console.WriteLine(" Readable : " + prop.Get.ToString())  
        Console.WriteLine(" Writable : " + prop.Set.ToString())  
        Console.WriteLine()  
      Next  
  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="d2dec-179">外部リソース</span><span class="sxs-lookup"><span data-stu-id="d2dec-179">External Resources</span></span>  
 <span data-ttu-id="d2dec-180">blogs.msdn.com のブログ「[EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223)」(EzAPI - SQL Server 2012 用の更新)</span><span class="sxs-lookup"><span data-stu-id="d2dec-180">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="d2dec-181">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="d2dec-181">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d2dec-182">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2dec-182">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d2dec-183">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="d2dec-183">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d2dec-184">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="d2dec-184">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2dec-185">参照</span><span class="sxs-lookup"><span data-stu-id="d2dec-185">See Also</span></span>  
 [<span data-ttu-id="d2dec-186">プログラムによるタスクの接続</span><span class="sxs-lookup"><span data-stu-id="d2dec-186">Connecting Tasks Programmatically</span></span>](../building-packages-programmatically/connecting-tasks-programmatically.md)  
  
  
