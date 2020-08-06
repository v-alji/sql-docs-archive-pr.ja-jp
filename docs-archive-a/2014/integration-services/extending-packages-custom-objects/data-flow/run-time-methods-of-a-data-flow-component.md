---
title: データ フロー コンポーネントの実行時のメソッド | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- run-time [Integration Services]
- data flow components [Integration Services], run-time methods
ms.assetid: fd9e4317-18dd-43af-bbdc-79db32183ac4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df0afe4c29044541c5a57aa3a466283ab4fe4fef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718591"
---
# <a name="run-time-methods-of-a-data-flow-component"></a><span data-ttu-id="2cbc3-102">データ フロー コンポーネントの実行時のメソッド</span><span class="sxs-lookup"><span data-stu-id="2cbc3-102">Run-time Methods of a Data Flow Component</span></span>
  <span data-ttu-id="2cbc3-103">実行時に、データ フロー タスクは、コンポーネントの順序の確認、実行プランの準備、および作業プランを実行するワーカー スレッドのプールの管理を行います。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-103">At run time, the data flow task examines the sequence of components, prepares an execution plan, and manages a pool of worker threads that execute the work plan.</span></span> <span data-ttu-id="2cbc3-104">タスクは、データの行を変換元から読み込み、変換を使用して処理し、変換先に保存します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-104">The task loads rows of data from sources, processes them through transformations, then saves them to destinations.</span></span>  
  
## <a name="sequence-of-method-execution"></a><span data-ttu-id="2cbc3-105">メソッドの実行順序</span><span class="sxs-lookup"><span data-stu-id="2cbc3-105">Sequence of Method Execution</span></span>  
 <span data-ttu-id="2cbc3-106">データ フロー コンポーネントの実行中に、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基本クラス内のメソッドのサブセットが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-106">During the execution of a data flow component, a subset of the methods in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class is called.</span></span> <span data-ttu-id="2cbc3-107">呼び出されるメソッドとその順序は常に同じです。ただし、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> および <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドは例外です。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-107">The methods, and the sequence in which they are called, are always the same, with the exception of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span> <span data-ttu-id="2cbc3-108">これら 2 つのメソッドは、コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> および <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> オブジェクトの存在と構成に基づいて呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-108">These two methods are called based on the existence and configuration of a component's <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> objects.</span></span>  
  
 <span data-ttu-id="2cbc3-109">次の一覧では、コンポーネントの実行中に呼び出される順にメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-109">The following list shows the methods in the order in which they are called during component execution.</span></span> <span data-ttu-id="2cbc3-110"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> は、常に <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> の前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-110">Note that <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, when called, is always called before <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrepareForExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PostExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Cleanup%2A>  
  
### <a name="primeoutput-method"></a><span data-ttu-id="2cbc3-111">PrimeOutput メソッド</span><span class="sxs-lookup"><span data-stu-id="2cbc3-111">PrimeOutput Method</span></span>  
 <span data-ttu-id="2cbc3-112"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> メソッドは、コンポーネントに少なくとも 1 つの出力があり、その出力が <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> オブジェクトを介して下流コンポーネントにアタッチされ、出力の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> プロパティが 0 の場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-112">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> method is called when a component has at least one output, attached to a downstream component through an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object, and the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property of the output is zero.</span></span> <span data-ttu-id="2cbc3-113"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> メソッドは、非同期出力型の変換元コンポーネントと変換の場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-113">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> method is called for source components and for transformations with asynchronous outputs.</span></span> <span data-ttu-id="2cbc3-114">後述の <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドとは異なり、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドは必要とされる各コンポーネントに対して 1 回だけ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-114">Unlike the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method described below, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method is only called once for each component that requires it.</span></span>  
  
### <a name="processinput-method"></a><span data-ttu-id="2cbc3-115">ProcessInput メソッド</span><span class="sxs-lookup"><span data-stu-id="2cbc3-115">ProcessInput Method</span></span>  
 <span data-ttu-id="2cbc3-116"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> メソッドは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> オブジェクトによって上流コンポーネントにアタッチされる入力が少なくとも 1 つあるコンポーネントに対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-116">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> method is called for components that have at least one input attached to an upstream component by an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object.</span></span> <span data-ttu-id="2cbc3-117"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> メソッドは、同期出力型の変換先コンポーネントと変換に対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-117">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> method is called for destination components and for transformations with synchronous outputs.</span></span> <span data-ttu-id="2cbc3-118"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> は、処理する行が上流コンポーネントから渡されなくなるまで繰り返し呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-118"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> is called repeatedly until there are no more rows to process from upstream components.</span></span>  
  
## <a name="working-with-inputs-and-outputs"></a><span data-ttu-id="2cbc3-119">入力と出力の処理</span><span class="sxs-lookup"><span data-stu-id="2cbc3-119">Working with Inputs and Outputs</span></span>  
 <span data-ttu-id="2cbc3-120">データ フロー コンポーネントは、実行時に次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-120">At run time, data flow components perform the following tasks:</span></span>  
  
-   <span data-ttu-id="2cbc3-121">変換コンポーネントは行を追加します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-121">Source components add rows.</span></span>  
  
-   <span data-ttu-id="2cbc3-122">同期出力型の変換コンポーネントは、変換元コンポーネントから渡される行を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-122">Transformation components with synchronous outputs receive rows provided by source components.</span></span>  
  
-   <span data-ttu-id="2cbc3-123">非同期出力型の変換コンポーネントは、行を受け取って行を追加します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-123">Transformation components with asynchronous outputs receive rows and add rows.</span></span>  
  
-   <span data-ttu-id="2cbc3-124">変換先コンポーネントは、行を受け取って変換先に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-124">Destination components receive rows and then load them into a destination.</span></span>  
  
 <span data-ttu-id="2cbc3-125">実行中、データ フロー タスクは、コンポーネントのシーケンスの出力列コレクションで定義されたすべての列を含む <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> オブジェクトを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-125">During execution, the data flow task allocates <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects that contain all the columns defined in the output column collections of a sequence of components.</span></span> <span data-ttu-id="2cbc3-126">たとえば、データ フロー シーケンス内の 4 つの各コンポーネントが 1 つの出力列をその出力列コレクションに追加した場合、各コンポーネントに提供されているバッファーには 4 つの列、つまりコンポーネントごとに 1 つの出力列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-126">For example, if each of four components in a data flow sequence adds one output column to its output column collection,the buffer that is provided to each component contains four columns, one for each output column per component.</span></span> <span data-ttu-id="2cbc3-127">この動作のため、使用しない列を含むバッファーをコンポーネントが受け取る場合があります。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-127">Because of this behavior, a component sometimes receives buffers that contain columns it does not use.</span></span>  
  
 <span data-ttu-id="2cbc3-128">コンポーネントが受け取るバッファーにはコンポーネントが使用しない列が含まれる場合もあるので、データ フロー タスクがコンポーネントに提供するバッファー内のコンポーネントの入力および出力列のコレクションから、使用する列を検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-128">Since the buffers received by your component may contain columns that the component will not use, you must locate the columns that you want to use in your component's input and output column collections in the buffer provided to the component by the data flow task.</span></span> <span data-ttu-id="2cbc3-129">これを行うには、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> プロパティの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-129">You do this by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property.</span></span> <span data-ttu-id="2cbc3-130">パフォーマンスの理由により、このタスクは通常、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> や <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> ではなく、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドで実行します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-130">For performance reasons, this task is ordinarily performed during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, rather than in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
 <span data-ttu-id="2cbc3-131"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> は <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> および <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドの前に呼び出され、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> がコンポーネントで使用できるようになった後に初めてコンポーネントで作業を実行できます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-131"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods, and is the first opportunity for a component to perform this work after the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> becomes available to the component.</span></span> <span data-ttu-id="2cbc3-132">このメソッドの実行中、コンポーネントはバッファー内の列を検索してこの情報を内部的に格納し、列が <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> または <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドのどちらかで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-132">During this method, the component should locate its columns in the buffers and store this information internally so the columns can be used in either the  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span>  
  
 <span data-ttu-id="2cbc3-133">次のコード例では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> で、同期出力型の変換コンポーネントがバッファー内の入力列を検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-133">The following code example demonstrates how a transformation component with a synchronous output locates its input columns in the buffer during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>.</span></span>  
  
```csharp  
private int []bufferColumnIndex;  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    bufferColumnIndex = new int[input.InputColumnCollection.Count];  
  
    for( int x=0; x < input.InputColumnCollection.Count; x++)  
    {  
        IDTSInputColumn100 column = input.InputColumnCollection[x];  
        bufferColumnIndex[x] = BufferManager.FindColumnByLineageID( input.Buffer, column.LineageID);  
    }  
}  
```  
  
```vb  
Dim bufferColumnIndex As Integer()  
  
    Public Overrides Sub PreExecute()  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
  
        ReDim bufferColumnIndex(input.InputColumnCollection.Count)  
  
        For x As Integer = 0 To input.InputColumnCollection.Count  
  
            Dim column As IDTSInputColumn100 = input.InputColumnCollection(x)  
            bufferColumnIndex(x) = BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID)  
  
        Next  
  
    End Sub  
```  
  
### <a name="adding-rows"></a><span data-ttu-id="2cbc3-134">行の追加</span><span class="sxs-lookup"><span data-stu-id="2cbc3-134">Adding Rows</span></span>  
 <span data-ttu-id="2cbc3-135">コンポーネントは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> オブジェクトに行を追加することで、下流コンポーネントに行を提供します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-135">Components supply rows to downstream components by adding rows to <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects.</span></span> <span data-ttu-id="2cbc3-136">データ フロー タスクは、下流コンポーネントに接続される <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> オブジェクトごとに 1 つずつ、出力バッファーの配列を <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドに渡すパラメーターとして提供します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-136">The data flow task provides an array of output buffers - one for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object that is connected to a downstream component - as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="2cbc3-137">非同期出力型の変換元コンポーネントと変換コンポーネントは、行をバッファーに追加し、行の追加が完了したら <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-137">Source components and transformation components with asynchronous outputs add rows to the buffers and call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method when they are finished adding rows.</span></span> <span data-ttu-id="2cbc3-138">データ フロー タスクは、コンポーネントに提供する出力バッファーを管理し、バッファーがいっぱいになると、バッファー内の行を自動的に次のコンポーネントに移動します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-138">The data flow task manages the output buffers that it supplies to components and, as a buffer becomes full, automatically moves the rows in the buffer to the next component.</span></span> <span data-ttu-id="2cbc3-139"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドは、繰り返し呼び出される <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドと異なり、コンポーネントごとに 1 回ずつ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-139">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method is called one time per component, unlike  the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, which is called repeatedly.</span></span>  
  
 <span data-ttu-id="2cbc3-140">次のコード例では、コンポーネントが <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドで出力バッファーに行を追加し、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> メソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-140">The following code example demonstrates how a component adds rows to its output buffers during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method, then calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method.</span></span>  
  
```csharp  
public override void PrimeOutput( int outputs, int []outputIDs,PipelineBuffer []buffers)  
{  
    for( int x=0; x < outputs; x++ )  
    {  
        IDTSOutput100 output = ComponentMetaData.OutputCollection.GetObjectByID( outputIDs[x]);  
        PipelineBuffer buffer = buffers[x];  
  
        // TODO: Add rows to the output buffer.  
    }  
    foreach( PipelineBuffer buffer in buffers )  
    {  
        /// Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset();  
    }  
}  
```  
  
```vb  
public overrides sub PrimeOutput( outputs as Integer , outputIDs() as Integer ,buffers() as PipelineBuffer buffers)  
  
    For x As Integer = 0 To outputs.MaxValue  
  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.GetObjectByID(outputIDs(x))  
        Dim buffer As PipelineBuffer = buffers(x)  
  
        ' TODO: Add rows to the output buffer.  
  
    Next  
  
    For Each buffer As PipelineBuffer In buffers  
  
        ' Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset()  
  
    Next  
  
End Sub  
```  
  
 <span data-ttu-id="2cbc3-141">出力バッファーに行を追加するコンポーネントの開発の詳細については、「[カスタム変換元コンポーネントの開発](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)」および「[非同期出力型のカスタム変換コンポーネントの開発](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-141">For more information about developing components that add rows to output buffers, see [Developing a Custom Source Component](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) and [Developing a Custom Transformation Component with Asynchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).</span></span>  
  
### <a name="receiving-rows"></a><span data-ttu-id="2cbc3-142">行の受信</span><span class="sxs-lookup"><span data-stu-id="2cbc3-142">Receiving Rows</span></span>  
 <span data-ttu-id="2cbc3-143">コンポーネントは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> オブジェクト内の上流コンポーネントから行を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-143">Components receive rows from upstream components in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects.</span></span> <span data-ttu-id="2cbc3-144">データ フロー タスクでは、上流コンポーネントがデータ フローに追加する行が含まれる <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> オブジェクトが、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドに渡されるパラメーターとして用意されています。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-144">The data flow task provides a <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> object that contains the rows added to the data flow by upstream components as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span> <span data-ttu-id="2cbc3-145">この入力バッファーを使用して、バッファー内の行および列を検証して変更することはできますが、行を追加したり削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-145">This input buffer can be used to examine and modify the rows and columns in the buffer, but cannot be used to add or remove rows.</span></span> <span data-ttu-id="2cbc3-146"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドは、渡されるバッファーがなくなるまで繰り返し呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-146">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method is called repeatedly until there are no more available buffers.</span></span> <span data-ttu-id="2cbc3-147">このメソッドが最後に呼び出されたとき、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティは `true` になります。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-147">The last time it is called, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property is `true`.</span></span> <span data-ttu-id="2cbc3-148">バッファーを次の行に進める <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> メソッドを使用することにより、バッファー内の行のコレクションを反復処理できます。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-148">You can iterate over the collection of rows in the buffer by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> method, which advances the buffer to the next row.</span></span> <span data-ttu-id="2cbc3-149">バッファーがコレクション内の最後の行にある場合、このメソッドは `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-149">This method returns `false` when the buffer is on the last row in the collection.</span></span> <span data-ttu-id="2cbc3-150">データの最後の行が処理された後にさらに操作を実行する必要がある場合を除き、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティを確認する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-150">You do not have to check the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property unless you have to perform an additional action after the last rows of data have been processed.</span></span>  
  
 <span data-ttu-id="2cbc3-151">次のテキストは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> メソッドと <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティを使用する正しいパターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-151">The following text shows the correct pattern for using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> method and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property:</span></span>  
  
 `while (buffer.NextRow())`  
  
 `{`  
  
 `// Do something with each row.`  
  
 `}`  
  
 `if (buffer.EndOfRowset)`  
  
 `{`  
  
 `// Optionally, do something after all rows have been processed.`  
  
 `}`  
  
 <span data-ttu-id="2cbc3-152">次のコード例では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドの実行中に、コンポーネントが入力バッファー内の行を処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-152">The following code example demonstrates how a component processes the rows in input buffers during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span>  
  
```csharp  
public override void ProcessInput( int inputID, PipelineBuffer buffer )  
{  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);  
        while( buffer.NextRow())  
        {  
            // TODO: Examine the columns in the current row.  
        }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)  
        While buffer.NextRow() = True  
  
            ' TODO: Examine the columns in the current row.  
        End While  
  
End Sub  
```  
  
 <span data-ttu-id="2cbc3-153">入力バッファー内の行を受け取るコンポーネントの開発の詳細については、「[カスタム変換先コンポーネントの開発](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)」および「[同期出力型のカスタム変換コンポーネントの開発](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-153">For more information about developing components that receive rows in input buffers, see [Developing a Custom Destination Component](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) and [Developing a Custom Transformation Component with Synchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>  
  
<span data-ttu-id="2cbc3-154">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="2cbc3-154">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2cbc3-155">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-155">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2cbc3-156">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="2cbc3-156">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2cbc3-157">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="2cbc3-157">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbc3-158">参照</span><span class="sxs-lookup"><span data-stu-id="2cbc3-158">See Also</span></span>  
 [<span data-ttu-id="2cbc3-159">データ フロー コンポーネントのデザイン時のメソッド</span><span class="sxs-lookup"><span data-stu-id="2cbc3-159">Design-time Methods of a Data Flow Component</span></span>](design-time-methods-of-a-data-flow-component.md)  
  
  
