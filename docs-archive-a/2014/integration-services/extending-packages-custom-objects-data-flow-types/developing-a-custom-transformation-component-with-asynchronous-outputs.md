---
title: 非同期出力型のカスタム変換コンポーネントの開発 | Microsoft Docs
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
- custom data flow components [Integration Services], transformation components
- asynchronous outputs [Integration Services]
- ProcessInput method
- cache [Integration Services]
- buffer allocations [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], transformation components
ms.assetid: 1c3e92c7-a4fa-4fdd-b9ca-ac3069536274
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41e2ecdf9f90765e75ff2b8c9c0681a25366e080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736612"
---
# <a name="developing-a-custom-transformation-component-with-asynchronous-outputs"></a><span data-ttu-id="5b920-102">非同期出力型のカスタム変換コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="5b920-102">Developing a Custom Transformation Component with Asynchronous Outputs</span></span>
  <span data-ttu-id="5b920-103">非同期出力型変換コンポーネントは、変換が入力行をすべて受け取るまで行を出力できないようにする場合や、変換が入力として受信した各行に対して必ずしも 1 つずつ出力行を生成しない場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="5b920-103">You use a component with asynchronous outputs when a transform cannot output rows until the component has received all its input rows, or when the transformation does not produce exactly one output row for each row received as input.</span></span> <span data-ttu-id="5b920-104">たとえば、集計変換では、行をすべて読み込むまではすべての行の合計を計算できません。</span><span class="sxs-lookup"><span data-stu-id="5b920-104">The Aggregate transformation, for example, cannot calculate a sum across rows until it has read all the rows.</span></span> <span data-ttu-id="5b920-105">これに対し、同期出力型コンポーネントは、データが渡されるたびに各データ行を変更する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="5b920-105">In contrast, you can use a component with synchronous outputs any time when you modify each row of data as it passes through.</span></span> <span data-ttu-id="5b920-106">各行のデータを順に変更したり、1 つまたは複数の列を新規作成して、各列にすべての入力行ごとの値を設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="5b920-106">You can modify the data for each row in place, or you can create one or more new columns, each of which has a value for every one of the input rows.</span></span> <span data-ttu-id="5b920-107">同期コンポーネントと非同期コンポーネントの相違点の詳細については、「[同期変換と非同期変換について](../understanding-synchronous-and-asynchronous-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b920-107">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="5b920-108">非同期出力型変換コンポーネントは、変換先コンポーネントと変換元コンポーネントの、両方の機能を果たすという特徴があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-108">Transformation components with asynchronous outputs are unique because they act as both destination and source components.</span></span> <span data-ttu-id="5b920-109">この種のコンポーネントは、上流コンポーネントから行を受け取り、下流コンポーネントで使用される行を追加します。</span><span class="sxs-lookup"><span data-stu-id="5b920-109">This kind of component receives rows from upstream components, and adds rows that are consumed by downstream components.</span></span> <span data-ttu-id="5b920-110">これらの操作を両方とも行うデータ フロー コンポーネントは、他にはありません。</span><span class="sxs-lookup"><span data-stu-id="5b920-110">No other data flow component performs both of these operations.</span></span>

 <span data-ttu-id="5b920-111">上流コンポーネントの列が同期出力型コンポーネントで使用可能な場合、自動的に、その下流にあるコンポーネントでも使用可能となります。</span><span class="sxs-lookup"><span data-stu-id="5b920-111">The columns from upstream components that are available to a component with synchronous outputs are automatically available to components downstream from the component.</span></span> <span data-ttu-id="5b920-112">したがって、同期出力型コンポーネントでは、出力列を定義しなくても次のコンポーネントに行や列を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5b920-112">Therefore, a component with synchronous outputs does not have to define any output columns to provide columns and rows to the next component.</span></span> <span data-ttu-id="5b920-113">これに対し、非同期出力型コンポーネントでは、下流コンポーネントに行を渡すために出力列を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-113">Components with asynchronous outputs, on the other hand, must define output columns and provide rows to downstream components.</span></span> <span data-ttu-id="5b920-114">したがって、非同期出力型コンポーネントの方が、デザイン時や実行時に必要な処理が多いため、開発者はより多くのコードを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-114">Therefore a component with asynchronous outputs has more tasks to perform during both design and execution time, and the component developer has more code to implement.</span></span>

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5b920-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には非同期出力型の変換がいくつか組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="5b920-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contains several transformations with asynchronous outputs.</span></span> <span data-ttu-id="5b920-116">たとえば並べ替え変換では、並べ替えを行う前に行がすべて必要であるため、非同期出力を使用して変換を実行しています。</span><span class="sxs-lookup"><span data-stu-id="5b920-116">For example, the Sort transformation requires all its rows before it can sort them, and achieves this by using asynchronous outputs.</span></span> <span data-ttu-id="5b920-117">行をすべて受け取ったら並べ替えを実行し、出力に行を追加します。</span><span class="sxs-lookup"><span data-stu-id="5b920-117">After it has received all its rows, it sorts them and adds them to its output.</span></span>

 <span data-ttu-id="5b920-118">ここでは、非同期出力型の変換を開発する方法の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b920-118">This section explains in detail how to develop transformations with asynchronous outputs.</span></span> <span data-ttu-id="5b920-119">変換元コンポーネントの開発の詳細については、「[カスタム変換元コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b920-119">For more information about source component development, see [Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).</span></span>

## <a name="design-time"></a><span data-ttu-id="5b920-120">デザイン時</span><span class="sxs-lookup"><span data-stu-id="5b920-120">Design Time</span></span>

### <a name="creating-the-component"></a><span data-ttu-id="5b920-121">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="5b920-121">Creating the Component</span></span>
 <span data-ttu-id="5b920-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> オブジェクトの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> プロパティは、同期出力か非同期出力かの区別を示します。</span><span class="sxs-lookup"><span data-stu-id="5b920-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property on the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object identifies whether an output is synchronous or asynchronous.</span></span> <span data-ttu-id="5b920-123">非同期出力を作成するには、コンポーネントに出力を追加し、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> プロパティを 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="5b920-123">To create an asynchronous output, add the output to the component and set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> to zero.</span></span> <span data-ttu-id="5b920-124">また、このプロパティを設定することにより、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> オブジェクトをコンポーネントの入出力の両方に割り当てるか、単一のバッファーを割り当てて 2 つのオブジェクトで共有するかをデータ フロー タスクが判断します。</span><span class="sxs-lookup"><span data-stu-id="5b920-124">Setting this property also determines whether the data flow task allocates <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects for both the input and output of the component, or whether a single buffer is allocated and shared between the two objects.</span></span>

 <span data-ttu-id="5b920-125">次のサンプル コードは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> を実装し、非同期出力を作成するコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="5b920-125">The following sample code shows a component that creates an asynchronous output in its <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> implementation.</span></span>

```csharp
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    [DtsPipelineComponent(DisplayName = "AsyncComponent",ComponentType = ComponentType.Transform)]
    public class AsyncComponent : PipelineComponent
    {
        public override void ProvideComponentProperties()
        {
            // Call the base class, which adds a synchronous input
            // and output.
            base.ProvideComponentProperties();

            // Make the output asynchronous.
            IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
            output.SynchronousInputID = 0;
        }
    }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime

<DtsPipelineComponent(DisplayName:="AsyncComponent", ComponentType:=ComponentType.Transform)> _
Public Class AsyncComponent
    Inherits PipelineComponent

    Public Overrides Sub ProvideComponentProperties()

        ' Call the base class, which adds a synchronous input
        ' and output.
        Me.ProvideComponentProperties()

        ' Make the output asynchronous.
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
        output.SynchronousInputID = 0

    End Sub

End Class
```

### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="5b920-126">出力列の作成と設定</span><span class="sxs-lookup"><span data-stu-id="5b920-126">Creating and Configuring Output Columns</span></span>
 <span data-ttu-id="5b920-127">前述したように、非同期型コンポーネントは出力列コレクションに列を追加し、下流コンポーネントに列を渡します。</span><span class="sxs-lookup"><span data-stu-id="5b920-127">As mentioned earlier, an asynchronous component adds columns to its output column collection to provide columns to downstream components.</span></span> <span data-ttu-id="5b920-128">コンポーネントの要件に応じて、デザイン時に選択できる方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="5b920-128">There are several design-time methods to choose from, depending on the needs of the component.</span></span> <span data-ttu-id="5b920-129">たとえば、上流コンポーネントからすべての列をそのまま下流コンポーネントに渡す場合は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.OnInputPathAttached%2A> メソッドをオーバーライドして列を追加します。これが、コンポーネントで入力列が使用可能となる最初のメソッドだからです。</span><span class="sxs-lookup"><span data-stu-id="5b920-129">For example, if you want to pass all the columns from the upstream components to the downstream components, you would override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.OnInputPathAttached%2A> method to add the columns, because this is the first method in which the input columns are available to the component.</span></span>

 <span data-ttu-id="5b920-130">入力列として選択した列に基づいてコンポーネントが出力列を作成する場合は、出力列を選択してそれらの使い方を示すように、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetUsageType%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5b920-130">If the component creates output columns based on the columns selected for its input, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetUsageType%2A> method to select the output columns and to indicate how they will be used.</span></span>

 <span data-ttu-id="5b920-131">非同期型出力型コンポーネントで、上流コンポーネントの列に基づいて出力列を作成する場合、使用できる上流の列が変更されると、コンポーネントは出力列のコレクションを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-131">If a component with asynchronous outputs creates output columns based on the columns from upstream components, and the available upstream columns change, the component should update its output column collection.</span></span> <span data-ttu-id="5b920-132">変更は <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> メソッド内で検出され、更新は <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> メソッド内で行われます。</span><span class="sxs-lookup"><span data-stu-id="5b920-132">These changes should be detected by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>, and fixed during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>.</span></span>

> [!NOTE]
>  <span data-ttu-id="5b920-133">出力列コレクションからある出力列を削除すると、データ フローの下流に位置し、この列を参照しているコンポーネントに悪影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="5b920-133">When an output column is removed from the output column collection, downstream components in the data flow that reference the column are adversely affected.</span></span> <span data-ttu-id="5b920-134">下流コンポーネントが悪影響を受けないようにするには、列を削除して再作成する方法を取らずに、出力列を修復する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-134">The output column must be repaired without removing and recreating the column to prevent breaking the downstream components.</span></span> <span data-ttu-id="5b920-135">たとえば、ある列のデータ型を変更した場合、データ型を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-135">For example, if the data type of the column has changed, you must update the data type.</span></span>

 <span data-ttu-id="5b920-136">次のコード例では、上流コンポーネントから渡される各列に対して出力列を作成し、出力列コレクションに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5b920-136">The following code example shows a component that adds an output column to its output column collection for each column available from the upstream component.</span></span>

```csharp
public override void OnInputPathAttached(int inputID)
{
   IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);
   IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
   IDTSVirtualInput100 vInput = input.GetVirtualInput();

   foreach (IDTSVirtualInputColumn100 vCol in vInput.VirtualInputColumnCollection)
   {
      IDTSOutputColumn100 outCol = output.OutputColumnCollection.New();
      outCol.Name = vCol.Name;
      outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage);
   }
}
```

```vb
Public Overrides Sub OnInputPathAttached(ByVal inputID As Integer)

    Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
    Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput()

    For Each vCol As IDTSVirtualInputColumn100 In vInput.VirtualInputColumnCollection

        Dim outCol As IDTSOutputColumn100 = output.OutputColumnCollection.New()
        outCol.Name = vCol.Name
        outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage)

    Next
End Sub
```

## <a name="run-time"></a><span data-ttu-id="5b920-137">実行時間</span><span class="sxs-lookup"><span data-stu-id="5b920-137">Run Time</span></span>
 <span data-ttu-id="5b920-138">非同期出力型コンポーネントは、他の種類のコンポーネントとは実行時における処理手順も異なります。</span><span class="sxs-lookup"><span data-stu-id="5b920-138">Components with asynchronous outputs also execute a different sequence of methods at run time than other types of components.</span></span> <span data-ttu-id="5b920-139">まず、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> と <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> の両方のメソッドに対する呼び出しを受信するのは、この型のコンポーネントのみです。</span><span class="sxs-lookup"><span data-stu-id="5b920-139">First, they are the only components that receive a call to both the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span> <span data-ttu-id="5b920-140">また、非同期出力型コンポーネントは、処理を開始する前に入力行すべてにアクセスできるようになっている必要があります。そのため、すべての行が読み取られるまで、入力行を内部キャッシュに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-140">Components with asynchronous outputs also require access to all the incoming rows before they can start processing; therefore, they must cache the input rows internally until all rows have been read.</span></span> <span data-ttu-id="5b920-141">最後に、他のコンポーネントとは異なり、非同期出力型コンポーネントは入力用と出力用の両方のバッファーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5b920-141">Finally, unlike other components, components with asynchronous outputs receive both an input buffer and an output buffer.</span></span>

### <a name="understanding-the-buffers"></a><span data-ttu-id="5b920-142">バッファーについて</span><span class="sxs-lookup"><span data-stu-id="5b920-142">Understanding the Buffers</span></span>
 <span data-ttu-id="5b920-143">コンポーネントが入力バッファーを受け取るのは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドの実行中です。</span><span class="sxs-lookup"><span data-stu-id="5b920-143">The input buffer is received by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span> <span data-ttu-id="5b920-144">このバッファーには、上流コンポーネントによってバッファーに追加された行が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5b920-144">This buffer contains the rows added to the buffer by upstream components.</span></span> <span data-ttu-id="5b920-145">また、このバッファーには、上流コンポーネントの出力に存在しながら、非同期型コンポーネントの入力コレクションに含まれていない列を含め、コンポーネントの入力の列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5b920-145">The buffer also contains the columns of the component's input, in addition to the columns that were provided in the output of an upstream component but were not added to the asynchronous component's input collection.</span></span>

 <span data-ttu-id="5b920-146"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドからコンポーネントに提供される出力バッファーには、最初は行が格納されていません。</span><span class="sxs-lookup"><span data-stu-id="5b920-146">The output buffer, which is provided to the component in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, does not initially contain rows.</span></span> <span data-ttu-id="5b920-147">コンポーネントは行をこのバッファーに追加し、バッファーがいっぱいになった時点で下流コンポーネントに渡します。</span><span class="sxs-lookup"><span data-stu-id="5b920-147">The component adds rows to this buffer and provides the buffer to downstream components when it is full.</span></span> <span data-ttu-id="5b920-148">出力バッファーには、他の下流コンポーネントが出力に追加したすべての列を含め、出力列コレクションで定義されている列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5b920-148">The output buffer contains the columns defined in the component's output column collection, in addition to any columns that other downstream components have added to their outputs.</span></span>

 <span data-ttu-id="5b920-149">この動作は、単一のバッファーを共有する同期出力型コンポーネントの動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="5b920-149">This is different behavior from that of components with synchronous outputs, which receive a single shared buffer.</span></span> <span data-ttu-id="5b920-150">同期出力型コンポーネントの共有バッファーには、上流コンポーネントと下流コンポーネントの出力に追加された列を含め、コンポーネントの入力列および出力列の両方が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5b920-150">The shared buffer of a component with synchronous outputs contains both the input and output columns of the component, in addition to columns added to the outputs of upstream and downstream components.</span></span>

### <a name="processing-rows"></a><span data-ttu-id="5b920-151">行の処理</span><span class="sxs-lookup"><span data-stu-id="5b920-151">Processing Rows</span></span>

#### <a name="caching-input-rows"></a><span data-ttu-id="5b920-152">入力行のキャッシュ</span><span class="sxs-lookup"><span data-stu-id="5b920-152">Caching Input Rows</span></span>
 <span data-ttu-id="5b920-153">非同期出力型コンポーネントを記述する場合、出力バッファーに行を追加するには 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-153">When you write a component with asynchronous outputs, you have three options for adding rows to the output buffer.</span></span> <span data-ttu-id="5b920-154">それは、入力行を受け取るたびに追加する方法、上流コンポーネントから行をすべて受け取るまでキャッシュする方法、またはコンポーネントを処理するうえで適切な時点で追加する方法です。</span><span class="sxs-lookup"><span data-stu-id="5b920-154">You can add them as input rows are received, you can cache them until the component has received all the rows from the upstream component, or you can add them when it is appropriate to do so for the component.</span></span> <span data-ttu-id="5b920-155">方法は、コンポーネントの要求に応じて選択します。</span><span class="sxs-lookup"><span data-stu-id="5b920-155">The method that you choose depends on the requirements of the component.</span></span> <span data-ttu-id="5b920-156">たとえば並べ替えコンポーネントの場合、上流から行をすべて受け取ってからでないと並べ替え処理はできません。</span><span class="sxs-lookup"><span data-stu-id="5b920-156">For example, the Sort component requires that all the upstream rows be received before they can be sorted.</span></span> <span data-ttu-id="5b920-157">したがって、すべての行が読み取られるまで待機してから、出力バッファーに行を追加します。</span><span class="sxs-lookup"><span data-stu-id="5b920-157">Therefore, it waits until all rows have been read before adding rows to the output buffer.</span></span>

 <span data-ttu-id="5b920-158">入力バッファーで受け取った行は、処理の準備ができるまで、コンポーネントの内部にキャッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-158">The rows that are received in the input buffer must be cached internally by the component until it is ready to process them.</span></span> <span data-ttu-id="5b920-159">入力バッファー内の行は、データ テーブルや多次元配列のほか、コンポーネントの内部構造の任意の場所にキャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="5b920-159">The incoming buffer rows can be cached in a data table, a multidimensional array, or any other internal structure.</span></span>

#### <a name="adding-output-rows"></a><span data-ttu-id="5b920-160">出力行の追加</span><span class="sxs-lookup"><span data-stu-id="5b920-160">Adding Output Rows</span></span>
 <span data-ttu-id="5b920-161">出力バッファーへの行の追加は、出力バッファーで <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> メソッドを呼び出すことによって行います。これは、行を受け取るたびに出力バッファーに追加する場合でも、すべての行を受け取ってから追加する場合でも同じです。</span><span class="sxs-lookup"><span data-stu-id="5b920-161">Whether you add rows to the output buffer as they are received or after receiving all of the rows, you do so by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> method on the output buffer.</span></span> <span data-ttu-id="5b920-162">行を追加したら、新しい行の各列に値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5b920-162">After you have added the row, you set the values of each column in the new row.</span></span>

 <span data-ttu-id="5b920-163">出力バッファーには、コンポーネントの出力列コレクションにはない列が含まれる場合があるため、値を設定するには、バッファーの該当する列のインデックスを探す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b920-163">Because there are sometimes more columns in the output buffer than in the output column collection of the component, you must locate the index of the appropriate column in the buffer before you can set its value.</span></span> <span data-ttu-id="5b920-164"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> プロパティの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> メソッドは、バッファー行のうち、指定された系列 ID を持つ列のインデックスを返します。これを使用して、バッファー列に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5b920-164">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property returns the index of the column in the buffer row with the specified lineage ID, which is then used to assign the value to the buffer column.</span></span>

 <span data-ttu-id="5b920-165"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> メソッドは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドまたは <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドの前に呼び出されますが、ここで初めて <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> プロパティが使用可能になり、初めて入力バッファーおよび出力バッファーの各列のインデックスを探すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="5b920-165">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, which is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method or the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, is the first method where the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property is available, and the first opportunity to locate the indexes of the columns in the input and output buffers.</span></span>

## <a name="sample"></a><span data-ttu-id="5b920-166">サンプル</span><span class="sxs-lookup"><span data-stu-id="5b920-166">Sample</span></span>
 <span data-ttu-id="5b920-167">次の例は、行を受け取るたびに出力バッファーに行を追加する、非同期出力型の簡単な変換コンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="5b920-167">The following sample shows a simple transformation component with asynchronous outputs that adds rows to the output buffer as they are received.</span></span> <span data-ttu-id="5b920-168">ただし、この例ではここで説明したメソッドや機能のすべてが使われているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="5b920-168">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="5b920-169">カスタムの非同期出力型変換コンポーネントでオーバーライドしなければならない重要なメソッドは示していますが、デザイン時の検証のためのコードは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="5b920-169">It demonstrates the important methods that every custom transformation component with asynchronous outputs must override, but does not contain code for design-time validation.</span></span> <span data-ttu-id="5b920-170">また、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッド内のコードは、入力列コレクションの各列に対応して、出力列コレクションに 1 つずつ出力列があるものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="5b920-170">Also, the code in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> assumes that the output column collection has one column for each column in the input column collection.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
   [DtsPipelineComponent(DisplayName = "AsynchronousOutput")]
   public class AsynchronousOutput : PipelineComponent
   {
      PipelineBuffer outputBuffer;
      int[] inputColumnBufferIndexes;
      int[] outputColumnBufferIndexes;

      public override void ProvideComponentProperties()
      {
         // Let the base class add the input and output objects.
         base.ProvideComponentProperties();

         // Name the input and output, and make the
         // output asynchronous.
         ComponentMetaData.InputCollection[0].Name = "Input";
         ComponentMetaData.OutputCollection[0].Name = "AsyncOutput";
         ComponentMetaData.OutputCollection[0].SynchronousInputID = 0;
      }
      public override void PreExecute()
      {
         IDTSInput100 input = ComponentMetaData.InputCollection[0];
         IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

         inputColumnBufferIndexes = new int[input.InputColumnCollection.Count];
         outputColumnBufferIndexes = new int[output.OutputColumnCollection.Count];

         for (int col = 0; col < input.InputColumnCollection.Count; col++)
            inputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection[col].LineageID);

         for (int col = 0; col < output.OutputColumnCollection.Count; col++)
            outputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[col].LineageID);

      }

      public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
      {
         if (buffers.Length != 0)
            outputBuffer = buffers[0];
      }
      public override void ProcessInput(int inputID, PipelineBuffer buffer)
      {
            // Advance the buffer to the next row.
            while (buffer.NextRow())
            {
               // Add a row to the output buffer.
               outputBuffer.AddRow();
               for (int x = 0; x < inputColumnBufferIndexes.Length; x++)
               {
                  // Copy the data from the input buffer column to the output buffer column.
                  outputBuffer[outputColumnBufferIndexes[x]] = buffer[inputColumnBufferIndexes[x]];
               }
            }
         if (buffer.EndOfRowset)
         {
            // EndOfRowset on the input buffer is true.
            // Set EndOfRowset on the output buffer.
            outputBuffer.SetEndOfRowset();
         }
      }
   }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

Namespace Microsoft.Samples.SqlServer.Dts

    <DtsPipelineComponent(DisplayName:="AsynchronousOutput")> _
    Public Class AsynchronousOutput

        Inherits PipelineComponent

        Private outputBuffer As PipelineBuffer
        Private inputColumnBufferIndexes As Integer()
        Private outputColumnBufferIndexes As Integer()

        Public Overrides Sub ProvideComponentProperties()

            ' Let the base class add the input and output objects.
            Me.ProvideComponentProperties()

            ' Name the input and output, and make the
            ' output asynchronous.
            ComponentMetaData.InputCollection(0).Name = "Input"
            ComponentMetaData.OutputCollection(0).Name = "AsyncOutput"
            ComponentMetaData.OutputCollection(0).SynchronousInputID = 0
        End Sub

        Public Overrides Sub PreExecute()

            Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)
            Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

            ReDim inputColumnBufferIndexes(input.InputColumnCollection.Count)
            ReDim outputColumnBufferIndexes(output.OutputColumnCollection.Count)

            For col As Integer = 0 To input.InputColumnCollection.Count
                inputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection(col).LineageID)
            Next

            For col As Integer = 0 To output.OutputColumnCollection.Count
                outputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(col).LineageID)
            Next

        End Sub
        Public Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())

            If buffers.Length <> 0 Then
                outputBuffer = buffers(0)
            End If

        End Sub

        Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)

                ' Advance the buffer to the next row.
                While (buffer.NextRow())

                    ' Add a row to the output buffer.
                    outputBuffer.AddRow()
                    For x As Integer = 0 To inputColumnBufferIndexes.Length

                        ' Copy the data from the input buffer column to the output buffer column.
                        outputBuffer(outputColumnBufferIndexes(x)) = buffer(inputColumnBufferIndexes(x))

                    Next
                End While

            If buffer.EndOfRowset = True Then
                ' EndOfRowset on the input buffer is true.
                ' Set the end of row set on the output buffer.
                outputBuffer.SetEndOfRowset()
            End If
        End Sub
    End Class
End Namespace
```

<span data-ttu-id="5b920-171">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="5b920-171">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5b920-172">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b920-172">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5b920-173">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="5b920-173">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5b920-174">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="5b920-174">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b920-175">参照</span><span class="sxs-lookup"><span data-stu-id="5b920-175">See Also</span></span>
 <span data-ttu-id="5b920-176">[同期出力型のカスタム変換コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)[同期変換と非同期変換につい](../understanding-synchronous-and-asynchronous-transformations.md)[てスクリプトコンポーネントによる非同期変換の作成](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)</span><span class="sxs-lookup"><span data-stu-id="5b920-176">[Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)</span></span>


