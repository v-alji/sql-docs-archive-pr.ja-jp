---
title: プログラムによるタスクの接続 | Microsoft Docs
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
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- constraints [Integration Services]
ms.assetid: 23668e88-cef4-4009-a9cf-38e607eab7a2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5aeeb70ed5741cc7372fdfc63e637fd53d932f91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639606"
---
# <a name="connecting-tasks-programmatically"></a><span data-ttu-id="c1227-102">プログラムによるタスクの接続</span><span class="sxs-lookup"><span data-stu-id="c1227-102">Connecting Tasks Programmatically</span></span>
  <span data-ttu-id="c1227-103">優先順位制約は、<xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> クラスとしてオブジェクト モデル内に表されるもので、パッケージ内での <xref:Microsoft.SqlServer.Dts.Runtime.Executable> オブジェクトの実行順序を確立します。</span><span class="sxs-lookup"><span data-stu-id="c1227-103">A precedence constraint, represented in the object model by the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> class, establishes the order in which <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects run in a package.</span></span> <span data-ttu-id="c1227-104">優先順位制約を使用すると、パッケージ内のコンテナーやタスクを、直前のコンテナーやタスクの実行結果に依存して実行させることができます。</span><span class="sxs-lookup"><span data-stu-id="c1227-104">The precedence constraint allows the execution of the containers and tasks in a package to be dependent on the result of the execution of a previous task or container.</span></span> <span data-ttu-id="c1227-105">2 つの <xref:Microsoft.SqlServer.Dts.Runtime.Executable> オブジェクト間の優先順位制約は、コンテナー オブジェクトの <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> コレクションにある <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> メソッドを呼び出すことによって確立されます。</span><span class="sxs-lookup"><span data-stu-id="c1227-105">Precedence constraints are established between pairs of <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects by calling the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> collection on the container object.</span></span> <span data-ttu-id="c1227-106">2 つの実行可能オブジェクト間の制約を作成したら、<xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> プロパティを設定して、制約で定義されている 2 番目の実行可能オブジェクトを実行する条件を設定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-106">After you create a constraint between two executable objects, you set the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> property to establish the criteria for executing the second executable defined in the constraint.</span></span>  
  
 <span data-ttu-id="c1227-107">次の表で説明するように、<xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A> プロパティに指定する値に応じて、1 つの優先順位制約内で制約と式の両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1227-107">You can use both a constraint and an expression in a single precedence constraint, depending on the value that you specify for the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A> property, as described in the following table:</span></span>  
  
|<span data-ttu-id="c1227-108">EvalOp プロパティの値</span><span class="sxs-lookup"><span data-stu-id="c1227-108">Value of the EvalOp property</span></span>|<span data-ttu-id="c1227-109">説明</span><span class="sxs-lookup"><span data-stu-id="c1227-109">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Constraint>|<span data-ttu-id="c1227-110">制約付きコンテナーまたは制約付きタスクを実行するかどうかを実行結果が決定するように指定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-110">Specifies that the execution outcome determines whether the constrained container or task runs.</span></span> <span data-ttu-id="c1227-111"><xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> プロパティを <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 列挙の目的の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-111">Set the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> to the desired value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Expression>|<span data-ttu-id="c1227-112">制約付きコンテナーまたは制約付きタスクを実行するかどうかを式の値で決定するように指定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-112">Specifies that the value of an expression determines whether the constrained container or task runs.</span></span> <span data-ttu-id="c1227-113"><xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-113">Set the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionAndConstraint>|<span data-ttu-id="c1227-114">実行する制約付きコンテナーまたは制約付きタスクに対して、制約結果が発生し、式が評価するように指定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-114">Specifies that the constraint outcome must occur and the expression must evaluate for the constrained container or task to run.</span></span> <span data-ttu-id="c1227-115"><xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> プロパティおよび <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> プロパティの両方を設定し、その <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-115">Set both the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> and the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> properties of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, and set its <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> property to `true`.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionOrConstraint>|<span data-ttu-id="c1227-116">実行する制約付きコンテナーまたは制約付きタスクに対して、制約結果が発生するか、または式が評価するように指定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-116">Specifies that either the constraint outcome must occur, or the expression must evaluate, for the constrained container or task to run.</span></span> <span data-ttu-id="c1227-117"><xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> プロパティおよび <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> プロパティの両方を設定し、その <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-117">Set both the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> and the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> properties of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, and set its <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> property to `false`.</span></span>|  
  
 <span data-ttu-id="c1227-118">次のコード例では、パッケージにタスクを 2 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="c1227-118">The following code sample demonstrates adding two tasks to a package.</span></span> <span data-ttu-id="c1227-119">次に、タスクの間に <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> を作成し、第 1 のタスクが終了するまで第 2 のタスクは実行しないように設定します。</span><span class="sxs-lookup"><span data-stu-id="c1227-119">A <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> is created between them that prevents the second task from running until the first task finishes.</span></span>  
  
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
  
      // Add a File System task.  
      Executable eFileTask1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost1 = eFileTask1 as TaskHost;  
  
      // Add a second File System task.  
      Executable eFileTask2 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost2 = eFileTask2 as TaskHost;  
  
      // Put a precedence constraint between the tasks.  
      // Set the constraint to specify that the second File System task cannot run  
      // until the first File System task finishes.  
      PrecedenceConstraint pcFileTasks =   
        p.PrecedenceConstraints.Add((Executable)thFileHost1, (Executable)thFileHost2);  
      pcFileTasks.Value = DTSExecResult.Completion;  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task.  
    Dim eFileTask1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost1 As TaskHost = CType(eFileTask1, TaskHost)  
  
    ' Add a second File System task.  
    Dim eFileTask2 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost2 As TaskHost = CType(eFileTask2, TaskHost)  
  
    ' Put a precedence constraint between the tasks.  
    ' Set the constraint to specify that the second File System task cannot run  
    ' until the first File System task finishes.  
    Dim pcFileTasks As PrecedenceConstraint = _  
      p.PrecedenceConstraints.Add(CType(thFileHost1, Executable), CType(thFileHost2, Executable))  
    pcFileTasks.Value = DTSExecResult.Completion  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="c1227-120">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="c1227-120">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c1227-121">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1227-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c1227-122">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="c1227-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c1227-123">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="c1227-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1227-124">参照</span><span class="sxs-lookup"><span data-stu-id="c1227-124">See Also</span></span>  
 [<span data-ttu-id="c1227-125">プログラムによるデータ フロー タスクの追加</span><span class="sxs-lookup"><span data-stu-id="c1227-125">Adding the Data Flow Task Programmatically</span></span>](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
  
  
