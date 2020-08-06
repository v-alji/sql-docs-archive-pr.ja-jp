---
title: カスタム タスクにおけるデバッグのサポートの追加 | Microsoft Docs
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
- BreakpointManager class
- breakpoints [Integration Services]
- custom tasks [Integration Services], debugging
- IDTSSuspend interface
- IDTSBreakpointSite interface
- SSIS custom tasks, debugging
- debugging [Integration Services], custom tasks
ms.assetid: 7f06e49b-0b60-4e81-97da-d32dc248264a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fcc1d0c18cd559b547eadb9c1fa77e8f143389d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642190"
---
# <a name="adding-support-for-debugging-in-a-custom-task"></a><span data-ttu-id="abb5b-102">カスタム タスクにおけるデバッグのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="abb5b-102">Adding Support for Debugging in a Custom Task</span></span>
  <span data-ttu-id="abb5b-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイム エンジンでは、ブレークポイントを使用することにより、パッケージ、タスク、およびその他の種類のコンテナーを実行中に中断できます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine enables packages, tasks, and other types of containers to be suspended during execution by using breakpoints.</span></span> <span data-ttu-id="abb5b-104">ブレークポイントを使用すると、アプリケーションまたはタスクの正しい動作を妨げるエラーを確認し、修正できます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-104">The use of breakpoints lets you review and correct errors that prevent your application or tasks from running correctly.</span></span> <span data-ttu-id="abb5b-105">ブレークポイントのアーキテクチャにより、クライアントは、タスクの処理を中断している間にパッケージ内のオブジェクトのランタイム値を定義された実行地点で評価できます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-105">The breakpoint architecture enables the client to evaluate the run-time value of objects in the package at defined points of execution while task processing is suspended.</span></span>  
  
 <span data-ttu-id="abb5b-106">カスタム タスクの開発者はこのアーキテクチャを利用して、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> インターフェイス、およびその親インターフェイスである <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> を使用することにより、カスタム ブレークポイント ターゲットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-106">Custom task developers can use this architecture to create custom breakpoint targets by using the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface, and its parent interface, <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend>.</span></span> <span data-ttu-id="abb5b-107"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> インターフェイスは、ランタイム エンジンと、カスタム ブレークポイント サイトまたはターゲットを作成し管理するためのタスクとの間の対話を定義します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-107">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface defines the interaction between the run-time engine and the task for creating and managing custom breakpoint sites or targets.</span></span> <span data-ttu-id="abb5b-108"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> インターフェイスは、ランタイム エンジンによって呼び出され、タスクの実行の中断および再開を通知するメソッドおよびプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-108">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interface provides methods and properties that are called by the run-time engine to notify the task to suspend or resume its execution.</span></span>  
  
 <span data-ttu-id="abb5b-109">ブレークポイント サイトまたはターゲットは、処理を中断できるタスクの実行ポイントです。</span><span class="sxs-lookup"><span data-stu-id="abb5b-109">A breakpoint site or target is a point in the execution of the task where processing can be suspended.</span></span> <span data-ttu-id="abb5b-110">**[ブレークポイントの設定]** ダイアログ ボックスで使用できるブレークポイント サイトを選択します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-110">Users select from available breakpoint sites in the **Set Breakpoints** dialog box.</span></span> <span data-ttu-id="abb5b-111">たとえば、Foreach ループ コンテナーでは、既定のブレークポイント オプションだけでなく [ループの各繰り返しの開始点で停止します] オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-111">For example, in addition to the default breakpoint options, the Foreach Loop Container offers the "Break at the beginning of every iteration of the loop" option.</span></span>  
  
 <span data-ttu-id="abb5b-112">タスクが実行中にブレークポイント ターゲットに達すると、タスクはブレークポイント ターゲットを評価して、そのブレークポイントが有効かどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-112">When a task reaches a breakpoint target during execution, it evaluates the breakpoint target to determine whether a breakpoint is enabled.</span></span> <span data-ttu-id="abb5b-113">有効な場合は、そのブレークポイントで実行を停止することを示します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-113">This indicates that the user wants execution to stop at that breakpoint.</span></span> <span data-ttu-id="abb5b-114">ブレークポイントが有効な場合、タスクは、ランタイム エンジンに対して <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-114">If the breakpoint is enabled, the task raises the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> event to the run-time engine.</span></span> <span data-ttu-id="abb5b-115">ランタイム エンジンは、現在パッケージ内で実行中の各タスクの `Suspend` メソッドを呼び出して、このイベントに応答します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-115">The run-time engine responds to the event by calling the `Suspend` method of each task that is currently running in the package.</span></span> <span data-ttu-id="abb5b-116">中断されたタスクの `ResumeExecution` メソッドをランタイムが呼び出すと、タスクの実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-116">Execution of the task resumes when the runtime calls the `ResumeExecution` method of the suspended task.</span></span>  
  
 <span data-ttu-id="abb5b-117">ブレークポイントを使用していないタスクでも、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> および <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abb5b-117">Tasks that do not use breakpoints should still implement the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interfaces.</span></span> <span data-ttu-id="abb5b-118">これにより、パッケージ内の他のオブジェクトが <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> イベントを発生させた場合でも、タスクを正しく中断することができます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-118">This ensures that the task is suspended correctly when other objects in the package raise <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> events.</span></span>  
  
## <a name="idtsbreakpointsite-interface-and-breakpointmanager"></a><span data-ttu-id="abb5b-119">IDTSBreakpointSite インターフェイスおよび BreakpointManager</span><span class="sxs-lookup"><span data-stu-id="abb5b-119">IDTSBreakpointSite Interface and BreakpointManager</span></span>  
 <span data-ttu-id="abb5b-120">タスクは、<xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.CreateBreakpointTarget%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> メソッドを呼び出し、整数 ID と説明のための文字列を提供することによって、ブレークポイント ターゲットを作成します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-120">Tasks create breakpoint targets by calling the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.CreateBreakpointTarget%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager>, providing an integer ID and string description as parameters.</span></span> <span data-ttu-id="abb5b-121">タスクが、ブレークポイント ターゲットを含むコード内の地点に達すると、タスクは <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.IsBreakpointTargetEnabled%2A> メソッドを使用してブレークポイント ターゲットを評価し、そのブレークポイントが有効かどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-121">When the task reaches the point in its code that contains a breakpoint target, it evaluates the breakpoint target by using the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.IsBreakpointTargetEnabled%2A> method to determine whether that breakpoint is enabled.</span></span> <span data-ttu-id="abb5b-122">`true` の場合、タスクは <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> イベントを発生させて、ランタイム エンジンに通知します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-122">If `true`, the task notifies the run-time engine by raising the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> event.</span></span>  
  
 <span data-ttu-id="abb5b-123"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> インターフェイスは、タスクの作成中にランタイム エンジンによって呼び出される単一メソッド <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite.AcceptBreakpointManager%2A> を定義します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-123">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface defines a single method, <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite.AcceptBreakpointManager%2A>, which is called by the run-time engine during task creation.</span></span> <span data-ttu-id="abb5b-124">メソッドは、パラメーターとして <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> オブジェクトを提供し、このオブジェクトは各タスクでブレークポイントの作成や管理を行うために使用されます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-124">This method provides as a parameter the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> object, which is then used by the task to create and manage its breakpoints.</span></span> <span data-ttu-id="abb5b-125">タスクは <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> を `Validate` メソッドおよび `Execute` メソッドで使用するため、これをローカルで格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abb5b-125">Tasks should store the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> locally for use during the `Validate` and `Execute` methods.</span></span>  
  
 <span data-ttu-id="abb5b-126">次のサンプル コードでは、<xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> を使用してブレークポイント ターゲットを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-126">The following sample code demonstrates how to create a breakpoint target by using the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager>.</span></span> <span data-ttu-id="abb5b-127">このサンプルでは <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> メソッドを呼び出してイベントを起動します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-127">The sample calls the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> method to raise the event.</span></span>  
  
```csharp  
public void AcceptBreakpointManager( BreakpointManager breakPointManager )  
{  
   //   Store the breakpoint manager locally.  
   this.bpm  = breakPointManager;  
}  
public override DTSExecResult Execute( Connections connections,  
  Variables variables, IDTSComponentEvents events,  
  IDTSLogging log, DtsTransaction txn)  
{  
   //   Create a breakpoint.  
   this.bpm.CreateBreakPointTarget( 1 , "A sample breakpoint target." );  
...  
   if( this.bpm.IsBreakpointTargetEnabled( 1 ) == true )  
      events.OnBreakpointHit( this.bpm.GetBreakpointTarget( 1 ) );  
}  
```  
  
```vb  
Public Sub AcceptBreakpointManager(ByVal breakPointManager As BreakpointManager)  
  
   ' Store the breakpoint manager locally.  
   Me.bpm  = breakPointManager  
  
End Sub  
  
Public Overrides Function Execute(ByVal connections As Connections, _  
  ByVal variables As Variables, ByVal events As IDTSComponentEvents, _  
  ByVal log As IDTSLogging, ByVal txn As DtsTransaction) As DTSExecResult  
  
   ' Create a breakpoint.  
   Me.bpm.CreateBreakPointTarget(1 , "A sample breakpoint target.")  
  
   If Me.bpm.IsBreakpointTargetEnabled(1) = True Then  
      events.OnBreakpointHit(Me.bpm.GetBreakpointTarget(1))  
   End If  
  
End Function  
```  
  
## <a name="idtssuspend-interface"></a><span data-ttu-id="abb5b-128">IDTSSuspend インターフェイス</span><span class="sxs-lookup"><span data-stu-id="abb5b-128">IDTSSuspend Interface</span></span>  
 <span data-ttu-id="abb5b-129"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> インターフェイスは、タスクの実行が一時停止または再開されるときに、ランタイム エンジンによって呼び出されるメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-129">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interface defines the methods that are called by the run-time engine when it pauses or resumes execution of a task.</span></span> <span data-ttu-id="abb5b-130"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> インターフェイスは <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> インターフェイスによって実装され、この `Suspend` メソッドおよび `ResumeExecution` メソッドは、通常カスタム タスクによってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-130">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interface is implemented by the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface, and its `Suspend` and `ResumeExecution` methods are usually overridden by the custom task.</span></span> <span data-ttu-id="abb5b-131">ランタイム エンジンがタスクから `OnBreakpointHit` イベントを受け取ると、実行中の各タスクの `Suspend` メソッドを呼び出し、タスクに一時停止するよう通知します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-131">When the run-time engine receives an `OnBreakpointHit` event from a task, it calls the `Suspend` method of each running task, notifying the tasks to pause.</span></span> <span data-ttu-id="abb5b-132">クライアントが実行を再開すると、ランタイム エンジンは中断しているタスクの `ResumeExecution` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-132">When the client resumes execution, the run-time engine calls the `ResumeExecution` method of the tasks that are suspended.</span></span>  
  
 <span data-ttu-id="abb5b-133">タスクの実行が中断および再開されると、タスクの実行スレッドも一時停止および再開されます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-133">Suspending and resuming task execution involves pausing and resuming the task's execution thread.</span></span> <span data-ttu-id="abb5b-134">マネージド コードでは、これは、.NET Framework の `ManualResetEvent` 名前空間の `System.Threading` クラスを使用することにより実現されます。</span><span class="sxs-lookup"><span data-stu-id="abb5b-134">In managed code, you do this using the `ManualResetEvent` class in `System.Threading` namespace of the .NET Framework.</span></span>  
  
 <span data-ttu-id="abb5b-135">次のコード サンプルは、タスクの実行を中断および再開します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-135">The following code sample demonstrates suspension and resumption of task execution.</span></span> <span data-ttu-id="abb5b-136">`Execute` メソッドは上記のコード サンプルから変更され、ブレークポイントが発生すると実行スレッドが一時停止します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-136">Notice that the `Execute` method has changed from the previous code sample, and the execution thread is paused when firing the breakpoint.</span></span>  
  
```csharp  
private ManualResetEvent m_suspended = new ManualResetEvent( true );  
private ManualResetEvent m_canExecute = new ManualResetEvent( true );  
private int   m_suspendRequired = 0;  
private int   m_debugMode = 0;  
  
public override DTSExecResult Execute( Connections connections, Variables variables, IDTSComponentEvents events, IDTSLogging log, DtsTransaction txn)  
{  
   // While a task is not executing, it is suspended.    
   // Now that we are executing,  
   // change to not suspended.  
   ChangeEvent(m_suspended, false);  
  
   // Check for a suspend before doing any work,   
   // in case the suspend and execute calls  
   // were initiated at virtually the same time.  
   CheckAndSuspend();  
   CheckAndFireBreakpoint( componentEvents, 1);  
}  
private void CheckAndSuspend()  
{  
   // Loop until we can execute.    
   // The loop is required rather than a simple If  
   // because there is a time between the return from WaitOne and the  
   // reset that we might receive another Suspend call.    
   // Suspend() will see that we are suspended  
   // and return.  So we need to rewait.  
   while (!m_canExecute.WaitOne(0, false))  
   {  
      ChangeEvent(m_suspended, true);  
      m_canExecute.WaitOne();  
      ChangeEvent(m_suspended, false);  
   }  
}  
private void CheckAndFireBreakpoint(IDTSComponentEvents events, int breakpointID)  
{  
   // If the breakpoint is enabled, fire it.  
   if (m_debugMode != 0 &&    this.bpm.IsBreakpointTargetEnabled(breakpointID))  
   {  
      //   Enter a suspend mode before firing the breakpoint.    
      //   Firing the breakpoint will cause the runtime   
      //   to call Suspend on this task.    
      //   Because we are blocked on the breakpoint,   
      //   we are suspended.  
      ChangeEvent(m_suspended, true);  
      events.OnBreakpointHit(this.bpm.GetBreakpointTarget(breakpointID));  
      ChangeEvent(m_suspended, false);  
   }  
   // Check for a suspension for two reasons:   
   //   1. If we are at a point where we could fire a breakpoint,   
   //      we are at a valid suspend point.  Even if we didn't hit a  
   //      breakpoint, the runtime may have called suspend,   
   //      so check for it.       
   //   2. Between the return from OnBreakpointHit   
   //      and the reset of the event, it is possible to have  
   //      received a suspend call from which we returned because   
   //      we were already suspended.  We need to be sure it is okay  
   //      to continue executing now.  
   CheckAndSuspend();  
}  
static void ChangeEvent(ManualResetEvent e, bool shouldSet)  
{  
   bool succeeded;  
   if (shouldSet)  
      succeeded = e.Set();  
   else  
      succeeded = e.Reset();  
  
   if (!succeeded)  
      throw new Exception("Synchronization object failed.");  
  
}  
public bool SuspendRequired  
{  
   get   {return m_suspendRequired != 0;}  
   set  
   {  
      // This lock is also taken by Suspend().    
      // Because it is possible for the package to be  
      // suspended and resumed in quick succession,   
      // this property might be set before  
      // the actual Suspend() call.    
      // Without the lock, the Suspend() might reset the canExecute  
      // event after we set it to abort the suspension.  
      lock (this)  
      {  
         Interlocked.Exchange(ref m_suspendRequired, value ? 1 : 0);  
         if (!value)  
            ResumeExecution();  
      }  
   }  
}  
public void ResumeExecution()  
{  
   ChangeEvent( m_canExecute,true );  
}  
public void Suspend()  
{  
   // This lock is also taken by the set SuspendRequired method.    
   // It prevents this call from overriding an   
   // aborted suspension.  See comments in set SuspendRequired.  
   lock (this)  
   {  
      // If a Suspend is required, do it.  
      if (m_suspendRequired != 0)  
         ChangeEvent(m_canExecute, false);  
   }  
   // We can't return from Suspend until the task is "suspended".  
   // This can happen one of two ways:   
   // the m_suspended event occurs, indicating that the execute thread  
   // has suspended, or the canExecute flag is set,   
   // indicating that a suspend is no longer required.  
   WaitHandle [] suspendOperationComplete = {m_suspended, m_canExecute};  
   WaitHandle.WaitAny(suspendOperationComplete);  
}  
```  
  
```vb  
Private m_suspended As ManualResetEvent = New ManualResetEvent(True)  
Private m_canExecute As ManualResetEvent = New ManualResetEvent(True)  
Private m_suspendRequired As Integer = 0  
Private m_debugMode As Integer = 0  
  
Public Overrides Function Execute(ByVal connections As Connections, _  
ByVal variables As Variables, ByVal events As IDTSComponentEvents, _  
ByVal log As IDTSLogging, ByVal txn As DtsTransaction) As DTSExecResult  
  
   ' While a task is not executing it is suspended.    
   ' Now that we are executing,  
   ' change to not suspended.  
   ChangeEvent(m_suspended, False)  
  
   ' Check for a suspend before doing any work,   
   ' in case the suspend and execute calls  
   ' were initiated at virtually the same time.  
   CheckAndSuspend()  
   CheckAndFireBreakpoint(componentEvents, 1)  
  
End Function  
  
Private Sub CheckAndSuspend()  
  
   ' Loop until we can execute.    
   ' The loop is required rather than a simple if  
   ' because there is a time between the return from WaitOne and the  
   ' reset that we might receive another Suspend call.    
   ' Suspend() will see that we are suspended  
   ' and return.  So we need to rewait.  
   Do While Not m_canExecute.WaitOne(0, False)  
              ChangeEvent(m_suspended, True)  
              m_canExecute.WaitOne()  
              ChangeEvent(m_suspended, False)  
   Loop  
  
End Sub  
  
Private Sub CheckAndFireBreakpoint(ByVal events As IDTSComponentEvents, _  
ByVal breakpointID As Integer)  
  
   ' If the breakpoint is enabled, fire it.  
   If m_debugMode <> 0 AndAlso Me.bpm.IsBreakpointTargetEnabled(breakpointID) Then  
              '   Enter a suspend mode before firing the breakpoint.    
              '   Firing the breakpoint will cause the runtime   
              '   to call Suspend on this task.    
              '   Because we are blocked on the breakpoint,   
              '   we are suspended.  
              ChangeEvent(m_suspended, True)  
              events.OnBreakpointHit(Me.bpm.GetBreakpointTarget(breakpointID))  
              ChangeEvent(m_suspended, False)  
   End If  
  
   ' Check for a suspension for two reasons:   
   '   1. If we are at a point where we could fire a breakpoint,   
   '         we are at a valid suspend point.  Even if we didn't hit a  
   '         breakpoint, the runtime may have called suspend,   
   '         so check for it.     
   '   2. Between the return from OnBreakpointHit   
   '         and the reset of the event, it is possible to have  
   '         received a suspend call from which we returned because   
   '         we were already suspended.  We need to be sure it is okay  
   '         to continue executing now.  
   CheckAndSuspend()  
  
End Sub  
  
Shared Sub ChangeEvent(ByVal e As ManualResetEvent, ByVal shouldSet As Boolean)  
  
   Dim succeeded As Boolean  
   If shouldSet Then  
              succeeded = e.Set()  
   Else  
              succeeded = e.Reset()  
   End If  
  
   If (Not succeeded) Then  
              Throw New Exception("Synchronization object failed.")  
   End If  
  
End Sub  
  
Public Property SuspendRequired() As Boolean  
   Get  
               Return m_suspendRequired <> 0  
  End Get  
  Set  
    ' This lock is also taken by Suspend().    
     '   Because it is possible for the package to be  
     '   suspended and resumed in quick succession,   
     '   this property might be set before  
     '   the actual Suspend() call.    
     '   Without the lock, the Suspend() might reset the canExecute  
     '   event after we set it to abort the suspension.  
              SyncLock Me  
                         Interlocked.Exchange(m_suspendRequired,IIf(Value, 1, 0))  
                         If (Not Value) Then  
                                    ResumeExecution()  
                         End If  
              End SyncLock  
   End Set  
End Property  
  
Public Sub ResumeExecution()  
   ChangeEvent(m_canExecute,True)  
End Sub  
  
Public Sub Suspend()  
  
   ' This lock is also taken by the set SuspendRequired method.    
   ' It prevents this call from overriding an   
   ' aborted suspension.  See comments in set SuspendRequired.  
   SyncLock Me  
   ' If a Suspend is required, do it.  
              If m_suspendRequired <> 0 Then  
                         ChangeEvent(m_canExecute, False)  
              End If  
   End SyncLock  
   ' We can't return from Suspend until the task is "suspended".  
   ' This can happen one of two ways:   
   ' the m_suspended event occurs, indicating that the execute thread  
   ' has suspended, or the canExecute flag is set,   
   ' indicating that a suspend is no longer required.  
   Dim suspendOperationComplete As WaitHandle() = {m_suspended, m_canExecute}  
   WaitHandle.WaitAny(suspendOperationComplete)  
  
End Sub  
```  
  
<span data-ttu-id="abb5b-137">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="abb5b-137">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="abb5b-138">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="abb5b-138">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="abb5b-139">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="abb5b-139">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="abb5b-140">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="abb5b-140">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb5b-141">参照</span><span class="sxs-lookup"><span data-stu-id="abb5b-141">See Also</span></span>  
 [<span data-ttu-id="abb5b-142">制御フローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="abb5b-142">Debugging Control Flow</span></span>](../../troubleshooting/debugging-control-flow.md)  
  
  
