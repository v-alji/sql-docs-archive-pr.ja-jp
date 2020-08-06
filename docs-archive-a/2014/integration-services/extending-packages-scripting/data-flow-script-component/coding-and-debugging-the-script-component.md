---
title: スクリプト コンポーネントのコーディングおよびデバッグ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, development environment
- Script component [Integration Services], debugging
- Script component [Integration Services], coding
- SSIS Script component, debugging
- Script component [Integration Services], development environment
- debugging [Integration Services], scripts
- SSIS Script component, coding
- VSTA
ms.assetid: c3913c15-66aa-4b61-89b5-68488fa5f0a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9363ad447ca3d0031289eafb1d8f616320fca5b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642181"
---
# <a name="coding-and-debugging-the-script-component"></a><span data-ttu-id="ec1fa-102">スクリプト コンポーネントのコーディングおよびデバッグ</span><span class="sxs-lookup"><span data-stu-id="ec1fa-102">Coding and Debugging the Script Component</span></span>
  <span data-ttu-id="ec1fa-103">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでは、スクリプト コンポーネントにメタデータ デザイン モードとコード デザイン モードの 2 つのモードがあります。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-103">In [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the Script component has two modes: metadata design mode and code design mode.</span></span> <span data-ttu-id="ec1fa-104">**[スクリプト変換エディター]** を開くと、スクリプト コンポーネントはメタデータ デザイン モードになります。このモードでは、メタデータを構成し、コンポーネントのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-104">When you open the **Script Transformation Editor**, the component enters metadata design mode, in which you configure metadata and set component properties.</span></span> <span data-ttu-id="ec1fa-105">メタデータ デザイン モードで、スクリプト コンポーネントのプロパティを設定して、入力と出力を構成したら、コード デザイン モードに切り替えてカスタム スクリプトを記述できます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-105">After you have set the properties of the Script component and configured the input and outputs in metadata design mode, you can switch to code design mode to write your custom script.</span></span> <span data-ttu-id="ec1fa-106">メタデータ デザイン モードとコード デザイン モードについて詳しくは、「[スクリプト コンポーネント エディターでのスクリプト コンポーネントの構成](configuring-the-script-component-in-the-script-component-editor.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-106">For more information about metadata design mode and code design mode, see [Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md).</span></span>

## <a name="writing-the-script-in-code-design-mode"></a><span data-ttu-id="ec1fa-107">コード デザイン モードでのスクリプトの記述</span><span class="sxs-lookup"><span data-stu-id="ec1fa-107">Writing the Script in Code Design Mode</span></span>

### <a name="script-component-development-environment"></a><span data-ttu-id="ec1fa-108">スクリプト コンポーネント開発環境</span><span class="sxs-lookup"><span data-stu-id="ec1fa-108">Script Component Development Environment</span></span>
 <span data-ttu-id="ec1fa-109">スクリプトを記述するには、 **[スクリプト変換エディター]** の **[スクリプト]** ページで **[スクリプトの編集]** をクリックし、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE を開きます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-109">To write your script, click **Edit Script** on the **Script** page of the **Script Transformation Editor** to open the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE.</span></span> <span data-ttu-id="ec1fa-110">VSTA IDE には、色分け表示が可能な [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] エディター、IntelliSense、オブジェクト ブラウザーなど、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET 環境での標準機能がすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-110">The VSTA IDE includes all the standard features of the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET environment, such as the color-coded [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] editor, IntelliSense, and Object Browser.</span></span>

 <span data-ttu-id="ec1fa-111">スクリプト コードは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# で記述されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-111">Script code is written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> <span data-ttu-id="ec1fa-112">スクリプト言語を指定するには、 **[スクリプト変換エディター]** で **[ScriptLanguage]** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-112">You specify the script language by setting the **ScriptLanguage** property in the **Script Transformation Editor**.</span></span> <span data-ttu-id="ec1fa-113">その他のプログラミング言語を使用する場合は、選択した言語でカスタム アセンブリを作成し、スクリプト コンポーネント内のコードからその機能を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-113">If you prefer to use another programming language, you can develop a custom assembly in your language of choice and call its functionality from the code in the Script component.</span></span>

 <span data-ttu-id="ec1fa-114">スクリプト コンポーネントで作成したスクリプトは、パッケージ定義に格納されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-114">The script that you create in the Script component is stored in the package definition.</span></span> <span data-ttu-id="ec1fa-115">スクリプト ファイルが別途存在するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-115">There is no separate script file.</span></span> <span data-ttu-id="ec1fa-116">したがって、スクリプト コンポーネントを使用してもパッケージの配置には影響しません。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-116">Therefore, the use of the Script component does not affect package deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="ec1fa-117">パッケージをデザインする際、スクリプト コードは一時的にプロジェクト ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-117">While you design the package, the script code is temporarily written to a project file.</span></span> <span data-ttu-id="ec1fa-118">機密情報をファイルに保存することはセキュリティ上危険であるため、パスワードなどの重要な情報はスクリプト コードに書き込まないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-118">Because storing sensitive information in a file is a potential security risk, we recommended that you do not include sensitive information such as passwords in the script code.</span></span>

 <span data-ttu-id="ec1fa-119">既定では、`Option Strict` が IDE で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-119">By default, `Option Strict` is disabled in the IDE.</span></span>

### <a name="script-component-project-structure"></a><span data-ttu-id="ec1fa-120">スクリプト コンポーネント プロジェクトの構造</span><span class="sxs-lookup"><span data-stu-id="ec1fa-120">Script Component Project Structure</span></span>
 <span data-ttu-id="ec1fa-121">スクリプト コンポーネントの威力は、インフラストラクチャ コードを生成して、記述する必要のあるコード量を減らす機能にあります。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-121">The power of the Script component is that it can generate infrastructure code that reduces the amount of code that you must write.</span></span> <span data-ttu-id="ec1fa-122">この機能を実現するには、入力と出力、およびその列とプロパティが固定され、既知である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-122">This feature relies on the fact that inputs and outputs and their columns and properties are fixed and known in advance.</span></span> <span data-ttu-id="ec1fa-123">したがって、コンポーネントのメタデータに後で変更を加えた場合、記述したコードが無効になり、</span><span class="sxs-lookup"><span data-stu-id="ec1fa-123">Therefore, any subsequent changes that you make to the component's metadata may invalidate the code that you have written.</span></span> <span data-ttu-id="ec1fa-124">パッケージの実行中にコンパイル エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-124">This causes compilation errors during execution of the package.</span></span>

#### <a name="project-items-and-classes-in-the-script-component-project"></a><span data-ttu-id="ec1fa-125">スクリプト コンポーネント プロジェクトのプロジェクト アイテムおよびクラス</span><span class="sxs-lookup"><span data-stu-id="ec1fa-125">Project Items and Classes in the Script Component Project</span></span>
 <span data-ttu-id="ec1fa-126">コード デザイン モードに切り替えると、VSTA IDE が開き、`ScriptMain` プロジェクト アイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-126">When you switch to code design mode, the VSTA IDE opens and displays the `ScriptMain` project item.</span></span> <span data-ttu-id="ec1fa-127">`ScriptMain` プロジェクト アイテムには、編集可能な `ScriptMain` クラスが含まれています。このクラスは、スクリプトのエントリ ポイントとしての役割を果たし、ここにコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-127">The `ScriptMain` project item contains the editable `ScriptMain` class, which serves as the entry point for the script and which is where you write your code.</span></span> <span data-ttu-id="ec1fa-128">このクラスのコード要素は、スクリプト タスクに対して選択したプログラミング言語に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-128">The code elements in the class vary depending on the programming language that you selected for the Script task.</span></span>

 <span data-ttu-id="ec1fa-129">スクリプト プロジェクトには、次の 2 つの読み取り専用のプロジェクト アイテムが自動生成され、追加されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-129">The script project contains two additional auto-generated read-only project items:</span></span>

-   <span data-ttu-id="ec1fa-130">次の 3 つのクラスを含む `ComponentWrapper` プロジェクト アイテム。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-130">The `ComponentWrapper` project item contains three classes:</span></span>

    -   <span data-ttu-id="ec1fa-131">`UserComponent` クラス。<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> から継承され、データの処理およびパッケージとのやり取りに使用するメソッドおよびプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-131">The `UserComponent` class, which inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> and contains the methods and properties that you will use to process data and to interact with the package.</span></span> <span data-ttu-id="ec1fa-132">`ScriptMain` クラスは `UserComponent` クラスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-132">The `ScriptMain` class inherits from the `UserComponent` class.</span></span>

    -   <span data-ttu-id="ec1fa-133">`Connections` コレクション クラス。[スクリプト変換エディター] の [接続マネージャー] ページで選択された、接続への参照が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-133">A `Connections` collection class that contains references to the connections selected on the Connection Manager page of the Script Transformation Editor.</span></span>

    -   <span data-ttu-id="ec1fa-134">[ `Variables` `ReadOnlyVariable` `ReadWriteVariables` **スクリプト変換エディター**] の [**スクリプト**] ページにあるプロパティおよびプロパティに入力された変数への参照を含むコレクションクラス。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-134">A `Variables` collection class that contains references to the variables entered in the `ReadOnlyVariable` and `ReadWriteVariables` properties on the **Script** page of the **Script Transformation Editor**.</span></span>

-   <span data-ttu-id="ec1fa-135">プロジェクトアイテムには、[ `BufferWrapper` <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> **スクリプト変換エディター**] の [**入力および出力**] ページで構成された各入力および出力に対して、から継承されるクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-135">The `BufferWrapper` project item contains a class that inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> for each input and output configured on the **Inputs and Outputs** page of the **Script Transformation Editor**.</span></span> <span data-ttu-id="ec1fa-136">これらの各クラスには、構成された入力列と出力列、およびそれらの列が含まれるデータ フロー バッファーに対応する、型指定されたアクセサー プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-136">Each of these classes contains typed accessor properties that correspond to the configured input and output columns, and the data flow buffers that contain the columns.</span></span>

 <span data-ttu-id="ec1fa-137">これらのオブジェクト、メソッド、およびプロパティの使用方法については、「[スクリプト コンポーネントのオブジェクト モデルについて](understanding-the-script-component-object-model.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-137">For information about how to use these objects, methods, and properties, see [Understanding the Script Component Object Model](understanding-the-script-component-object-model.md).</span></span> <span data-ttu-id="ec1fa-138">特定の種類のスクリプト コンポーネントで、これらのクラスのメソッドおよびプロパティを使用する方法については、セクション「[その他のスクリプト コンポーネントの例](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-138">For information about how to use the methods and properties of these classes in a particular type of Script component, see the section [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span> <span data-ttu-id="ec1fa-139">サンプルについてのトピックでは、完全なコード例も示します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-139">The example topics also contain complete code samples.</span></span>

 <span data-ttu-id="ec1fa-140">スクリプトコンポーネントを変換として構成すると、 `ScriptMain` プロジェクトアイテムには次の自動生成されたコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-140">When you configure the Script component as a transformation, the `ScriptMain` project item contains the following autogenerated code.</span></span> <span data-ttu-id="ec1fa-141">コード テンプレートでも、スクリプト コンポーネントの概要、および、変数、イベント、接続など、SSIS オブジェクトを取得および操作する方法に関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-141">The code template also provides an overview of the Script component, and additional information on how to retrieve and manipulate SSIS objects, such as variables, events, and connections.</span></span>

```vb
' Microsoft SQL Server Integration Services Script Component
' Write scripts using Microsoft Visual Basic 2008.
' ScriptMain is the entry point class of the script.

Imports System
Imports System.Data
Imports System.Math
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

<Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute> _
<CLSCompliant(False)> _
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub PreExecute()
        MyBase.PreExecute()
        '
        ' Add your code here for preprocessing or remove if not needed
        '
    End Sub

    Public Overrides Sub PostExecute()
        MyBase.PostExecute()
        '
        ' Add your code here for postprocessing or remove if not needed
        ' You can set read/write variables here, for example:
        ' Me.Variables.MyIntVar = 100
        '
    End Sub

    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)
        '
        ' Add your code here
        '
    End Sub

End Class
```

```csharp
/* Microsoft SQL Server Integration Services user script component
*  Write scripts using Microsoft Visual C# 2008.
*  ScriptMain is the entry point class of the script.*/

using System;
using System.Data;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

[Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute]
public class ScriptMain : UserComponent
{

    public override void PreExecute()
    {
        base.PreExecute();
        /*
          Add your code here for preprocessing or remove if not needed
        */
    }

    public override void PostExecute()
    {
        base.PostExecute();
        /*
          Add your code here for postprocessing or remove if not needed
          You can set read/write variables here, for example:
          Variables.MyIntVar = 100
        */
    }

    public override void Input0_ProcessInputRow(Input0Buffer Row)
    {
        /*
          Add your code here
        */
    }

}
```

#### <a name="additional-project-items-in-the-script-component-project"></a><span data-ttu-id="ec1fa-142">スクリプト コンポーネント プロジェクトのその他のプロジェクト アイテム</span><span class="sxs-lookup"><span data-stu-id="ec1fa-142">Additional Project Items in the Script Component Project</span></span>
 <span data-ttu-id="ec1fa-143">スクリプト コンポーネント プロジェクトには、既定の `ScriptMain` アイテム以外のアイテムを格納できます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-143">The Script component project can include items other than the default `ScriptMain` item.</span></span> <span data-ttu-id="ec1fa-144">プロジェクトには、クラス、モジュール、コード ファイル、およびフォルダーを追加できます。また、フォルダーを使用してアイテムのグループを整理できます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-144">You can add classes, modules, code files, and folders to the project, and you can use folders to organize groups of items.</span></span>

 <span data-ttu-id="ec1fa-145">追加したすべてのアイテムは、パッケージ内部に保存されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-145">All the items that you add are persisted inside the package.</span></span>

#### <a name="references-in-the-script-component-project"></a><span data-ttu-id="ec1fa-146">スクリプト コンポーネント プロジェクトの参照</span><span class="sxs-lookup"><span data-stu-id="ec1fa-146">References in the Script Component Project</span></span>
 <span data-ttu-id="ec1fa-147">参照をマネージド アセンブリに追加するには、 **[プロジェクト エクスプローラー]** でスクリプト タスク プロジェクトを右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-147">You can add references to managed assemblies by right-clicking the Script task project in **Project Explorer**, and then clicking **Add Reference**.</span></span> <span data-ttu-id="ec1fa-148">詳しくは、「[スクリプティング ソリューションでの他のアセンブリの参照](../referencing-other-assemblies-in-scripting-solutions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-148">For more information, see [Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="ec1fa-149">プロジェクト参照は、VSTA IDE の **[クラス ビュー]** または**プロジェクト エクスプローラー**で表示できます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-149">You can view project references in the VSTA IDE in **Class View** or in **Project Explorer**.</span></span> <span data-ttu-id="ec1fa-150">どちらのウィンドウも **[表示]** メニューから開きます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-150">You open either of these windows from the **View** menu.</span></span> <span data-ttu-id="ec1fa-151">新しい参照は、 **[プロジェクト]** メニュー、**プロジェクト エクスプローラー**、または **[クラス ビュー]** から追加できます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-151">You can add a new reference from the **Project** menu, from **Project Explorer**, or from **Class View**.</span></span>

## <a name="interacting-with-the-package-in-the-script-component"></a><span data-ttu-id="ec1fa-152">スクリプト コンポーネント内でのパッケージとの対話</span><span class="sxs-lookup"><span data-stu-id="ec1fa-152">Interacting with the Package in the Script Component</span></span>
 <span data-ttu-id="ec1fa-153">スクリプト コンポーネント内で記述するカスタム スクリプトは、自動生成された基本クラス内の、厳密に型指定されたアクセサーを使用して、コンポーネントに含まれているパッケージの変数や接続マネージャーにアクセスし、それらを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-153">The custom script that you write in the Script component can access and use variables and connection managers from the containing package through strongly-typed accessors in the auto-generated base classes.</span></span> <span data-ttu-id="ec1fa-154">ただし、変数および接続マネージャーをスクリプトで使用できるようにするには、コード デザイン モードに切り替える前に、その両方を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-154">However, you must configure both variables and connection managers before entering code-design mode if you want to make them available to your script.</span></span> <span data-ttu-id="ec1fa-155">また、スクリプト コンポーネントのコードから、イベントを発生させたり、ログ記録を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-155">You can also raise events and perform logging from your Script component code.</span></span>

 <span data-ttu-id="ec1fa-156">スクリプト コンポーネント プロジェクト内に自動生成されるプロジェクト アイテムには、パッケージと情報をやり取りするために、以下のオブジェクト、メソッド、およびプロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-156">The autogenerated project items in the Script component project provide the following objects, methods, and properties for interacting with the package.</span></span>

|<span data-ttu-id="ec1fa-157">パッケージの機能</span><span class="sxs-lookup"><span data-stu-id="ec1fa-157">Package Feature</span></span>|<span data-ttu-id="ec1fa-158">アクセス方法</span><span class="sxs-lookup"><span data-stu-id="ec1fa-158">Access Method</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="ec1fa-159">変数:</span><span class="sxs-lookup"><span data-stu-id="ec1fa-159">Variables</span></span>|<span data-ttu-id="ec1fa-160">`Variables` プロジェクト アイテムの `ComponentWrapper` コレクション クラス内の、名前付きで型指定されたアクセサー プロパティを使用します。これは `Variables` クラスの `ScriptMain` プロパティを介して公開されています。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-160">Use the named and typed accessor properties in the `Variables` collection class in the `ComponentWrapper` project item, exposed through the `Variables` property of the `ScriptMain` class.</span></span><br /><br /> <span data-ttu-id="ec1fa-161">`PreExecute` メソッドでは、読み取り専用変数にのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-161">The `PreExecute` method can access only read-only variables.</span></span> <span data-ttu-id="ec1fa-162">`PostExecute` メソッドでは、読み取り専用変数および読み取り/書き込み変数の両方にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-162">The `PostExecute` method can access both read-only and read/write variables.</span></span>|
|<span data-ttu-id="ec1fa-163">接続</span><span class="sxs-lookup"><span data-stu-id="ec1fa-163">Connections</span></span>|<span data-ttu-id="ec1fa-164">`Connections` プロジェクト アイテムの `ComponentWrapper` コレクション クラス内の、名前付きで型指定されたアクセサー プロパティを使用します。これは `Connections` クラスの `ScriptMain` プロパティを介して公開されています。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-164">Use the named and typed accessor properties in the `Connections` collection class in the `ComponentWrapper` project item, exposed through the `Connections` property of the `ScriptMain` class.</span></span>|
|<span data-ttu-id="ec1fa-165">events</span><span class="sxs-lookup"><span data-stu-id="ec1fa-165">Events</span></span>|<span data-ttu-id="ec1fa-166"><xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>クラスのプロパティ `ScriptMain` とインターフェイスの\*\*Fire \<X> \*\*メソッドを使用して、イベントを発生させ <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> ます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-166">Raise events by using the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the `ScriptMain` class and the **Fire\<X>** methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span>|
|<span data-ttu-id="ec1fa-167">ログ記録</span><span class="sxs-lookup"><span data-stu-id="ec1fa-167">Logging</span></span>|<span data-ttu-id="ec1fa-168">`ScriptMain` クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> メソッドを使用して、ログ記録を実行します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-168">Perform logging by using the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method of the `ScriptMain` class.</span></span>|

## <a name="debugging-the-script-component"></a><span data-ttu-id="ec1fa-169">スクリプト コンポーネントのデバッグ</span><span class="sxs-lookup"><span data-stu-id="ec1fa-169">Debugging the Script Component</span></span>
 <span data-ttu-id="ec1fa-170">スクリプト コンポーネントのコードをデバッグするには、コードに少なくとも 1 つのブレークポイントを設定し、VSTA IDE を閉じて [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-170">To debug the code in your Script component, set at least one breakpoint in the code, and then close the VSTA IDE to run the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="ec1fa-171">パッケージが実行されてスクリプト コンポーネントが開始されると、VSTA IDE が再度開き、読み取り専用モードでコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-171">When package execution enters the Script component, the VSTA IDE reopens and displays your code in read-only mode.</span></span> <span data-ttu-id="ec1fa-172">実行によりブレークポイントに到達したら、変数の値の検証や、残りのコードのステップ スルーができます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-172">After execution reaches your breakpoint, you can examine variable values and step through the remaining code.</span></span>

> [!NOTE]
>  <span data-ttu-id="ec1fa-173">パッケージ実行タスクから実行されている子パッケージの一部としてスクリプト コンポーネントを実行する場合は、スクリプト コンポーネントをデバッグできません。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-173">You cannot debug a Script component when you run the Script component as part of a child package that is run from an Execute Package task.</span></span> <span data-ttu-id="ec1fa-174">このような場合は、子パッケージのスクリプト コンポーネント内で設定したブレークポイントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-174">Breakpoints that you set in the Script component in the child package are disregarded in these circumstances.</span></span> <span data-ttu-id="ec1fa-175">子パッケージを単独で実行することにより、通常どおりパッケージをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-175">You can debug the child package normally by running it separately.</span></span>

> [!NOTE]
>  <span data-ttu-id="ec1fa-176">複数のスクリプト コンポーネントが含まれるパッケージをデバッグする場合、デバッガーによってデバッグされるスクリプト コンポーネントは 1 つです。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-176">When you debug a package that contains multiple Script components, the debugger debugs one Script component.</span></span> <span data-ttu-id="ec1fa-177">Foreach ループまたは For ループ コンテナーの場合と同様に、デバッガーが完了した場合、システムは別のスクリプト コンポーネントをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-177">The system can debug another Script component if the debugger completes, as in the case of a Foreach Loop or For Loop container.</span></span>

 <span data-ttu-id="ec1fa-178">ただし、次の方法を使用することにより、スクリプト コンポーネントの実行を監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-178">You can also monitor the execution of the Script component by using the following methods:</span></span>

-   <span data-ttu-id="ec1fa-179">実行を中断し、system.string 名前空間のメソッドを使用してモーダルメッセージを表示し `MessageBox.Show` ます**System.Windows.Forms** 。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-179">Interrupt execution and display a modal message by using the `MessageBox.Show` method in the **System.Windows.Forms** namespace.</span></span> <span data-ttu-id="ec1fa-180">デバッグが完了したら、このコードは削除してください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-180">(Remove this code after you complete the debugging process.)</span></span>

-   <span data-ttu-id="ec1fa-181">情報メッセージ、警告、およびエラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-181">Raise events for informational messages, warnings, and errors.</span></span> <span data-ttu-id="ec1fa-182">FireInformation、FireWarning、FireError の各メソッドでは、イベントの説明が Visual Studio の **[出力]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-182">The FireInformation, FireWarning, and FireError methods display the event description in the Visual Studio **Output** window.</span></span> <span data-ttu-id="ec1fa-183">ただし、FireProgress メソッド、Console.Write メソッド、および Console.WriteLine メソッドでは、 **[出力]** ウィンドウに情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-183">However, the FireProgress method, the Console.Write method, and Console.WriteLine method do not display any information in the **Output** window.</span></span> <span data-ttu-id="ec1fa-184">FireProgress イベントからのメッセージが [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーの **[進行状況]** タブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-184">Messages from the FireProgress event appear on the **Progress** tab of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ec1fa-185">詳しくは、「[スクリプト コンポーネントでのイベントの発生](../../data-flow/transformations/script-component.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-185">For more information, see [Raising Events in the Script Component](../../data-flow/transformations/script-component.md).</span></span>

-   <span data-ttu-id="ec1fa-186">イベントまたはユーザー定義のメッセージを、有効なログ プロバイダーに記録します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-186">Log events or user-defined messages to enabled logging providers.</span></span> <span data-ttu-id="ec1fa-187">詳しくは、「[スクリプト コンポーネントでのログ記録](logging-in-the-script-component.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-187">For more information, see [Logging in the Script Component](logging-in-the-script-component.md).</span></span>

 <span data-ttu-id="ec1fa-188">データを変換先に保存せずに、変換元または変換として構成されたスクリプト コンポーネントの出力を調べるだけの場合は、[行数変換](../../data-flow/transformations/row-count-transformation.md)を使ってデータ フローを終了し、スクリプト コンポーネントの出力にデータ ビューアーをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-188">If you just want to examine the output of a Script component configured as a source or as a transformation, without saving the data to a destination, you can stop the data flow with a [Row Count Transformation](../../data-flow/transformations/row-count-transformation.md) and attach a data viewer to the output of the Script component.</span></span> <span data-ttu-id="ec1fa-189">データ ビューアーについて詳しくは、「[データ フローのデバッグ](../../troubleshooting/debugging-data-flow.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-189">For information about data viewers, see [Debugging Data Flow](../../troubleshooting/debugging-data-flow.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ec1fa-190">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ec1fa-190">In This Section</span></span>
 <span data-ttu-id="ec1fa-191">スクリプト コンポーネントのコーディングの詳細については、このセクションの次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-191">For more information about coding the Script component, see the following topics in this section.</span></span>

 <span data-ttu-id="ec1fa-192">[スクリプトコンポーネントのオブジェクトモデルについて](understanding-the-script-component-object-model.md)スクリプトコンポーネントで使用できるオブジェクト、メソッド、およびプロパティの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-192">[Understanding the Script Component Object Model](understanding-the-script-component-object-model.md) Explains how to use the objects, methods, and properties available in the Script component.</span></span>

 <span data-ttu-id="ec1fa-193">[スクリプトソリューションでの他のアセンブリの参照](../referencing-other-assemblies-in-scripting-solutions.md)スクリプトコンポーネントのクラスライブラリからオブジェクトを参照する方法について説明 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-193">[Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md) Explains how to reference objects from the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library in the Script component.</span></span>

 <span data-ttu-id="ec1fa-194">[スクリプトコンポーネントに対するエラー出力のシミュレート](../../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)スクリプトコンポーネントによる処理中にエラーが発生する行のエラー出力をシミュレートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-194">[Simulating an Error Output for the Script Component](../../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md) Explains how to simulate an error output for rows that raise errors during processing by the Script component.</span></span>

## <a name="external-resources"></a><span data-ttu-id="ec1fa-195">外部リソース</span><span class="sxs-lookup"><span data-stu-id="ec1fa-195">External Resources</span></span>

-   <span data-ttu-id="ec1fa-196">blogs.msdn.com のブログ「[VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661)」(SSIS 2008 インストールおよび R2 インストールでの VSTA のセットアップと構成に関する問題)。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-196">Blog entry, [VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661), on blogs.msdn.com.</span></span>

<span data-ttu-id="ec1fa-197">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="ec1fa-197">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ec1fa-198">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-198">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ec1fa-199">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="ec1fa-199">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ec1fa-200">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="ec1fa-200">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec1fa-201">参照</span><span class="sxs-lookup"><span data-stu-id="ec1fa-201">See Also</span></span>
 [<span data-ttu-id="ec1fa-202">スクリプト コンポーネント エディターでのスクリプト コンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="ec1fa-202">Configuring the Script Component in the Script Component Editor</span></span>](configuring-the-script-component-in-the-script-component-editor.md)


