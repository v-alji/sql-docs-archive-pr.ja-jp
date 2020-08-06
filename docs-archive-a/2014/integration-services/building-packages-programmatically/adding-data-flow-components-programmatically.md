---
title: プログラムによるデータ フロー コンポーネントの追加| Microsoft Docs
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
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: c06065cf-43e5-4b6b-9824-7309d7f5e35e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 807e758e42b738c4b0bf64b1d6f48bc29649ae6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639614"
---
# <a name="adding-data-flow-components-programmatically"></a><span data-ttu-id="793d8-102">プログラムによるデータ フロー コンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="793d8-102">Adding Data Flow Components Programmatically</span></span>
  <span data-ttu-id="793d8-103">データ フローを作成するには、最初にコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="793d8-103">When you build a data flow, you start by adding components.</span></span> <span data-ttu-id="793d8-104">次に、追加したコンポーネントを構成して相互に接続し、実行時のデータ フローを確立します。</span><span class="sxs-lookup"><span data-stu-id="793d8-104">Then you configure those components and connect them together to establish the flow of data at run time.</span></span> <span data-ttu-id="793d8-105">このセクションでは、データ フロー タスクへのコンポーネントの追加、コンポーネントのデザイン時インスタンスの作成、およびコンポーネントの構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="793d8-105">This section describes adding a component to the data flow task, creating the design-time instance of the component, and then configuring the component.</span></span> <span data-ttu-id="793d8-106">コンポーネントの接続方法については、「[プログラムによるデータ フロー コンポーネントの接続](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="793d8-106">For information about how to connect components, see [Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
## <a name="adding-a-component"></a><span data-ttu-id="793d8-107">コンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="793d8-107">Adding a Component</span></span>  
 <span data-ttu-id="793d8-108"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaDataCollection100.New%2A> コレクションの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.ComponentMetaDataCollection%2A> メソッドを呼び出して新しいコンポーネントを作成し、データ フロー タスクに追加します。</span><span class="sxs-lookup"><span data-stu-id="793d8-108">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaDataCollection100.New%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.ComponentMetaDataCollection%2A> collection to create a new component and add it to the data flow task.</span></span> <span data-ttu-id="793d8-109">このメソッドは、コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスを返します。</span><span class="sxs-lookup"><span data-stu-id="793d8-109">This method returns the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface of the component.</span></span> <span data-ttu-id="793d8-110">ただしこの時点で、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> には、いずれかのコンポーネントに固有な情報は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="793d8-110">However, at this point, the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> does not contain information specific to any one component.</span></span> <span data-ttu-id="793d8-111"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> プロパティを設定し、コンポーネントの種類を識別します。</span><span class="sxs-lookup"><span data-stu-id="793d8-111">Set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property to identify the type of component.</span></span> <span data-ttu-id="793d8-112">データ フロー タスクはこのプロパティの値を使用して、実行時にコンポーネントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="793d8-112">The data flow task uses the value of this property to create an instance of the component at run time.</span></span>  
  
 <span data-ttu-id="793d8-113"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> プロパティの値には、CLSID、PROGID、またはコンポーネントの <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> プロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="793d8-113">The value specified in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property can be the CLSID, PROGID, or <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> property of the component.</span></span> <span data-ttu-id="793d8-114">CLSID は通常、コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> プロパティの値として [プロパティ] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="793d8-114">The CLSID is normally displayed in the Properties window as the value of the component's <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property.</span></span> <span data-ttu-id="793d8-115">このプロパティ、および使用できるコンポーネントの他のプロパティの取得については、「[プログラムによるデータ フロー コンポーネントの検出](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="793d8-115">For information about obtaining this property and other properties of available components, see [Discovering Data Flow Components Programmatically](../building-packages-programmatically/discovering-data-flow-components-programmatically.md).</span></span>  
  
## <a name="adding-a-managed-component"></a><span data-ttu-id="793d8-116">マネージド コンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="793d8-116">Adding a Managed Component</span></span>  
 <span data-ttu-id="793d8-117">CLSID または PROGID を使用して、いずれかのマネージド データ フロー コンポーネントをデータ フローに追加することはできません。これらの値はコンポーネント自体ではなく、ラッパーを指しているためです。</span><span class="sxs-lookup"><span data-stu-id="793d8-117">You cannot use the CLSID or PROGID to add one the managed data flow components to the data flow, because these values point to a wrapper and not to the component itself.</span></span> <span data-ttu-id="793d8-118">その代わり、次のサンプルに示すように、`CreationName` プロパティまたは `AssemblyQualifiedName` プロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="793d8-118">Instead you can use the `CreationName` property or the `AssemblyQualifiedName` property as shown in the following sample.</span></span>  
  
 <span data-ttu-id="793d8-119">`AssemblyQualifiedName` プロパティを使用する場合は、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プロジェクトで、マネージド コンポーネントを含んでいるアセンブリに参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="793d8-119">If you intend to use the `AssemblyQualifiedName` property, then you must add a reference in your [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] project to the assembly that contains the managed component.</span></span> <span data-ttu-id="793d8-120">これらのアセンブリは、 **[参照の追加]** ダイアログ ボックスの [.NET] タブに一覧表示されません。</span><span class="sxs-lookup"><span data-stu-id="793d8-120">These assemblies are not listed on the .NET tab of the **Add Reference** dialog box.</span></span> <span data-ttu-id="793d8-121">通常は、**C:\Program Files\Microsoft SQL Server\100\DTS\PipelineComponents** フォルダーを参照してアセンブリを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="793d8-121">Normally you must browse to locate the assembly in the **C:\Program Files\Microsoft SQL Server\100\DTS\PipelineComponents** folder.</span></span>  
  
 <span data-ttu-id="793d8-122">組み込みマネージド データ フロー コンポーネントの要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="793d8-122">The built-in managed data flow components include:</span></span>  
  
-   [!INCLUDE[vstecado](../../includes/vstecado-md.md)] <span data-ttu-id="793d8-123">ソース</span><span class="sxs-lookup"><span data-stu-id="793d8-123">Source</span></span>  
  
-   <span data-ttu-id="793d8-124">XML ソース</span><span class="sxs-lookup"><span data-stu-id="793d8-124">XML Source</span></span>  
  
-   <span data-ttu-id="793d8-125">DataReader 変換先</span><span class="sxs-lookup"><span data-stu-id="793d8-125">DataReader Destination</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="793d8-126">Compact 変換先</span><span class="sxs-lookup"><span data-stu-id="793d8-126">Compact Destination</span></span>  
  
-   <span data-ttu-id="793d8-127">スクリプト コンポーネント</span><span class="sxs-lookup"><span data-stu-id="793d8-127">Script Component</span></span>  
  
 <span data-ttu-id="793d8-128">次のコード サンプルは、マネージド コンポーネントをデータ フローに追加するための 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="793d8-128">The following code sample shows both ways of adding a managed component to the data flow:</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Microsoft.SqlServer.Dts.Runtime.Package package = new Microsoft.SqlServer.Dts.Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Microsoft.SqlServer.Dts.Runtime.TaskHost thMainPipe = (Microsoft.SqlServer.Dts.Runtime.TaskHost)e;  
      MainPipe dataFlowTask = (MainPipe)thMainPipe.InnerObject;  
  
      // The Application object will be used to obtain the CreationName  
      //  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
      Application app = new Application();  
  
      // Add a first ADO NET source to the data flow.  
      //  The CreationName property requires an Application instance.  
      IDTSComponentMetaData100 component1 = dataFlowTask.ComponentMetaDataCollection.New();  
      component1.Name = "DataReader Source";  
      component1.ComponentClassID = app.PipelineComponentInfos["DataReader Source"].CreationName;  
  
      // Add a second ADO NET source to the data flow.  
      //  The AssemblyQualifiedName property requires a reference to the assembly.  
      IDTSComponentMetaData100 component2 = dataFlowTask.ComponentMetaDataCollection.New();  
      component2.Name = "DataReader Source";  
      component2.ComponentClassID = typeof(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName;  
    }  
  }  
}  
  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' The Application object will be used to obtain the CreationName  
    '  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
    Dim app As New Application()  
  
    ' Add a first ADO NET source to the data flow.  
    '  The CreationName property requires an Application instance.  
    Dim component1 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component1.Name = "DataReader Source"  
    component1.ComponentClassID = app.PipelineComponentInfos("DataReader Source").CreationName  
  
    ' Add a second ADO NET source to the data flow.  
    '  The AssemblyQualifiedName property requires a reference to the assembly.  
    Dim component2 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component2.Name = "DataReader Source"  
    component2.ComponentClassID = _  
      GetType(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName  
  
  End Sub  
  
End Module  
```  
  
## <a name="creating-the-design-time-instance-of-the-component"></a><span data-ttu-id="793d8-129">コンポーネントのデザイン時インスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="793d8-129">Creating the Design-time Instance of the Component</span></span>  
 <span data-ttu-id="793d8-130"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> メソッドを呼び出し、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> プロパティによって識別される、コンポーネントのデザイン時インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="793d8-130">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> method to create the design time instance of the component identified by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property.</span></span> <span data-ttu-id="793d8-131">このメソッドは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> インターフェイスのマネージド ラッパーである <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="793d8-131">This method returns the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> object, which is the managed wrapper for the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>  
  
 <span data-ttu-id="793d8-132">可能な限り、コンポーネントのメタデータを直接変更するのではなく、必ずデザイン時インスタンスのメソッドを使用して、コンポーネントを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="793d8-132">Whenever possible, you should modify a component by using the methods of the design-time instance instead of by modifying the component metadata directly.</span></span> <span data-ttu-id="793d8-133">メタデータには、接続など、直接設定する必要のあるアイテムがありますが、メタデータを直接変更すると、コンポーネントが変更を監視および検証する機能がバイパスされるため、一般的にはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="793d8-133">Although there are items in the metadata that you must set directly, such as connections, generally it is inadvisable to modify the metadata directly because you bypass the ability of the component to monitor and validate changes.</span></span>  
  
## <a name="assigning-connections"></a><span data-ttu-id="793d8-134">接続の割り当て</span><span class="sxs-lookup"><span data-stu-id="793d8-134">Assigning Connections</span></span>  
 <span data-ttu-id="793d8-135">OLE DB ソース コンポーネントなどの一部のコンポーネントは外部データに接続する必要があるため、パッケージ内にある既存の <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトをこの目的で使用します。</span><span class="sxs-lookup"><span data-stu-id="793d8-135">Some components, such as the OLE DB Source component, require a connection to external data and use an existing <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object in the package for this purpose.</span></span> <span data-ttu-id="793d8-136"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnectionCollection100.Count%2A> コレクションの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> プロパティは、コンポーネントが必要とする、実行時の <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトの数を示します。</span><span class="sxs-lookup"><span data-stu-id="793d8-136">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnectionCollection100.Count%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> collection indicates the number of run-time <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects required by the component.</span></span> <span data-ttu-id="793d8-137">この数が 0 より大きい場合、コンポーネントには接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="793d8-137">If the count is greater than zero, the component requires a connection.</span></span> <span data-ttu-id="793d8-138"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.ConnectionManager%2A> の最初の接続の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.Name%2A> および <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> プロパティを指定して、パッケージの接続マネージャーをコンポーネントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="793d8-138">Assign a connection manager from the package to the component by specifying the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.ConnectionManager%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.Name%2A> properties of the first connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.</span></span> <span data-ttu-id="793d8-139">実行時の接続コレクション内にある接続マネージャーの名前は、パッケージから参照される接続マネージャーの名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="793d8-139">Note that the name of the connection manager in the run-time connection collection must match the name of the connection managerreferenced from the package.</span></span>  
  
## <a name="setting-the-values-of-custom-properties"></a><span data-ttu-id="793d8-140">カスタム プロパティの値の設定</span><span class="sxs-lookup"><span data-stu-id="793d8-140">Setting the Values of Custom Properties</span></span>  
 <span data-ttu-id="793d8-141">コンポーネントのデザイン時インスタンスを作成したら、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="793d8-141">After creating the design-time instance of the component, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="793d8-142">このメソッドは、コンストラクターと同様、新しく作成されたコンポーネントのカスタム プロパティと入力および出力オブジェクトを作成することにより、そのコンポーネントを初期化します。</span><span class="sxs-lookup"><span data-stu-id="793d8-142">This method is similar to a constructor because it initializes a newly created component by creating its custom properties and its input and output objects.</span></span> <span data-ttu-id="793d8-143">コンポーネントがリセットされ、メタデータに加えられた以前の変更が失われるため、1 つのコンポーネントで <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> を複数回呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="793d8-143">Do not call <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> more than one time on a component, because the component may reset itself and lose any modifications previously made to its metadata.</span></span>  
  
 <span data-ttu-id="793d8-144">コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.CustomPropertyCollection%2A> には、コンポーネント固有の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> オブジェクトのコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="793d8-144">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.CustomPropertyCollection%2A> of the component contains a collection of <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> objects specific to the component.</span></span> <span data-ttu-id="793d8-145">オブジェクトのプロパティが常に可視である他のプログラミング モデルとは異なり、コンポーネントは <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> メソッドが呼び出されたときにのみ、そのコンポーネントのカスタム プロパティのコレクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="793d8-145">Unlike other programming models, where the properties of an object are always visible on the object, components only populate their custom property collections when you call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="793d8-146">メソッドを呼び出したら、コンポーネントのデザイン時インスタンスの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.SetComponentProperty%2A> メソッドを使用して、コンポーネントのカスタム プロパティに値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="793d8-146">After you call method, use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.SetComponentProperty%2A> method of the design-time instance of the component to assign values to its custom properties.</span></span> <span data-ttu-id="793d8-147">このメソッドは、カスタム プロパティを識別する名前と値のペアを受け取り、新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="793d8-147">This method accepts a name/value pair that identifies the custom property and provides its new value.</span></span>  
  
## <a name="initializing-output-columns"></a><span data-ttu-id="793d8-148">出力列の初期化</span><span class="sxs-lookup"><span data-stu-id="793d8-148">Initializing Output Columns</span></span>  
 <span data-ttu-id="793d8-149">コンポーネントをタスクに追加して構成したら、オブジェクトの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> で列のコレクションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="793d8-149">After you add a component to the task and configure it, initialize the collection of columns in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the object.</span></span> <span data-ttu-id="793d8-150">この手順は変換元コンポーネントに特に関連するものです。変換および変換先コンポーネントの列は、一般的に、上流コンポーネントから受け取る列に依存するため、この手順では初期化されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="793d8-150">This step is especially relevant for source components, but may not initialize the columns for transformation and destination components because they generally depend on the columns that they receive from upstream components.</span></span>  
  
 <span data-ttu-id="793d8-151"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> メソッドを呼び出し、変換元コンポーネントの出力の列を初期化します。</span><span class="sxs-lookup"><span data-stu-id="793d8-151">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> method to initialize the columns in the outputs of a source component.</span></span> <span data-ttu-id="793d8-152">コンポーネントは外部データ ソースに自動的には接続されないので、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.AcquireConnections%2A> を呼び出す前に <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> メソッドを呼び出して、コンポーネントに外部データ ソースへのアクセスを提供し、列のメタデータを設定します。</span><span class="sxs-lookup"><span data-stu-id="793d8-152">Because components do not automatically connect to external data sources, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.AcquireConnections%2A> method before calling <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> to provide the component access to its external data source and the ability to populate its column metadata.</span></span> <span data-ttu-id="793d8-153">最後に <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReleaseConnections%2A> メソッドを呼び出し、接続を解放します。</span><span class="sxs-lookup"><span data-stu-id="793d8-153">Finally, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReleaseConnections%2A> method to release the connection.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="793d8-154">次の手順</span><span class="sxs-lookup"><span data-stu-id="793d8-154">Next Step</span></span>  
 <span data-ttu-id="793d8-155">コンポーネントを追加して構成したら、次の手順としてコンポーネント間のパスを作成します。これについては、トピック「[2 つのコンポーネント間のパスの作成](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)」で説明します。</span><span class="sxs-lookup"><span data-stu-id="793d8-155">After adding and configuring the component, the next step is to create paths between components, which is discussed in the topic, [Creating a Path Between Two Components](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="793d8-156">サンプル</span><span class="sxs-lookup"><span data-stu-id="793d8-156">Sample</span></span>  
 <span data-ttu-id="793d8-157">次のコード例は、OLE DB ソース コンポーネントをデータ フロー タスクに追加し、コンポーネントのデザイン時インスタンスを作成して、コンポーネントのプロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="793d8-157">The following code sample adds the OLE DB Source component to a data flow task, creates a design-time instance of the component, and configures the component's properties.</span></span> <span data-ttu-id="793d8-158">この例では、アセンブリ Microsoft.SqlServer.DTSRuntimeWrap に対する追加の参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="793d8-158">This example requires an additional reference to the assembly Microsoft.SqlServer.DTSRuntimeWrap.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Runtime.Package package = new Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Runtime.TaskHost thMainPipe = e as Runtime.TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Add an OLEDB connection manager to the package.  
      ConnectionManager cm = package.Connections.Add("OLEDB");  
      cm.Name = "OLEDB ConnectionManager";  
      cm.ConnectionString = "Data Source=(local);" +   
        "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" +   
        "Integrated Security=SSPI;"  
  
      // Add an OLE DB source to the data flow.  
      IDTSComponentMetaData100 component =   
        dataFlowTask.ComponentMetaDataCollection.New();  
      component.Name = "OLEDBSource";  
      component.ComponentClassID = "DTSAdapter.OleDbSource.1";  
      // You can also use the CLSID of the component instead of the PROGID.  
      //component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
      // Get the design time instance of the component.  
      CManagedComponentWrapper instance = component.Instantiate();  
  
      // Initialize the component  
      instance.ProvideComponentProperties();  
  
      // Specify the connection manager.  
      if (component.RuntimeConnectionCollection.Count > 0)  
      {  
        component.RuntimeConnectionCollection[0].ConnectionManager =   
          DtsConvert.GetExtendedInterface(package.Connections[0]);  
        component.RuntimeConnectionCollection[0].ConnectionManagerID =   
          package.Connections[0].ID;      }  
  
      // Set the custom properties.  
      instance.SetComponentProperty("AccessMode", 2);  
      instance.SetComponentProperty("SqlCommand",   
        "Select * from Production.Product");  
  
      // Reinitialize the metadata.  
      instance.AcquireConnections(null);  
      instance.ReinitializeMetaData();  
      instance.ReleaseConnections();  
  
      // Add other components to the data flow and connect them.  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Add an OLEDB connection manager to the package.  
    Dim cm As ConnectionManager = package.Connections.Add("OLEDB")  
    cm.Name = "OLEDB ConnectionManager"  
    cm.ConnectionString = "Data Source=(local);" & _  
      "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;"  
  
    ' Add an OLE DB source to the data flow.  
    Dim component As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component.Name = "OLEDBSource"  
    component.ComponentClassID = "DTSAdapter.OleDbSource.1"  
    ' You can also use the CLSID of the component instead of the PROGID.  
    'component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
    ' Get the design time instance of the component.  
    Dim instance As CManagedComponentWrapper = component.Instantiate()  
  
    ' Initialize the component.  
    instance.ProvideComponentProperties()  
  
    ' Specify the connection manager.  
    If component.RuntimeConnectionCollection.Count > 0 Then  
      component.RuntimeConnectionCollection(0).ConnectionManager = _  
        DtsConvert.GetExtendedInterface(package.Connections(0))  
      component.RuntimeConnectionCollection(0).ConnectionManagerID = _  
        package.Connections(0).ID  
    End If  
  
    ' Set the custom properties.  
    instance.SetComponentProperty("AccessMode", 2)  
    instance.SetComponentProperty("SqlCommand", _  
      "Select * from Production.Product")  
  
    ' Reinitialize the metadata.  
    instance.AcquireConnections(vbNull)  
    instance.ReinitializeMetaData()  
    instance.ReleaseConnections()  
  
    ' Add other components to the data flow and connect them.  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="793d8-159">外部リソース</span><span class="sxs-lookup"><span data-stu-id="793d8-159">External Resources</span></span>  
 <span data-ttu-id="793d8-160">blogs.msdn.com のブログ「[EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223)」(EzAPI - SQL Server 2012 用の更新)</span><span class="sxs-lookup"><span data-stu-id="793d8-160">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="793d8-161">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="793d8-161">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="793d8-162">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="793d8-162">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="793d8-163">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="793d8-163">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="793d8-164">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="793d8-164">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793d8-165">参照</span><span class="sxs-lookup"><span data-stu-id="793d8-165">See Also</span></span>  
 [<span data-ttu-id="793d8-166">プログラムによるデータ フロー コンポーネントの接続</span><span class="sxs-lookup"><span data-stu-id="793d8-166">Connecting Data Flow Components Programmatically</span></span>](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
  
  
