---
title: スクリプト タスクのコーディングおよびデバッグ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], debugging
- SSIS Script task, development environment
- SSIS Script task, debugging
- Script task [Integration Services], development environment
- Script task [Integration Services], coding
- debugging [Integration Services], scripts
- VSTA
- SSIS Script task, coding
ms.assetid: 687c262f-fcab-42e8-92ae-e956f3d92d69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f4383469368ac1fe3c70ff82f8c8bb2cf755838
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712174"
---
# <a name="coding-and-debugging-the-script-task"></a><span data-ttu-id="17147-102">スクリプト タスクのコーディングおよびデバッグ</span><span class="sxs-lookup"><span data-stu-id="17147-102">Coding and Debugging the Script Task</span></span>
  <span data-ttu-id="17147-103">**[スクリプト タスク エディター]** でスクリプト タスクを構成したら、スクリプト タスク開発環境でカスタム コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="17147-103">After configuring the Script task in the **Script Task Editor**, you write your custom code in the Script task development environment.</span></span>

## <a name="script-task-development-environment"></a><span data-ttu-id="17147-104">スクリプト タスク開発環境</span><span class="sxs-lookup"><span data-stu-id="17147-104">Script Task Development Environment</span></span>
 <span data-ttu-id="17147-105">スクリプト タスクでは、スクリプト自体の開発環境として、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="17147-105">The Script task uses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the development environment for the script itself.</span></span>

 <span data-ttu-id="17147-106">スクリプト コードは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# で記述されます。</span><span class="sxs-lookup"><span data-stu-id="17147-106">Script code is written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> <span data-ttu-id="17147-107">スクリプト言語を指定するには、**スクリプト タスク エディター**で **[ScriptLanguage]** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="17147-107">You specify the script language by setting the **ScriptLanguage** property in the **Script Task Editor**.</span></span> <span data-ttu-id="17147-108">その他のプログラミング言語を使用する場合は、選択した言語でカスタム アセンブリを作成し、スクリプト タスク内のコードからその機能を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="17147-108">If you prefer to use another programming language, you can develop a custom assembly in your language of choice and call its functionality from the code in the Script task.</span></span>

 <span data-ttu-id="17147-109">スクリプト タスクで作成したスクリプトは、パッケージ定義に格納されます。</span><span class="sxs-lookup"><span data-stu-id="17147-109">The script that you create in the Script task is stored in the package definition.</span></span> <span data-ttu-id="17147-110">スクリプト ファイルが別途存在するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="17147-110">There is no separate script file.</span></span> <span data-ttu-id="17147-111">したがって、スクリプト タスクを使用してもパッケージの配置には影響しません。</span><span class="sxs-lookup"><span data-stu-id="17147-111">Therefore, the use of the Script task does not affect package deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="17147-112">パッケージをデザインしてスクリプトをデバッグする際、スクリプト コードは一時的にプロジェクト ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="17147-112">When you design the package and debug the script, the script code is temporarily written to a project file.</span></span> <span data-ttu-id="17147-113">機密情報をファイルに保存することはセキュリティ上危険であるため、パスワードなどの重要な情報はスクリプト コードに書き込まないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="17147-113">Because storing sensitive information in a file is a potential security risk, we recommend that you do not include sensitive information such as passwords in the script code.</span></span>

 <span data-ttu-id="17147-114">既定では、`Option Strict` が IDE で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="17147-114">By default, `Option Strict` is disabled in the IDE.</span></span>

## <a name="script-task-project-structure"></a><span data-ttu-id="17147-115">スクリプト タスク プロジェクトの構造</span><span class="sxs-lookup"><span data-stu-id="17147-115">Script Task Project Structure</span></span>
 <span data-ttu-id="17147-116">スクリプト タスクに格納されているスクリプトを作成または変更する場合、VSTA は空の新しいプロジェクトを開くか、または既存のプロジェクトを再度開きます。</span><span class="sxs-lookup"><span data-stu-id="17147-116">When you create or modify the script that is contained in a Script task, VSTA opens an empty new project or reopens the existing project.</span></span> <span data-ttu-id="17147-117">この VSTA プロジェクトを作成しても、パッケージの配置に影響はありません。このプロジェクトはパッケージ ファイル内部に保存され、スクリプト タスクは追加ファイルを作成しないためです。</span><span class="sxs-lookup"><span data-stu-id="17147-117">The creation of this VSTA project does not affect the deployment of the package, because the project is saved inside the package file; the Script task does not create additional files.</span></span>

### <a name="project-items-and-classes-in-the-script-task-project"></a><span data-ttu-id="17147-118">スクリプト タスク プロジェクトのプロジェクト アイテムおよびクラス</span><span class="sxs-lookup"><span data-stu-id="17147-118">Project Items and Classes in the Script Task Project</span></span>
 <span data-ttu-id="17147-119">VSTA の [プロジェクト エクスプローラー] ウィンドウに表示されるスクリプト タスク プロジェクトには、既定で `ScriptMain` という単一のアイテムが格納されます。</span><span class="sxs-lookup"><span data-stu-id="17147-119">By default, the Script task project displayed in the VSTA Project Explorer window contains a single item, `ScriptMain`.</span></span> <span data-ttu-id="17147-120">`ScriptMain` アイテムには、同じく `ScriptMain` という名前の単一のクラスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="17147-120">The `ScriptMain` item, in turn, contains a single class, also named `ScriptMain`.</span></span> <span data-ttu-id="17147-121">このクラスのコード要素は、スクリプト タスクに対して選択したプログラミング言語に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="17147-121">The code elements in the class vary depending on the programming language that you selected for the Script task:</span></span>

-   <span data-ttu-id="17147-122">スクリプト タスクが [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] プログラミング言語用に構成されている場合は、`ScriptMain` クラスにパブリック サブルーチン `Main` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="17147-122">When the Script task is configured for the [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] programming language, the `ScriptMain` class has a public subroutine, `Main`.</span></span> <span data-ttu-id="17147-123">`ScriptMain.Main` サブルーチンは、ユーザーのスクリプト タスクを実行するときにランタイムが呼び出すメソッドです。</span><span class="sxs-lookup"><span data-stu-id="17147-123">The `ScriptMain.Main` subroutine is the method that the runtime calls when you run your Script task.</span></span>

     <span data-ttu-id="17147-124">既定では、新しいスクリプトの `Main` サブルーチン内にあるコードは、行 `Dts.TaskResult = ScriptResults.Success` のみです。</span><span class="sxs-lookup"><span data-stu-id="17147-124">By default, the only code in the `Main` subroutine of a new script is the line `Dts.TaskResult = ScriptResults.Success`.</span></span> <span data-ttu-id="17147-125">この行は、タスクの処理が正常に実行されたことをランタイムに通知します。</span><span class="sxs-lookup"><span data-stu-id="17147-125">This line informs the runtime that the task was successful in its operation.</span></span> <span data-ttu-id="17147-126">`Dts.TaskResult`プロパティは、「[スクリプトタスクから結果を返す](../../extending-packages-scripting/task/returning-results-from-the-script-task.md)」で説明されています。</span><span class="sxs-lookup"><span data-stu-id="17147-126">The `Dts.TaskResult` property is discussed in [Returning Results from the Script Task](../../extending-packages-scripting/task/returning-results-from-the-script-task.md).</span></span>

-   <span data-ttu-id="17147-127">スクリプト タスクが Visual C# プログラミング言語用に構成されている場合は、`ScriptMain` クラスにパブリック メソッド `Main` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="17147-127">When the Script task is configured for the Visual C# programming language, the `ScriptMain` class has a public method, `Main`.</span></span> <span data-ttu-id="17147-128">このメソッドは、スクリプト タスク実行時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="17147-128">The method is called when the Script task runs.</span></span>

     <span data-ttu-id="17147-129">既定では、`Main` メソッドに `Dts.TaskResult = (int)ScriptResults.Success` という行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="17147-129">By default, the `Main` method includes the line `Dts.TaskResult = (int)ScriptResults.Success`.</span></span> <span data-ttu-id="17147-130">この行は、タスクの処理が正常に実行されたことをランタイムに通知します。</span><span class="sxs-lookup"><span data-stu-id="17147-130">This line informs the runtime that the task was successful in its operation.</span></span>

 <span data-ttu-id="17147-131">`ScriptMain` アイテムには、`ScriptMain` クラス以外のクラスを格納できます。</span><span class="sxs-lookup"><span data-stu-id="17147-131">The `ScriptMain` item can contain classes other than the `ScriptMain` class.</span></span> <span data-ttu-id="17147-132">クラスは、そのクラスが含まれているスクリプト タスクでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="17147-132">Classes are available only to the Script task in which they reside.</span></span>

 <span data-ttu-id="17147-133">既定では、`ScriptMain` プロジェクト アイテムには、次のコードが自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="17147-133">By default, the `ScriptMain` project item contains the following autogenerated code.</span></span> <span data-ttu-id="17147-134">コード テンプレートでも、スクリプト タスクの概要、および、変数、イベント、接続など、SSIS オブジェクトを取得および操作する方法に関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="17147-134">The code template also provides an overview of the Script task, and additional information on how to retrieve and manipulate SSIS objects, such as variables, events, and connections.</span></span>

```vb
' Microsoft SQL Server Integration Services Script Task
' Write scripts using Microsoft Visual Basic 2008.
' The ScriptMain is the entry point class of the script.

Imports System
Imports System.Data
Imports System.Math
Imports Microsoft.SqlServer.Dts.Runtime.VSTAProxy

<System.AddIn.AddIn("ScriptMain", Version:="1.0", Publisher:="", Description:="")> _
Partial Class ScriptMain

Private Sub ScriptMain_Startup(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Startup

End Sub

Private Sub ScriptMain_Shutdown(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Shutdown
Try
' Unlock variables from the read-only and read-write variable collection properties
If (Dts.Variables.Count <> 0) Then
Dts.Variables.Unlock()
End If
Catch ex As Exception
        End Try
End Sub

Enum ScriptResults
Success = DTSExecResult.Success
Failure = DTSExecResult.Failure
End Enum

' The execution engine calls this method when the task executes.
' To access the object model, use the Dts property. Connections, variables, events,
' and logging features are available as members of the Dts property as shown in the following examples.
'
' To reference a variable, call Dts.Variables("MyCaseSensitiveVariableName").Value
' To post a log entry, call Dts.Log("This is my log text", 999, Nothing)
' To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, True)
'
' To use the connections collection use something like the following:
' ConnectionManager cm = Dts.Connections.Add("OLEDB")
' cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;"
'
' Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.
' 
' To open Help, press F1.

Public Sub Main()
'
' Add your code here
'
Dts.TaskResult = ScriptResults.Success
End Sub

End Class
```

```csharp
/*
   Microsoft SQL Server Integration Services Script Task
   Write scripts using Microsoft Visual C# 2008.
   The ScriptMain is the entry point class of the script.
*/

using System;
using System.Data;
using Microsoft.SqlServer.Dts.Runtime.VSTAProxy;
using System.Windows.Forms;

namespace ST_1bcfdbad36d94f8ba9f23a10375abe53.csproj
{
    [System.AddIn.AddIn("ScriptMain", Version = "1.0", Publisher = "", Description = "")]
    public partial class ScriptMain
    {
        private void ScriptMain_Startup(object sender, EventArgs e)
        {

        }

        private void ScriptMain_Shutdown(object sender, EventArgs e)
        {
            try
            {
                // Unlock variables from the read-only and read-write variable collection properties
                if (Dts.Variables.Count != 0)
                {
                    Dts.Variables.Unlock();
                }
            }
            catch
            {
            }
        }

        #region VSTA generated code
        private void InternalStartup()
        {
            this.Startup += new System.EventHandler(ScriptMain_Startup);
            this.Shutdown += new System.EventHandler(ScriptMain_Shutdown);
        }
        enum ScriptResults
        {
            Success = DTSExecResult.Success,
            Failure = DTSExecResult.Failure
        };

        #endregion

        /*
The execution engine calls this method when the task executes.
To access the object model, use the Dts property. Connections, variables, events,
and logging features are available as members of the Dts property as shown in the following examples.

To reference a variable, call Dts.Variables["MyCaseSensitiveVariableName"].Value;
To post a log entry, call Dts.Log("This is my log text", 999, null);
To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, true);

To use the connections collection use something like the following:
ConnectionManager cm = Dts.Connections.Add("OLEDB");
cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;";

Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.

To open Help, press F1.
*/

        public void Main()
        {
            // TODO: Add your code here
            Dts.TaskResult = (int)ScriptResults.Success;
        }
    }
```

### <a name="additional-project-items-in-the-script-task-project"></a><span data-ttu-id="17147-135">スクリプト タスク プロジェクトのその他のプロジェクト アイテム</span><span class="sxs-lookup"><span data-stu-id="17147-135">Additional Project Items in the Script Task Project</span></span>
 <span data-ttu-id="17147-136">スクリプト タスク プロジェクトには、既定の `ScriptMain` アイテム以外のアイテムを格納できます。</span><span class="sxs-lookup"><span data-stu-id="17147-136">The Script task project can include items other than the default `ScriptMain` item.</span></span> <span data-ttu-id="17147-137">プロジェクトには、クラス、モジュール、およびコード ファイルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="17147-137">You can add classes, modules, and code files to the project.</span></span> <span data-ttu-id="17147-138">また、フォルダーを使用してアイテムのグループを整理できます。</span><span class="sxs-lookup"><span data-stu-id="17147-138">You can also use folders to organize groups of items.</span></span> <span data-ttu-id="17147-139">追加したすべてのアイテムは、パッケージ内部に保存されます。</span><span class="sxs-lookup"><span data-stu-id="17147-139">All the items that you add are persisted inside the package.</span></span>

### <a name="references-in-the-script-task-project"></a><span data-ttu-id="17147-140">スクリプト タスク プロジェクトの参照</span><span class="sxs-lookup"><span data-stu-id="17147-140">References in the Script Task Project</span></span>
 <span data-ttu-id="17147-141">参照をマネージド アセンブリに追加するには、 **[プロジェクト エクスプローラー]** でスクリプト タスク プロジェクトを右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="17147-141">You can add references to managed assemblies by right-clicking the Script task project in **Project Explorer**, and then clicking **Add Reference**.</span></span> <span data-ttu-id="17147-142">詳しくは、「[スクリプティング ソリューションでの他のアセンブリの参照](../referencing-other-assemblies-in-scripting-solutions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="17147-142">For more information, see [Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="17147-143">プロジェクト参照は、VSTA IDE の **[クラス ビュー]** または**プロジェクト エクスプローラー**で表示できます。</span><span class="sxs-lookup"><span data-stu-id="17147-143">You can view project references in the VSTA IDE in **Class View** or in **Project Explorer**.</span></span> <span data-ttu-id="17147-144">どちらのウィンドウも **[表示]** メニューから開きます。</span><span class="sxs-lookup"><span data-stu-id="17147-144">You open either of these windows from the **View** menu.</span></span> <span data-ttu-id="17147-145">新しい参照は、 **[プロジェクト]** メニュー、**プロジェクト エクスプローラー**、または **[クラス ビュー]** から追加できます。</span><span class="sxs-lookup"><span data-stu-id="17147-145">You can add a new reference from the **Project** menu, from **Project Explorer**, or from **Class View**.</span></span>

## <a name="interacting-with-the-package-in-the-script-task"></a><span data-ttu-id="17147-146">スクリプト タスク内でのパッケージとの対話</span><span class="sxs-lookup"><span data-stu-id="17147-146">Interacting with the Package in the Script Task</span></span>
 <span data-ttu-id="17147-147">スクリプト タスクは、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> クラスのインスタンスであるグローバル オブジェクト `Dts`、およびそのメンバーを使用して、内部のパッケージや [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイムとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="17147-147">The Script task uses the global `Dts` object, which is an instance of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class, and its members to interact with the containing package and with the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.</span></span>

 <span data-ttu-id="17147-148">次の表は、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> クラスのプリンシパルのパブリック メンバーの一覧です。このクラスは、グローバル オブジェクト `Dts` を介してスクリプト タスクのコードに公開されます。</span><span class="sxs-lookup"><span data-stu-id="17147-148">The following table lists the principal public members of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class, which is exposed to Script task code through the global `Dts` object.</span></span> <span data-ttu-id="17147-149">このセクションのトピックでは、これらのメンバーを使用する方法についてさらに詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="17147-149">The topics in this section discuss the use of these members in more detail.</span></span>

|<span data-ttu-id="17147-150">メンバー</span><span class="sxs-lookup"><span data-stu-id="17147-150">Member</span></span>|<span data-ttu-id="17147-151">目的</span><span class="sxs-lookup"><span data-stu-id="17147-151">Purpose</span></span>|
|------------|-------------|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>|<span data-ttu-id="17147-152">パッケージで定義されている接続マネージャーへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="17147-152">Provides access to connection managers defined in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>|<span data-ttu-id="17147-153">スクリプト タスクでエラー、警告、および情報メッセージを発生させるためのイベント インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="17147-153">Provides an events interface to let the Script task raise errors, warnings, and informational messages.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>|<span data-ttu-id="17147-154">`TaskResult` のほか、ワークフローの分岐にも使用できる単一のオブジェクトをランタイムに返す簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="17147-154">Provides a simple way to return a single object to the runtime (in addition to the `TaskResult`) that can also be used for workflow branching.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>|<span data-ttu-id="17147-155">タスクの進行状況や結果などの情報を、有効なログ プロバイダーに記録します。</span><span class="sxs-lookup"><span data-stu-id="17147-155">Logs information such as task progress and results to enabled log providers.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>|<span data-ttu-id="17147-156">タスクの成功または失敗をレポートします。</span><span class="sxs-lookup"><span data-stu-id="17147-156">Reports the success or failure of the task.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Transaction%2A>|<span data-ttu-id="17147-157">タスクのコンテナーを実行しているトランザクションが存在する場合、それを提供します。</span><span class="sxs-lookup"><span data-stu-id="17147-157">Provides the transaction, if any, within which the task's container is running.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>|<span data-ttu-id="17147-158">スクリプトで使用するため、`ReadOnlyVariables` および `ReadWriteVariables` タスク プロパティの一覧に含まれる変数へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="17147-158">Provides access to the variables listed in the `ReadOnlyVariables` and `ReadWriteVariables` task properties for use within the script.</span></span>|

 <span data-ttu-id="17147-159"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> クラスには、使用しない可能性のあるパブリック メンバーも含まれています。</span><span class="sxs-lookup"><span data-stu-id="17147-159">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class also contains some public members that you will probably not use.</span></span>

|<span data-ttu-id="17147-160">メンバー</span><span class="sxs-lookup"><span data-stu-id="17147-160">Member</span></span>|<span data-ttu-id="17147-161">説明</span><span class="sxs-lookup"><span data-stu-id="17147-161">Description</span></span>|
|------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>|<span data-ttu-id="17147-162">変数にアクセスするには、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティの方が便利です。</span><span class="sxs-lookup"><span data-stu-id="17147-162">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property provides more convenient access to variables.</span></span> <span data-ttu-id="17147-163"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> も使用できますが、読み書きする変数をロックおよびロック解除するためのメソッドを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="17147-163">Although you can use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, you must explicitly call methods to lock and unlock variables for reading and writing.</span></span> <span data-ttu-id="17147-164"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティを使用すると、スクリプト タスクにより自動的にロック セマンティクスが処理されます。</span><span class="sxs-lookup"><span data-stu-id="17147-164">The Script task handles locking semantics for you when you use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property.</span></span>|

## <a name="debugging-the-script-task"></a><span data-ttu-id="17147-165">スクリプト タスクのデバッグ</span><span class="sxs-lookup"><span data-stu-id="17147-165">Debugging the Script Task</span></span>
 <span data-ttu-id="17147-166">スクリプト タスクのコードをデバッグするには、コードに少なくとも 1 つのブレークポイントを設定し、VSTA IDE を閉じて [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="17147-166">To debug the code in your Script task, set at least one breakpoint in the code, and then close the VSTA IDE to run the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="17147-167">パッケージが実行されてスクリプト タスクが開始されると、VSTA IDE が再度開き、読み取り専用モードでコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="17147-167">When package execution enters the Script task, the VSTA IDE reopens and displays your code in read-only mode.</span></span> <span data-ttu-id="17147-168">実行によりブレークポイントに到達したら、変数の値の検証や、残りのコードのステップ スルーができます。</span><span class="sxs-lookup"><span data-stu-id="17147-168">After execution reaches your breakpoint, you can examine variable values and step through the remaining code.</span></span>

> [!WARNING]
>  <span data-ttu-id="17147-169">64 ビット モードでパッケージを実行すると、スクリプト タスクをデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="17147-169">You can debug the Script task when you run the package in 64-bit mode.</span></span>

> [!NOTE]
>  <span data-ttu-id="17147-170">スクリプト タスクをデバッグするには、パッケージを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17147-170">You must execute the package to debug into your Script task.</span></span> <span data-ttu-id="17147-171">個別のタスクのみを実行する場合、スクリプト タスク コードのブレークポイントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="17147-171">If you execute only the individual task, breakpoints in the Script task code are ignored.</span></span>

> [!NOTE]
>  <span data-ttu-id="17147-172">パッケージ実行タスクから実行されている子パッケージの一部としてスクリプト タスクを実行する場合は、スクリプト タスクをデバッグできません。</span><span class="sxs-lookup"><span data-stu-id="17147-172">You cannot debug a Script task when you run the Script task as part of a child package that is run from an Execute Package task.</span></span> <span data-ttu-id="17147-173">このような場合は、子パッケージのスクリプト タスク内で設定したブレークポイントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="17147-173">Breakpoints that you set in the Script task in the child package are disregarded in these circumstances.</span></span> <span data-ttu-id="17147-174">子パッケージを単独で実行することにより、通常どおりパッケージをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="17147-174">You can debug the child package normally by running it separately.</span></span>

> [!NOTE]
>  <span data-ttu-id="17147-175">複数のスクリプト タスクが含まれるパッケージをデバッグする場合、デバッガーによってデバッグされるスクリプト タスクは 1 つです。</span><span class="sxs-lookup"><span data-stu-id="17147-175">When you debug a package that contains multiple Script tasks, the debugger debugs one Script task.</span></span> <span data-ttu-id="17147-176">Foreach ループまたは For ループ コンテナーの場合と同様に、デバッガーが完了した場合、システムは別のスクリプト タスクをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="17147-176">The system can debug another Script task if the debugger completes, as in the case of a Foreach Loop or For Loop container.</span></span>

## <a name="external-resources"></a><span data-ttu-id="17147-177">外部リソース</span><span class="sxs-lookup"><span data-stu-id="17147-177">External Resources</span></span>

-   <span data-ttu-id="17147-178">blogs.msdn.com のブログ「[VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661)」(SSIS 2008 インストールおよび R2 インストールでの VSTA のセットアップと構成に関する問題)。</span><span class="sxs-lookup"><span data-stu-id="17147-178">Blog entry, [VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661), on blogs.msdn.com.</span></span>

<span data-ttu-id="17147-179">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="17147-179">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="17147-180">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] が提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="17147-180">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="17147-181">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="17147-181">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="17147-182">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="17147-182">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="17147-183">参照</span><span class="sxs-lookup"><span data-stu-id="17147-183">See Also</span></span>
 <span data-ttu-id="17147-184">スクリプト[ソリューションでの他のアセンブリの参照](../referencing-other-assemblies-in-scripting-solutions.md)[スクリプトタスクエディターでのスクリプトタスクの構成](configuring-the-script-task-in-the-script-task-editor.md)</span><span class="sxs-lookup"><span data-stu-id="17147-184">[Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md) [Configuring the Script Task in the Script Task Editor](configuring-the-script-task-in-the-script-task-editor.md)</span></span>


