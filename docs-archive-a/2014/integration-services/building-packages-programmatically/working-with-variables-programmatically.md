---
title: プログラムでの変数の使用 | Microsoft Docs
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
- System namespace
- scope [Integration Services]
- variables [Integration Services], programmatically
- configuration files [Integration Services]
- Variables collection
- User namespace
- custom variables [Integration Services]
- variables [Integration Services], customizing
ms.assetid: c4b76a3d-94ca-4a8e-bb45-cb8bd0ea3ec1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2c903ee6adb8989eaeb93efbe943eca93c73eae4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738682"
---
# <a name="working-with-variables-programmatically"></a><span data-ttu-id="90cbc-102">プログラムでの変数の使用</span><span class="sxs-lookup"><span data-stu-id="90cbc-102">Working with Variables Programmatically</span></span>
  <span data-ttu-id="90cbc-103">変数を使用すると、値を動的に設定し、パッケージ、コンテナー、タスク、およびイベント ハンドラーの処理を制御できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-103">Variables are a way to dynamically set values and control processes in packages, containers, tasks, and event handlers.</span></span> <span data-ttu-id="90cbc-104">また、優先順位制約で変数を使用して、別のタスクへのデータ フローの方向を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-104">Variables can also be used by precedence constraints to control the direction of the flow of data to different tasks.</span></span> <span data-ttu-id="90cbc-105">変数には、以下のようにさまざまな使用方法があります。</span><span class="sxs-lookup"><span data-stu-id="90cbc-105">Variables have a variety of uses:</span></span>

-   <span data-ttu-id="90cbc-106">実行時にパッケージのプロパティを更新する。</span><span class="sxs-lookup"><span data-stu-id="90cbc-106">Update properties of a package at run time.</span></span>

-   <span data-ttu-id="90cbc-107">実行時に Transact-SQL ステートメントのパラメーター値を設定する。</span><span class="sxs-lookup"><span data-stu-id="90cbc-107">Populate parameter values for Transact-SQL statements at run time.</span></span>

-   <span data-ttu-id="90cbc-108">Foreach ループのフローを制御する。</span><span class="sxs-lookup"><span data-stu-id="90cbc-108">Control the flow of a Foreach loop.</span></span> <span data-ttu-id="90cbc-109">詳細については、「[制御フローに列挙を追加する](../control-flow/control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cbc-109">For more information, see [Add Enumeration to a Control Flow](../control-flow/control-flow.md).</span></span>

-   <span data-ttu-id="90cbc-110">式で使用することにより、優先順位制約を制御する。</span><span class="sxs-lookup"><span data-stu-id="90cbc-110">Control a precedence constraint by its use in an expression.</span></span> <span data-ttu-id="90cbc-111">優先順位制約では、制約定義に変数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-111">A precedence constraint can include variables in the constraint definition.</span></span> <span data-ttu-id="90cbc-112">詳細については、「 [優先順位制約に式を追加する](../control-flow/precedence-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cbc-112">For more information, see [Add Expressions to Precedence Constraints](../control-flow/precedence-constraints.md).</span></span>

-   <span data-ttu-id="90cbc-113">For ループ コンテナーの条件付きの繰り返しを制御する。</span><span class="sxs-lookup"><span data-stu-id="90cbc-113">Control the conditional repeat of a For Loop container.</span></span> <span data-ttu-id="90cbc-114">詳細については、「[制御フローに繰り返しを追加する](../add-iteration-to-a-control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cbc-114">For more information, see [Add Iteration to a Control Flow](../add-iteration-to-a-control-flow.md).</span></span>

-   <span data-ttu-id="90cbc-115">変数値が含まれる式を構築する。</span><span class="sxs-lookup"><span data-stu-id="90cbc-115">Build expressions that include variable values.</span></span>

-   <span data-ttu-id="90cbc-116">パッケージ、**Foreach ループ** コンテナー、**For ループ** コンテナー、**シーケンス** コンテナー、タスク ホスト、およびイベント ハンドラーなど、すべての種類のコンテナー用にカスタム変数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-116">You can create custom variables for all container types: packages, **Foreach Loop** containers, **For Loop** containers, **Sequence** containers, TaskHosts, and event handlers.</span></span> <span data-ttu-id="90cbc-117">詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../use-variables-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="90cbc-117">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>

## <a name="scope"></a><span data-ttu-id="90cbc-118">スコープ</span><span class="sxs-lookup"><span data-stu-id="90cbc-118">Scope</span></span>
 <span data-ttu-id="90cbc-119">各コンテナーには、独自の <xref:Microsoft.SqlServer.Dts.Runtime.Variables> コレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="90cbc-119">Each container has its own <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection.</span></span> <span data-ttu-id="90cbc-120">新しい変数が作成されると、その親コンテナーのスコープ内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-120">When a new variable is created, it is within the scope of its parent container.</span></span> <span data-ttu-id="90cbc-121">パッケージ コンテナーは、コンテナー階層の最上層にあるため、パッケージ スコープを持つ変数はグローバル変数と同じように機能し、パッケージ内のすべてのコンテナーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-121">Because the package container is at the top of the container hierarchy, variables with package scope function like global variables, and are visible to all containers within the package.</span></span> <span data-ttu-id="90cbc-122">また、子コンテナーは、<xref:Microsoft.SqlServer.Dts.Runtime.Variables> コレクションを介して、親コンテナーの変数コレクションにアクセスできます。アクセスするには、コレクション内の変数名または変数のインデックスのどちらかを使用します。</span><span class="sxs-lookup"><span data-stu-id="90cbc-122">The collection of variables for the container can also be accessed by the children of the container through the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection, by using either the variable name or the variable's index in the collection.</span></span>

 <span data-ttu-id="90cbc-123">変数は上から順にスコープされるため、パッケージ レベルで宣言された変数は、パッケージ内のすべてのコンテナーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-123">Because the visibility of a variable is scoped from the top down, variables declared at the package level are visible to all the containers in the package.</span></span> <span data-ttu-id="90cbc-124">したがって、コンテナーの <xref:Microsoft.SqlServer.Dts.Runtime.Variables> コレクションには、コンテナー独自の変数だけでなく、その親コンテナーに属するすべての変数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-124">Therefore, the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection on a container includes all the variables that belong to its parent in addition to its own variables</span></span>

 <span data-ttu-id="90cbc-125">これに対し、タスクに含まれる変数のスコープおよび可視性は制限されているため、そのタスクのみで使用できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-125">Conversely, the variables that are contained in a task are limited in scope and visibility, and are only visible to the task.</span></span>

 <span data-ttu-id="90cbc-126">パッケージが他のパッケージを実行する場合、呼び出し元のスコープで定義された変数は、呼び出し先のパッケージで使用できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-126">If a package runs other packages, the variables defined in the scope of the calling package are available to the called package.</span></span> <span data-ttu-id="90cbc-127">ただし、呼び出し先のパッケージに同じ名前の変数が存在する場合だけは例外です。</span><span class="sxs-lookup"><span data-stu-id="90cbc-127">The only exception occurs when a same-named variable exists in the called package.</span></span> <span data-ttu-id="90cbc-128">この衝突が発生すると、呼び出し先の変数値が呼び出し元のパッケージの値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="90cbc-128">When this collision occurs, the variable value in the called package overrides the value from the calling package.</span></span> <span data-ttu-id="90cbc-129">呼び出し先のパッケージのスコープで定義された変数は、呼び出し元のパッケージでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="90cbc-129">Variables defined in the scope of the called package are never available back to the calling package.</span></span>

 <span data-ttu-id="90cbc-130">次のコード例では、プログラムによって、変数 `myCustomVar` をパッケージのスコープで作成し、パッケージで使用できるすべての変数を反復処理し、変数の名前、データ型、および値を出力します。</span><span class="sxs-lookup"><span data-stu-id="90cbc-130">The following code example programmatically creates a variable, `myCustomVar`, at the package scope, and then iterates through all the variables visible to the package, printing their name, data type, and value.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Application app = new Application();
      // Load a sample package that contains a variable that sets the file name.
      Package pkg = app.LoadPackage(
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +
        @"\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx",
        null);
      Variables pkgVars = pkg.Variables;
      Variable myVar = pkg.Variables.Add("myCustomVar", false, "User", "3");
      foreach (Variable pkgVar in pkgVars)
      {
        Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name,
          pkgVar.DataType, pkgVar.Value.ToString());
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

    Dim app As Application = New Application()
    ' Load a sample package that contains a variable that sets the file name.
    Dim pkg As Package = app.LoadPackage( _
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _
      "\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx", _
      Nothing)
    Dim pkgVars As Variables = pkg.Variables
    Dim myVar As Variable = pkg.Variables.Add("myCustomVar", False, "User", "3")
    Dim pkgVar As Variable
    For Each pkgVar In pkgVars
      Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name, _
        pkgVar.DataType, pkgVar.Value.ToString())
    Next
    Console.Read()

  End Sub

End Module
```

 <span data-ttu-id="90cbc-131">**サンプル出力:**</span><span class="sxs-lookup"><span data-stu-id="90cbc-131">**Sample Output:**</span></span>

 `Variable: CancelEvent, Int32, 0`

 `Variable: CreationDate, DateTime, 4/18/2003 11:57:00 AM`

 `Variable: CreatorComputerName, String,`

 `Variable: CreatorName, String,`

 `Variable: ExecutionInstanceGUID, String, {237AB5A4-7E59-4FC9-8D61-E8F20363DF25}`

 `Variable: FileName, String, Junk`

 `Variable: InteractiveMode, Boolean, False`

 `Variable: LocaleID, Int32, 1033`

 `Variable: MachineName, String, MYCOMPUTERNAME`

 `Variable: myCustomVar, String, 3`

 `Variable: OfflineMode, Boolean, False`

 `Variable: PackageID, String, {F0D2E396-A6A5-42AE-9467-04CE946A810C}`

 `Variable: PackageName, String, DTSPackage1`

 `Variable: StartTime, DateTime, 1/28/2005 7:55:39 AM`

 `Variable: UserName, String, <domain>\<userid>`

 `Variable: VersionBuild, Int32, 198`

 `Variable: VersionComments, String,`

 `Variable: VersionGUID, String, {90E105B4-B4AF-4263-9CBD-C2050C2D6148}`

 `Variable: VersionMajor, Int32, 1`

 `Variable: VersionMinor, Int32, 0`

 <span data-ttu-id="90cbc-132">**System** 名前空間で有効なすべての変数は、パッケージで使用できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-132">Notice that all the variables scoped in the **System** namespace are available to the package.</span></span> <span data-ttu-id="90cbc-133">詳細については、「 [システム変数](../system-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cbc-133">For more information, see [System Variables](../system-variables.md).</span></span>

## <a name="namespaces"></a><span data-ttu-id="90cbc-134">名前空間</span><span class="sxs-lookup"><span data-stu-id="90cbc-134">Namespaces</span></span>
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="90cbc-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) では、**User** および **System** 名前空間という 2 つの既定の名前空間が提供され、変数はこれらの名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="90cbc-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) provides two default namespaces where variables reside; **User** and **System** namespaces.</span></span> <span data-ttu-id="90cbc-136">既定では、開発者が作成したカスタム変数は、**User** 名前空間に追加されます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-136">By default, any custom variable created by the developer is added to the **User** namespace.</span></span> <span data-ttu-id="90cbc-137">システム変数は、**System** 名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="90cbc-137">System variables reside in the **System** namespace.</span></span> <span data-ttu-id="90cbc-138">**User** 名前空間以外の名前空間を追加作成してカスタム変数を保持したり、**User** 名前空間の名前を変更することはできますが、**System** 名前空間の変数を追加したり、変更することはできません。また、システム変数を別の名前空間に割り当てることもできません。</span><span class="sxs-lookup"><span data-stu-id="90cbc-138">You can create additional namespaces other than the **User** namespace to hold custom variables, and you can change the name of the **User** namespace, but you cannot add or modify variables in the **System** namespace, or assign system variables to a different namespace.</span></span>

 <span data-ttu-id="90cbc-139">使用できるシステム変数は、コンテナーの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="90cbc-139">The system variables that are available differ depending on the container type.</span></span> <span data-ttu-id="90cbc-140">パッケージ、コンテナー、タスク、およびイベント ハンドラーで使用できるシステム変数の一覧については、「[システム変数](../system-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cbc-140">For a list of the system variables available to packages, containers, tasks, and event handlers, see [System Variables](../system-variables.md).</span></span>

## <a name="value"></a><span data-ttu-id="90cbc-141">値</span><span class="sxs-lookup"><span data-stu-id="90cbc-141">Value</span></span>
 <span data-ttu-id="90cbc-142">カスタム変数の値には、リテラルまたは式を設定できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-142">The value of a custom variable can be a literal or an expression:</span></span>

-   <span data-ttu-id="90cbc-143">変数にリテラル値を格納する場合は、<xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> プロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="90cbc-143">If you want the variable to contain a literal value, set the value of its <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property.</span></span>

-   <span data-ttu-id="90cbc-144">変数に式を含めて、式の結果を変数の値として使用する場合、変数の <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> プロパティを `true` に設定し、<xref:Microsoft.SqlServer.Dts.Runtime.Variable.Expression%2A> プロパティで式を指定します。</span><span class="sxs-lookup"><span data-stu-id="90cbc-144">If you want the variable to contain an expression, so that you can use the results of the expression as its value, set the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> property of the variable to `true`, and provide an expression in the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Expression%2A> property.</span></span> <span data-ttu-id="90cbc-145">実行時に式が評価され、式の戻り値が変数の値として使用されます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-145">At run time, the expression is evaluated, and the result of the expression is used as the value of the variable.</span></span> <span data-ttu-id="90cbc-146">たとえば、変数の式のプロパティが `"100 * 2""100 * 2"` の場合、変数は値 200 に評価されます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-146">For example, if the expression property of a variable is `"100 * 2""100 * 2"`, the variable evaluates to a value of 200.</span></span>

 <span data-ttu-id="90cbc-147">変数の <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> に明示的に値を設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="90cbc-147">For a variable, you cannot explicitly set the value of its <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A>.</span></span> <span data-ttu-id="90cbc-148"><xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> 値は、変数に割り当てられた初期値から推論され、その後は変更できません。</span><span class="sxs-lookup"><span data-stu-id="90cbc-148">The <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> value is inferred from the initial value assigned to the variable, and cannot be changed afterward.</span></span> <span data-ttu-id="90cbc-149">変数のデータ型の詳細については、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cbc-149">For more information about variable data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

 <span data-ttu-id="90cbc-150">次のコード例では、新しい変数を作成し、<xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> を `true` に設定して、式 `"100 * 2"` を変数の式のプロパティに割り当てます。その後、変数の値を出力します。</span><span class="sxs-lookup"><span data-stu-id="90cbc-150">The following code example creates a new variable, sets <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> to `true`, assigns the expression `"100 * 2"` to the expression property of the variable, and then outputs the value of the variable.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Package pkg = new Package();
      Variable v100 = pkg.Variables.Add("myVar", false, "", 1);
      v100.EvaluateAsExpression = true;
      v100.Expression = "100 * 2";
      Console.WriteLine("Expression for myVar: {0}", 
        v100.Properties["Expression"].GetValue(v100));
      Console.WriteLine("Value of myVar: {0}", v100.Value.ToString());
      Console.Read();
    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim pkg As Package = New Package
    Dim v100 As Variable = pkg.Variables.Add("myVar", False, "", 1)
    v100.EvaluateAsExpression = True
    v100.Expression = "100 * 2"
    Console.WriteLine("Expression for myVar: {0}", _
      v100.Properties("Expression").GetValue(v100))
    Console.WriteLine("Value of myVar: {0}", v100.Value.ToString)
    Console.Read()

  End Sub

End Module
```

 <span data-ttu-id="90cbc-151">**サンプル出力:**</span><span class="sxs-lookup"><span data-stu-id="90cbc-151">**Sample Output:**</span></span>

 `Expression for myVar: 100 * 2`

 `Value of myVar: 200`

 <span data-ttu-id="90cbc-152">式は、[!INCLUDE[ssIS](../../includes/ssis-md.md)] 式の構文を使用する、有効な式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="90cbc-152">The expression must be a valid expression that uses the [!INCLUDE[ssIS](../../includes/ssis-md.md)] expression syntax.</span></span> <span data-ttu-id="90cbc-153">式の構文が提供する演算子や関数のほか、リテラルも変数式で使用できますが、他の変数または列を式で参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="90cbc-153">Literals are permitted in variable expressions, in addition to the operators and functions that the expression syntax provides, but expressions cannot reference other variables or columns.</span></span> <span data-ttu-id="90cbc-154">詳細については、「 [Integration Services (SSIS) 式](../expressions/integration-services-ssis-expressions.md)に評価されるまでそのワークフローを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="90cbc-154">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="90cbc-155">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="90cbc-155">Configuration Files</span></span>
 <span data-ttu-id="90cbc-156">構成ファイルにカスタム変数を含めると、実行時に変数を更新できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-156">If a configuration file includes a custom variable, the variable can be updated at run time.</span></span> <span data-ttu-id="90cbc-157">つまり、パッケージを実行すると、パッケージにあらかじめ含まれていた変数の値は、構成ファイルの新しい値で置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-157">What this means is that when the package runs, the value of the variable originally in the package is replaced with a new value from the configuration file.</span></span> <span data-ttu-id="90cbc-158">この置き換え方法を使用すると、異なる変数値が必要な複数のサーバーにパッケージを配置するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="90cbc-158">This replacement technique is useful when a package is deployed to multiple servers that require different variable values.</span></span> <span data-ttu-id="90cbc-159">たとえば、変数を使用して、**Foreach ループ** コンテナーがそのワークフローを繰り返す回数を指定したり、エラーが発生したときにイベント ハンドラーが送信する電子メールの受信者を一覧表示したり、パッケージが失敗するまでのエラーの発生回数を変更できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-159">For example, a variable can specify the number of times a **Foreach Loop** container repeats its workflow, or list the recipients that an event handler sends e-mail to when an error is raised, or change the number of errors that can occur before the package fails.</span></span> <span data-ttu-id="90cbc-160">これらの変数は、各環境の構成ファイルで動的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-160">These variables are dynamically provided in configuration files for each environment.</span></span> <span data-ttu-id="90cbc-161">したがって、構成ファイルでは読み取り/書き込み用の変数のみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="90cbc-161">Therefore, only variables that are read/write are allowed in configuration files.</span></span> <span data-ttu-id="90cbc-162">詳細については、「 [パッケージ構成を作成する](../create-package-configurations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cbc-162">For more information, see [Create Package Configurations](../create-package-configurations.md).</span></span>

<span data-ttu-id="90cbc-163">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="90cbc-163">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="90cbc-164">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cbc-164">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="90cbc-165">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="90cbc-165">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="90cbc-166">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="90cbc-166">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="90cbc-167">参照</span><span class="sxs-lookup"><span data-stu-id="90cbc-167">See Also</span></span>
 <span data-ttu-id="90cbc-168">[SSIS&#41; 変数の Integration Services &#40;](../integration-services-ssis-variables.md) [パッケージでの変数の使用](../use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="90cbc-168">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) [Use Variables in Packages](../use-variables-in-packages.md)</span></span>


