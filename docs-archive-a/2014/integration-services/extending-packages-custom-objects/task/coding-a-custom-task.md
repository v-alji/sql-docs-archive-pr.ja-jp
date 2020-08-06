---
title: カスタム タスクのコーディング | Microsoft Docs
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
- Validate method
- custom tasks [Integration Services], validating
- validation [Integration Services], design-time tasks
- SSIS custom tasks, validating
ms.assetid: dc224f4f-b339-4eb6-a008-1b4fe0ea4fd2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c369f4a7e8352be7ddde9e2e3938b47b0bcc1349
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642187"
---
# <a name="coding-a-custom-task"></a><span data-ttu-id="d817d-102">カスタム タスクのコーディング</span><span class="sxs-lookup"><span data-stu-id="d817d-102">Coding a Custom Task</span></span>
  <span data-ttu-id="d817d-103">[Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基本クラスを継承するクラスを作成し、<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性をそのクラスに適用したら、基本クラスのプロパティとメソッドの実装をオーバーライドして、カスタム機能を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d817d-103">After you have created a class that inherits from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>

## <a name="configuring-the-task"></a><span data-ttu-id="d817d-104">タスクの構成</span><span class="sxs-lookup"><span data-stu-id="d817d-104">Configuring the Task</span></span>

### <a name="validating-the-task"></a><span data-ttu-id="d817d-105">タスクの検証</span><span class="sxs-lookup"><span data-stu-id="d817d-105">Validating the Task</span></span>
 <span data-ttu-id="d817d-106">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージのデザイン中に検証機能を使用して各タスクの設定を確認できるため、すべてのエラーを実行時にのみ見つけるのではなく、無効または不適切な設定が行われた場合、すぐにその問題を確認できます。</span><span class="sxs-lookup"><span data-stu-id="d817d-106">When you are designing an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package, you can use validation to verify settings on each task, so that you can catch incorrect or inappropriate settings as soon as they are set, instead of finding all errors at run-time only.</span></span> <span data-ttu-id="d817d-107">検証の目的は、タスクの正常な実行を妨げる無効な設定または接続が、タスクに含まれているかどうかを判別することです。</span><span class="sxs-lookup"><span data-stu-id="d817d-107">The purpose of validation is to determine whether the task contains invalid settings or connections that will prevent it from running successfully.</span></span> <span data-ttu-id="d817d-108">これによって、パッケージに含まれるタスクは、初回から正しく実行される可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="d817d-108">This makes sure that the package contains tasks that have a good chance of running on their first run.</span></span>

 <span data-ttu-id="d817d-109">検証機能は、カスタム コード内で `Validate` メソッドを使用することによって実装できます。</span><span class="sxs-lookup"><span data-stu-id="d817d-109">You can implement validation by using the `Validate` method in custom code.</span></span> <span data-ttu-id="d817d-110">ランタイム エンジンは、タスク上の `Validate` メソッドを呼び出すことにより、タスクを検証します。</span><span class="sxs-lookup"><span data-stu-id="d817d-110">The run-time engine validates a task by calling the `Validate` method on the task.</span></span> <span data-ttu-id="d817d-111">タスクの開発者は、タスクの検証が成功または失敗する条件を定義し、評価の結果をランタイム エンジンに通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d817d-111">It is the responsibility of the task developer to define the criteria that give you a successful or failed task validation, and to notify the run-time engine of the result of this evaluation.</span></span>

#### <a name="task-abstract-base-class"></a><span data-ttu-id="d817d-112">タスクの抽象基本クラス</span><span class="sxs-lookup"><span data-stu-id="d817d-112">Task Abstract Base Class</span></span>
 <span data-ttu-id="d817d-113">[Microsoft の SqlServer. Runtime. task](/dotnet/api/microsoft.sqlserver.dts.runtime.task)抽象基本クラスには、 `Validate` 各タスクがオーバーライドして検証条件を定義するメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d817d-113">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) abstract base class provides the `Validate` method that each task overrides to define its validation criteria.</span></span> <span data-ttu-id="d817d-114">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーは、パッケージのデザイン中、`Validate` メソッドを自動的に複数回呼び出します。さらに、警告またはエラーが発生した場合はユーザーに画面上で通知し、タスクの構成に関する問題を識別できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d817d-114">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer automatically calls the `Validate` method multiple times during package design, and provides visual cues to the user when warnings or errors occur to help identify problems with the configuration of the task.</span></span> <span data-ttu-id="d817d-115">タスクは、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 列挙から値を返し、警告およびエラー イベントを発生させることにより、検証結果を返します。</span><span class="sxs-lookup"><span data-stu-id="d817d-115">Tasks provide validation results by returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration, and by raising warning and error events.</span></span> <span data-ttu-id="d817d-116">これらのイベントには、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでユーザーに表示される情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d817d-116">These events contain information that is displayed to the user in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="d817d-117">次に、いくつかの検証の例を挙げます。</span><span class="sxs-lookup"><span data-stu-id="d817d-117">Some examples for validation follow:</span></span>

-   <span data-ttu-id="d817d-118">接続マネージャーは、特定のファイル名を検証します。</span><span class="sxs-lookup"><span data-stu-id="d817d-118">A connection manager validates the specific file name.</span></span>

-   <span data-ttu-id="d817d-119">接続マネージャーは、入力の種類が XML ファイルなどの必要な種類であることを検証します。</span><span class="sxs-lookup"><span data-stu-id="d817d-119">A connection manager validates that the type of input is the expected type, such as an XML file.</span></span>

-   <span data-ttu-id="d817d-120">データベースの入力が必要なタスクは、データベース以外の接続からデータを受け取れないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d817d-120">A task that expects database input verifies that it cannot receive data from a non-database connection.</span></span>

-   <span data-ttu-id="d817d-121">タスクは、タスクのどのプロパティも、同じタスクに設定された他のプロパティと矛盾していないことを保証します。</span><span class="sxs-lookup"><span data-stu-id="d817d-121">A task guarantees that none of its properties contradicts other properties set on the same task.</span></span>

-   <span data-ttu-id="d817d-122">タスクは、タスクが使用する必要なすべてのリソースが実行時に使用できることを保証します。</span><span class="sxs-lookup"><span data-stu-id="d817d-122">A task guarantees that all required resources used by the task at execution time are available.</span></span>

 <span data-ttu-id="d817d-123">検証する項目としない項目を決定する際には、パフォーマンスを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d817d-123">Performance is something to consider in determining what is validated and what is not.</span></span> <span data-ttu-id="d817d-124">たとえば、タスクへの入力で、低帯域またはトラフィックが混雑しているネットワーク経由の接続が使用されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d817d-124">For example, the input to a task might be a connection over a network that has low bandwidth or heavy traffic.</span></span> <span data-ttu-id="d817d-125">その場合、リソースが使用可能かを検証する処理には、数秒かかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d817d-125">The validation may take several seconds to process if you decide to validate that the resource is available.</span></span> <span data-ttu-id="d817d-126">別の検証では要求処理量が多いサーバーへのラウンド トリップが発生し、検証ルーチンの速度が遅くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d817d-126">Another validation may cause a round-trip to a server that is in high demand, and the validation routine might be slow.</span></span> <span data-ttu-id="d817d-127">検証可能なプロパティや設定は多数ありますが、すべてを検証するべきではありません。</span><span class="sxs-lookup"><span data-stu-id="d817d-127">Although there are many properties and settings that can be validated, not everything should be validated.</span></span>

-   <span data-ttu-id="d817d-128">`Validate` メソッド内のコードは、タスクの実行前に <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> によっても呼び出され、検証が失敗した場合は <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> の実行が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-128">The code in the `Validate` method is also called by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> before the task is run, and the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> cancels execution if validation fails.</span></span>

#### <a name="user-interface-considerations-during-validation"></a><span data-ttu-id="d817d-129">検証時のユーザー インターフェイスについての検討事項</span><span class="sxs-lookup"><span data-stu-id="d817d-129">User Interface Considerations during Validation</span></span>
 <span data-ttu-id="d817d-130">このメソッドに[は、](/dotnet/api/microsoft.sqlserver.dts.runtime.task) <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> パラメーターとしてインターフェイスが含まれています。 `Validate`</span><span class="sxs-lookup"><span data-stu-id="d817d-130">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) includes an <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface as a parameter to the `Validate` method.</span></span> <span data-ttu-id="d817d-131"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> インターフェイスには、イベントをランタイム エンジンに送るためにタスクが呼び出すメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d817d-131">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface contains the methods that are called by the task in order to raise events to the run-time engine.</span></span> <span data-ttu-id="d817d-132">検証中に警告またはエラー条件が発生すると、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> および <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-132">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods are called when a warning or error condition occurs during validation.</span></span> <span data-ttu-id="d817d-133">どちらの警告メソッドにも、エラー コード、ソース コンポーネント、説明、ヘルプ ファイル、ヘルプ コンテキスト情報などの同じパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="d817d-133">Both warning methods require the same parameters, which include an error code, source component, description, Help file, and Help context information.</span></span> <span data-ttu-id="d817d-134">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーはこの情報に基づいて、エラーの発生をデザイン画面上で視覚的に通知します。</span><span class="sxs-lookup"><span data-stu-id="d817d-134">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses this information to display visual cues on the design surface.</span></span> <span data-ttu-id="d817d-135">デザイナーによって提供される視覚的な通知には、デザイン画面上のタスクの横に表示される感嘆符のアイコンがあります。</span><span class="sxs-lookup"><span data-stu-id="d817d-135">The visual cues that are provided by the designer include an exclamation icon that appears next to the task on the designer surface.</span></span> <span data-ttu-id="d817d-136">この視覚的通知は、実行を続けるにはタスクの構成を追加する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="d817d-136">This visual cue signals to the user that the task requires additional configuration before execution can continue.</span></span>

 <span data-ttu-id="d817d-137">感嘆符のアイコンによって、エラー メッセージを含むツールヒントも表示されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-137">The exclamation icon also displays a ToolTip that contains an error message.</span></span> <span data-ttu-id="d817d-138">エラー メッセージは、タスクによってイベントの説明パラメーターに提供されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-138">The error message is provided by the task in the description parameter of the event.</span></span> <span data-ttu-id="d817d-139">エラー メッセージは、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] の **[タスク一覧]** ペインにも表示されます。このペインは、すべての検証エラーを表示するための集中管理場所となります。</span><span class="sxs-lookup"><span data-stu-id="d817d-139">Error messages are also displayed in the **Task List** pane of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], providing the user with a central location for viewing all validation errors.</span></span>

#### <a name="validation-example"></a><span data-ttu-id="d817d-140">検証例</span><span class="sxs-lookup"><span data-stu-id="d817d-140">Validation Example</span></span>
 <span data-ttu-id="d817d-141">次のコード例は、`UserName` プロパティを使用したタスクを示しています。</span><span class="sxs-lookup"><span data-stu-id="d817d-141">The following code example shows a task with a `UserName` property.</span></span> <span data-ttu-id="d817d-142">このプロパティは、検証に必要なものとして指定されています。</span><span class="sxs-lookup"><span data-stu-id="d817d-142">This property has been specified as required for validation to succeed.</span></span> <span data-ttu-id="d817d-143">このプロパティが設定されていない場合、タスクはエラーを通知し、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> 列挙から <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> を返します。</span><span class="sxs-lookup"><span data-stu-id="d817d-143">If the property is not set, the task posts an error, and returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration.</span></span> <span data-ttu-id="d817d-144">例外が発生すると、`Validate` メソッドは try/catch ブロックにラップされ、検証は失敗します。</span><span class="sxs-lookup"><span data-stu-id="d817d-144">The `Validate` method is wrapped in a try/catch block, and fails validation if an exception occurs.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

public class SampleTask : Task
{
  private string userName = "";

  public override DTSExecResult Validate(Connections connections,
     VariableDispenser variableDispenser, IDTSComponentEvents events,
     IDTSLogging log)
  {
    try
    {
      if (this.userName == "")
      {
        //   Raise an OnError event.
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0);
        //   Fail validation.
        return DTSExecResult.Failure;
      }
      //   Return success.
      return DTSExecResult.Success;
    }
    catch (System.Exception exception)
    {
      //   Capture exceptions, post an error, and fail validation.
      events.FireError(0, "Sampletask", exception.Message, "", 0);
      return DTSExecResult.Failure;
    }
  }
  public string UserName
  {
    get
    {
      return this.userName;
    }
    set
    {
      this.userName = value;
    }
  }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Runtime

Public Class SampleTask
  Inherits Task

  Private _userName As String = ""

  Public Overrides Function Validate(ByVal connections As Connections, _
     ByVal variableDispenser As VariableDispenser, _
     ByVal events As IDTSComponentEvents, _
     ByVal log As IDTSLogging) As DTSExecResult

    Try
      If Me._userName = "" Then
        '   Raise an OnError event.
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0)
        '   Fail validation.
        Return DTSExecResult.Failure
      End If
      '   Return success.
      Return DTSExecResult.Success
    Catch exception As System.Exception
      '   Capture exceptions, post an error, and fail validation.
      events.FireError(0, "Sampletask", exception.Message, "", 0)
      Return DTSExecResult.Failure
    End Try

  End Function

  Public Property UserName() As String
    Get
      Return Me._userName
    End Get
    Set(ByVal Value As String)
      Me._userName = Value
    End Set
  End Property

End Class
```

### <a name="persisting-the-task"></a><span data-ttu-id="d817d-145">タスクの保存</span><span class="sxs-lookup"><span data-stu-id="d817d-145">Persisting the Task</span></span>
 <span data-ttu-id="d817d-146">通常、タスクに対して、カスタムの永続性を実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d817d-146">Ordinarily you do not have to implement custom persistence for a task.</span></span> <span data-ttu-id="d817d-147">カスタムの永続性は、オブジェクトのプロパティで複合データ型が使用されている場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="d817d-147">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="d817d-148">詳細については、「[Integration Services 用のカスタム オブジェクトの開発](../developing-custom-objects-for-integration-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d817d-148">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>

## <a name="executing-the-task"></a><span data-ttu-id="d817d-149">タスクの実行</span><span class="sxs-lookup"><span data-stu-id="d817d-149">Executing the Task</span></span>
 <span data-ttu-id="d817d-150">このセクションでは、タスクによって継承およびオーバーライドされる `Execute` メソッドの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d817d-150">This section describes how to use the `Execute` method that is inherited and overridden by tasks.</span></span> <span data-ttu-id="d817d-151">また、タスクの実行結果についての情報を提供するさまざまな方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="d817d-151">This section also explains various ways of providing information about the results of task execution.</span></span>

### <a name="execute-method"></a><span data-ttu-id="d817d-152">Execute メソッド</span><span class="sxs-lookup"><span data-stu-id="d817d-152">Execute Method</span></span>
 <span data-ttu-id="d817d-153">パッケージに含まれるタスクは、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のランタイムが `Execute` メソッドを呼び出すと実行されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-153">Tasks that are contained in a package run when the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime calls their `Execute` method.</span></span> <span data-ttu-id="d817d-154">タスクは、中心となるビジネス ロジックや機能をこのメソッドに実装し、メッセージを送信したり、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 列挙から値を返したり、`get` プロパティの `ExecutionValue` プロパティをオーバーライドしたりする方法で、実行結果を返します。</span><span class="sxs-lookup"><span data-stu-id="d817d-154">Tasks implement their core business logic and functionality in this method, and provide the results of execution by posting messages, returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration, and overriding the property `get` of the `ExecutionValue` property.</span></span>

 <span data-ttu-id="d817d-155">[Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基本クラスには、既定で <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> メソッドが実装されています。</span><span class="sxs-lookup"><span data-stu-id="d817d-155">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class provides a default implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span> <span data-ttu-id="d817d-156">カスタム タスクは、実行時の機能を定義するために、このメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="d817d-156">The custom tasks override this method to define their run-time functionality.</span></span> <span data-ttu-id="d817d-157"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> オブジェクトはタスクをラップし、ランタイム エンジンやパッケージ内の他のオブジェクトと分離します。</span><span class="sxs-lookup"><span data-stu-id="d817d-157">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object wraps the task, isolating it from the run-time engine and the other objects in the package.</span></span> <span data-ttu-id="d817d-158">そのため、タスクはパッケージ内での実行順序に関する位置を認識しているわけではなく、ランタイムによって呼び出されたときにのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-158">Because of this isolation, the task is unaware of its location in the package with regard to its execution order, and runs only when it is called by the runtime.</span></span> <span data-ttu-id="d817d-159">このアーキテクチャにより、実行中にタスクがパッケージを変更したときに発生する問題が回避されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-159">This architecture prevents problems that can occur when tasks modify the package during execution.</span></span> <span data-ttu-id="d817d-160">タスクがパッケージ内の他のオブジェクトにアクセスするには、<xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> メソッド内のパラメーターとして用意されているオブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d817d-160">The task is provided access to the other objects in the package only through the objects supplied to it as parameters in the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span> <span data-ttu-id="d817d-161">これらのパラメーターを使用すると、パッケージの安定度と信頼性を保証するために必要な分離性を保ちながら、イベントの発生、イベント ログへのエントリの記録、変数コレクションへのアクセス、およびトランザクション内のデータ ソースへの接続の登録を、タスクに実行させることができます。</span><span class="sxs-lookup"><span data-stu-id="d817d-161">These parameters let tasks raise events, write entries to the event log, access the variables collection, and enlist connections to data sources in transactions, while still maintaining the isolation that is necessary to guarantee the stability and reliability of the package.</span></span>

 <span data-ttu-id="d817d-162">次の表は、<xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> メソッド内のタスクに対して提供されるパラメーターの一覧です。</span><span class="sxs-lookup"><span data-stu-id="d817d-162">The following table lists the parameters provided to the task in the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span>

|<span data-ttu-id="d817d-163">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d817d-163">Parameter</span></span>|<span data-ttu-id="d817d-164">説明</span><span class="sxs-lookup"><span data-stu-id="d817d-164">Description</span></span>|
|---------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Runtime.Connections>|<span data-ttu-id="d817d-165">タスクで使用できる <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトのコレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="d817d-165">Contains a collection of <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects available to the task.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.VariableDispenser>|<span data-ttu-id="d817d-166">タスクで使用できる変数を含みます。</span><span class="sxs-lookup"><span data-stu-id="d817d-166">Contains the variables available to the task.</span></span> <span data-ttu-id="d817d-167">タスクは、VariableDispenser を介して変数を使用します。変数を直接使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="d817d-167">The tasks use variables through the VariableDispenser; the tasks do not use variables directly.</span></span> <span data-ttu-id="d817d-168">変数ディスペンサーには、変数をロックまたはロック解除したり、デッドロックや上書きを防ぐ機能があります。</span><span class="sxs-lookup"><span data-stu-id="d817d-168">The variable dispenser locks and unlocks variables, and prevents deadlocks or overwrites.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>|<span data-ttu-id="d817d-169">イベントを生成してランタイム エンジンに送るためにタスクが呼び出すメソッドを含みます。</span><span class="sxs-lookup"><span data-stu-id="d817d-169">Contains the methods called by the task to raise events to the run-time engine.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSLogging>|<span data-ttu-id="d817d-170">イベント ログにエントリを記録するためにタスクが使用するメソッドおよびプロパティを含みます。</span><span class="sxs-lookup"><span data-stu-id="d817d-170">Contains methods and properties used by the task to write entries to the event log.</span></span>|
|<span data-ttu-id="d817d-171">Object</span><span class="sxs-lookup"><span data-stu-id="d817d-171">Object</span></span>|<span data-ttu-id="d817d-172">トランザクション オブジェクトの一部がコンテナーである場合、そのオブジェクトを含みます。</span><span class="sxs-lookup"><span data-stu-id="d817d-172">Contains the transaction object that the container is a part of, if any.</span></span> <span data-ttu-id="d817d-173">この値はパラメーターとして、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> オブジェクトの <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-173">This value is passed as a parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of a <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object.</span></span>|

### <a name="providing-execution-feedback"></a><span data-ttu-id="d817d-174">実行結果のフィードバックの送信</span><span class="sxs-lookup"><span data-stu-id="d817d-174">Providing Execution Feedback</span></span>
 <span data-ttu-id="d817d-175">タスクは、タスクのコードを `try/catch` ブロックにラップし、ランタイム エンジンに例外が発生するのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="d817d-175">Tasks wrap their code in `try/catch` blocks to prevent exceptions from being raised to the run-time engine.</span></span> <span data-ttu-id="d817d-176">これにより、パッケージは予期せず停止することなく、実行を完了します。</span><span class="sxs-lookup"><span data-stu-id="d817d-176">This ensures that the package finishes execution and does not stop unexpectedly.</span></span> <span data-ttu-id="d817d-177">ランタイム エンジンには、タスクの実行中に発生する可能性のあるエラー条件を処理するメカニズムが他にも用意されています。</span><span class="sxs-lookup"><span data-stu-id="d817d-177">However, the run-time engine provides other mechanisms for handling error conditions that can occur during the execution of a task.</span></span> <span data-ttu-id="d817d-178">このメカニズムには、エラー メッセージや警告メッセージの通知、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 構造からの戻り値、メッセージの通知、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> の戻り値、<xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A> プロパティによるタスクの実行結果に関する情報の公開などが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d817d-178">These include posting error and warning messages, returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> structure, posting messages, returning the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value, and disclosing information about the results of task execution through the <xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A> property.</span></span>

 <span data-ttu-id="d817d-179"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> インターフェイスには、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> メソッドがあり、タスクはこれらを呼び出して、エラー メッセージや警告メッセージをランタイム エンジンに通知できます。</span><span class="sxs-lookup"><span data-stu-id="d817d-179">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface contains the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods, which can be called by the task to post error and warning messages to the run-time engine.</span></span> <span data-ttu-id="d817d-180">どちらのメソッドにも、エラー コード、ソース コンポーネント、説明、ヘルプ ファイル、ヘルプ コンテキスト情報などのパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="d817d-180">Both methods require parameters such as the error code, source component, description, Help file, and help context information.</span></span> <span data-ttu-id="d817d-181">タスクの構成に応じて、ランタイムは、イベントやブレークポイントを発生させたり、イベント ログに情報を記録したりする方法で、これらのメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="d817d-181">Depending on the configuration of the task, the runtime responds to these messages by raising events and breakpoints, or by writing information to the event log.</span></span>

 <span data-ttu-id="d817d-182"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> は、実行結果に関する追加情報を提供するために使用可能な <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> プロパティも提供します。</span><span class="sxs-lookup"><span data-stu-id="d817d-182">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> also provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property that can be used to provide additional information about the results of execution.</span></span> <span data-ttu-id="d817d-183">たとえば、タスクがその `Execute` メソッドの一部としてテーブルから行を削除すると、削除された行数は <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> プロパティの値として返されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-183">For example, if a task deletes rows from a table as part of its `Execute` method, it might return the number of rows deleted as the value of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property.</span></span> <span data-ttu-id="d817d-184">また、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> は <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A> プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="d817d-184">In addition, the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A> property.</span></span> <span data-ttu-id="d817d-185">ユーザーはこのプロパティを使用して、タスクから返された <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> を、タスクで認識可能な任意の変数にマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="d817d-185">This property lets the user map the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> returned from the task to any variable visible to the task.</span></span> <span data-ttu-id="d817d-186">指定した変数を使用して、タスク間の優先順位制約を確立できます。</span><span class="sxs-lookup"><span data-stu-id="d817d-186">The specified variable can then be used to establish precedence constraints between tasks.</span></span>

### <a name="execution-example"></a><span data-ttu-id="d817d-187">実行例</span><span class="sxs-lookup"><span data-stu-id="d817d-187">Execution Example</span></span>
 <span data-ttu-id="d817d-188">次のコード例では、`Execute` メソッドを実装する方法、およびオーバーライドされた `ExecutionValue` プロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="d817d-188">The following code example demonstrates an implementation of the `Execute` method, and shows an overridden `ExecutionValue` property.</span></span> <span data-ttu-id="d817d-189">このタスクでは、タスクの `fileName` プロパティで指定されたファイルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="d817d-189">The task deletes the file that is specified by the `fileName` property of the task.</span></span> <span data-ttu-id="d817d-190">ファイルが存在しない場合、または `fileName` プロパティが空の文字列である場合、タスクは警告メッセージを通知します。</span><span class="sxs-lookup"><span data-stu-id="d817d-190">The task posts a warning if the file does not exist, or if the `fileName` property is an empty string.</span></span> <span data-ttu-id="d817d-191">タスクは、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> プロパティで、ファイルが削除されたかどうかを示す `Boolean` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="d817d-191">The task returns a `Boolean` value in the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property to indicate whether the file was deleted.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

public class SampleTask : Task
{
  private string fileName = "";
  private bool fileDeleted = false;

  public override DTSExecResult Execute(Connections cons,
     VariableDispenser vars, IDTSComponentEvents events,
     IDTSLogging log, Object txn)
  {
    try
    {
      if (this.fileName == "")
      {
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0);
        this.fileDeleted = false;
      }
      else
      {
        if (System.IO.File.Exists(this.fileName))
        {
          System.IO.File.Delete(this.fileName);
          this.fileDeleted = true;
        }
        else
          this.fileDeleted = false;
      }
      return DTSExecResult.Success;
    }
    catch (System.Exception exception)
    {
      //   Capture the exception and post an error.
      events.FireError(0, "Sampletask", exception.Message, "", 0);
      return DTSExecResult.Failure;
    }
  }
  public string FileName
  {
    get { return this.fileName; }
    set { this.fileName = value; }
  }
  public override object ExecutionValue
  {
    get { return this.fileDeleted; }
  }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Runtime

Public Class SampleTask
  Inherits Task

  Private _fileName As String = ""
  Private _fileDeleted As Boolean = False

  Public Overrides Function Execute(ByVal cons As Connections, _
     ByVal vars As VariableDispenser, ByVal events As IDTSComponentEvents, _
     ByVal log As IDTSLogging, ByVal txn As Object) As DTSExecResult

    Try
      If Me._fileName = "" Then
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0)
        Me._fileDeleted = False
      Else
        If System.IO.File.Exists(Me._fileName) Then
          System.IO.File.Delete(Me._fileName)
          Me._fileDeleted = True
        Else
          Me._fileDeleted = False
        End If
      End If
      Return DTSExecResult.Success
    Catch exception As System.Exception
      '   Capture the exception and post an error.
      events.FireError(0, "Sampletask", exception.Message, "", 0)
      Return DTSExecResult.Failure
    End Try

  End Function

  Public Property FileName() As String
    Get
      Return Me._fileName
    End Get
    Set(ByVal Value As String)
      Me._fileName = Value
    End Set
  End Property

  Public Overrides ReadOnly Property ExecutionValue() As Object
    Get
      Return Me._fileDeleted
    End Get
  End Property

End Class
```

<span data-ttu-id="d817d-192">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="d817d-192">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d817d-193">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d817d-193">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d817d-194">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="d817d-194">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d817d-195">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="d817d-195">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="d817d-196">参照</span><span class="sxs-lookup"><span data-stu-id="d817d-196">See Also</span></span>
 <span data-ttu-id="d817d-197">カスタムタスクの[作成](creating-a-custom-task.md)カスタムタスクの[コーディング](coding-a-custom-task.md)カスタムタスク[のユーザーインターフェイスの開発](developing-a-user-interface-for-a-custom-task.md)</span><span class="sxs-lookup"><span data-stu-id="d817d-197">[Creating a Custom Task](creating-a-custom-task.md) [Coding a Custom Task](coding-a-custom-task.md) [Developing a User Interface for a Custom Task](developing-a-user-interface-for-a-custom-task.md)</span></span>


