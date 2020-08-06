---
title: 同期出力型のカスタム変換コンポーネントの開発 | Microsoft Docs
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
- ProcessInput method
- buffer allocations [Integration Services]
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- data flow components [Integration Services], transformation components
ms.assetid: b694d21f-9919-402d-9192-666c6449b0b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 94d78872570103d3df7e1cb96aecb144fafe4257
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736613"
---
# <a name="developing-a-custom-transformation-component-with-synchronous-outputs"></a><span data-ttu-id="48f69-102">同期出力型のカスタム変換コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="48f69-102">Developing a Custom Transformation Component with Synchronous Outputs</span></span>
  <span data-ttu-id="48f69-103">同期出力型の変換コンポーネントは、上流コンポーネントから行を受け取り、これらの行の列の値を読み取ったり変更したりして、下流コンポーネントに渡します。</span><span class="sxs-lookup"><span data-stu-id="48f69-103">Transformation components with synchronous outputs receive rows from upstream components, and read or modify the values in the columns of these rows as they pass the rows to downstream components.</span></span> <span data-ttu-id="48f69-104">このコンポーネントは、上流コンポーネントから提供される列から派生する、別の出力列も定義しますが、データ フローに行を追加することはありません。</span><span class="sxs-lookup"><span data-stu-id="48f69-104">They may also define additional output columns that are derived from the columns provided by upstream components, but they do not add rows to the data flow.</span></span> <span data-ttu-id="48f69-105">同期コンポーネントと非同期コンポーネントの相違点の詳細については、「[同期変換と非同期変換について](../understanding-synchronous-and-asynchronous-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48f69-105">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>  
  
 <span data-ttu-id="48f69-106">この種類のコンポーネントは、データがコンポーネントに提供されたときにインラインで変更され、処理する前にコンポーネントがすべての行を確認する必要がないタスクに適しています。</span><span class="sxs-lookup"><span data-stu-id="48f69-106">This kind of component is suited for tasks where the data is modified inline as it is provided to the component and where the component does not have to see all the rows before processing them.</span></span> <span data-ttu-id="48f69-107">通常、同期出力型の変換では、外部データ ソースへの接続、外部メタデータ列の管理、および出力バッファーへの行の追加は行われないため、このコンポーネントを開発するのは最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="48f69-107">It is the easiest component to develop because transformations with synchronous outputs typically do not connect to external data sources, manage external metadata columns, or add rows to output buffers.</span></span>  
  
 <span data-ttu-id="48f69-108">同期出力型の変換コンポーネントを作成するには、コンポーネント用に選択された上流列を格納する <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> オブジェクトと、コンポーネントによって作成された派生列を格納する <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="48f69-108">Creating a transformation component with synchronous outputs involves adding an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> that will contain the upstream columns selected for the component, and a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object that may contain derived columns created by the component.</span></span> <span data-ttu-id="48f69-109">さらに、デザイン時のメソッドを実装し、実行中に受信バッファー行内の列を読み取ったり変更するコードを設定します。</span><span class="sxs-lookup"><span data-stu-id="48f69-109">It also includes implementing the design-time methods, and providing code that reads or modifies the columns in the incoming buffer rows during execution.</span></span>  
  
 <span data-ttu-id="48f69-110">このセクションでは、カスタム変換コンポーネントの実装に必要な情報、および概念の理解に役立つコード例を提供します。</span><span class="sxs-lookup"><span data-stu-id="48f69-110">This section provides the information that is required to implement a custom transformation component, and provides code examples to help you better understand the concepts.</span></span>  
  
## <a name="design-time"></a><span data-ttu-id="48f69-111">デザイン時</span><span class="sxs-lookup"><span data-stu-id="48f69-111">Design Time</span></span>  
 <span data-ttu-id="48f69-112">このコンポーネントのデザイン時のコードでは、入力と出力の作成、コンポーネントが生成するすべての出力の追加、および、コンポーネントの構成の検証を行います。</span><span class="sxs-lookup"><span data-stu-id="48f69-112">The design-time code for this component involves creating the inputs and outputs, adding any additional output columns that the component generates, and validating the configuration of the component.</span></span>  
  
### <a name="creating-the-component"></a><span data-ttu-id="48f69-113">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="48f69-113">Creating the Component</span></span>  
 <span data-ttu-id="48f69-114">コンポーネントの入力、出力、およびカスタム プロパティは、通常、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> メソッドの実行中に作成します。</span><span class="sxs-lookup"><span data-stu-id="48f69-114">The inputs, outputs, and custom properties of the component are typically created during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="48f69-115">同期出力型の変換コンポーネントの入力および出力を追加するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="48f69-115">There are two ways that you can add the input and the output of a transformation component with synchronous outputs.</span></span> <span data-ttu-id="48f69-116">メソッドの基本クラスの実装を使用して、作成された既定の入力および出力を変更する方法と、入力と出力を手動で明示的に追加する方法です。</span><span class="sxs-lookup"><span data-stu-id="48f69-116">You can use the base class implementation of the method and then modify the default input and output that it creates, or you can explicitly add the input and output yourself.</span></span>  
  
 <span data-ttu-id="48f69-117">次のコード例は、入力および出力オブジェクトを明示的に追加する <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> を実装します。</span><span class="sxs-lookup"><span data-stu-id="48f69-117">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> that explicitly adds the input and output objects.</span></span> <span data-ttu-id="48f69-118">同様の処理を行うために呼び出す基本クラスについては、コメントに記載されています。</span><span class="sxs-lookup"><span data-stu-id="48f69-118">The call to the base class that would accomplish the same thing is included in a comment.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SynchronousComponent", ComponentType = ComponentType.Transform)]  
    public class SyncComponent : PipelineComponent  
    {  
  
        public override void ProvideComponentProperties()  
        {  
            // Add the input.  
            IDTSInput100 input = ComponentMetaData.InputCollection.New();  
            input.Name = "Input";  
  
            // Add the output.  
            IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
            output.Name = "Output";  
            output.SynchronousInputID = input.ID;  
  
            // Alternatively, you can let the base class add the input and output  
            // and set the SynchronousInputID of the output to the ID of the input.  
            // base.ProvideComponentProperties();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsPipelineComponent(DisplayName:="SynchronousComponent", ComponentType:=ComponentType.Transform)> _  
Public Class SyncComponent  
    Inherits PipelineComponent  
  
    Public Overrides Sub ProvideComponentProperties()  
  
        ' Add the input.  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New()  
        input.Name = "Input"  
  
        ' Add the output.  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New()  
        output.Name = "Output"  
        output.SynchronousInputID = Input.ID  
  
        ' Alternatively, you can let the base class add the input and output  
        ' and set the SynchronousInputID of the output to the ID of the input.  
        ' base.ProvideComponentProperties();  
  
    End Sub  
  
End Class  
```  
  
### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="48f69-119">出力列の作成と設定</span><span class="sxs-lookup"><span data-stu-id="48f69-119">Creating and Configuring Output Columns</span></span>  
 <span data-ttu-id="48f69-120">同期出力型の変換コンポーネントでは、バッファーに行は追加されません。ただし、コンポーネントの出力に出力列を追加することはできます。</span><span class="sxs-lookup"><span data-stu-id="48f69-120">Although transformation components with synchronous outputs do not add rows to buffers, they may add extra output columns to their output.</span></span> <span data-ttu-id="48f69-121">通常、コンポーネントが出力列を追加すると、新しい出力列の値は、実行時に上流コンポーネントから渡される 1 つ以上の列に含まれるデータから取得されます。</span><span class="sxs-lookup"><span data-stu-id="48f69-121">Typically, when a component adds an output column, the values for the new output column are derived at run time from the data that is contained in one or more of the columns provided to the component by an upstream component.</span></span>  
  
 <span data-ttu-id="48f69-122">出力列が作成されたら、データ型のプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48f69-122">After an output column has been created, its data type properties must be set.</span></span> <span data-ttu-id="48f69-123">出力列のデータ型のプロパティを設定するには特別な処理が必要で、その処理は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> メソッドを呼び出して実行します。</span><span class="sxs-lookup"><span data-stu-id="48f69-123">Setting the data type properties of an output column requires special handling and is performed by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> method.</span></span> <span data-ttu-id="48f69-124">このメソッドが必要になるのは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> のプロパティがそれぞれ互いの設定に依存しているため、個別に読み取り専用であるからです。</span><span class="sxs-lookup"><span data-stu-id="48f69-124">This method is required because the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> properties are individually read-only, because each depends on the settings of the other.</span></span> <span data-ttu-id="48f69-125">このメソッドを使用すると、プロパティの値を確実に矛盾なく設定でき、データ フロー タスクにより、正しく設定されていることが検証されます。</span><span class="sxs-lookup"><span data-stu-id="48f69-125">This method guarantees that the values of the properties are set consistently, and the data flow task validates that they are set correctly.</span></span>  
  
 <span data-ttu-id="48f69-126">列の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> により、他のプロパティに設定される値が決定されます。</span><span class="sxs-lookup"><span data-stu-id="48f69-126">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> of the column determines the values that are set for the other properties.</span></span> <span data-ttu-id="48f69-127">次の表は、各 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> の依存するプロパティの要件を示しています。</span><span class="sxs-lookup"><span data-stu-id="48f69-127">The following table shows the requirements on the dependent properties for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>.</span></span> <span data-ttu-id="48f69-128">ここに示されていないデータ型の場合、依存するプロパティは 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="48f69-128">The data types not listed have their dependent properties set to zero.</span></span>  
  
|<span data-ttu-id="48f69-129">DataType</span><span class="sxs-lookup"><span data-stu-id="48f69-129">DataType</span></span>|<span data-ttu-id="48f69-130">長さ</span><span class="sxs-lookup"><span data-stu-id="48f69-130">Length</span></span>|<span data-ttu-id="48f69-131">スケール</span><span class="sxs-lookup"><span data-stu-id="48f69-131">Scale</span></span>|<span data-ttu-id="48f69-132">Precision</span><span class="sxs-lookup"><span data-stu-id="48f69-132">Precision</span></span>|<span data-ttu-id="48f69-133">CodePage</span><span class="sxs-lookup"><span data-stu-id="48f69-133">CodePage</span></span>|  
|--------------|------------|-----------|---------------|--------------|  
|<span data-ttu-id="48f69-134">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="48f69-134">DT_DECIMAL</span></span>|<span data-ttu-id="48f69-135">0</span><span class="sxs-lookup"><span data-stu-id="48f69-135">0</span></span>|<span data-ttu-id="48f69-136">0 より大きく 28 以下。</span><span class="sxs-lookup"><span data-stu-id="48f69-136">Greater than 0 and less than or equal to 28.</span></span>|<span data-ttu-id="48f69-137">0</span><span class="sxs-lookup"><span data-stu-id="48f69-137">0</span></span>|<span data-ttu-id="48f69-138">0</span><span class="sxs-lookup"><span data-stu-id="48f69-138">0</span></span>|  
|<span data-ttu-id="48f69-139">DT_CY</span><span class="sxs-lookup"><span data-stu-id="48f69-139">DT_CY</span></span>|<span data-ttu-id="48f69-140">0</span><span class="sxs-lookup"><span data-stu-id="48f69-140">0</span></span>|<span data-ttu-id="48f69-141">0</span><span class="sxs-lookup"><span data-stu-id="48f69-141">0</span></span>|<span data-ttu-id="48f69-142">0</span><span class="sxs-lookup"><span data-stu-id="48f69-142">0</span></span>|<span data-ttu-id="48f69-143">0</span><span class="sxs-lookup"><span data-stu-id="48f69-143">0</span></span>|  
|<span data-ttu-id="48f69-144">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="48f69-144">DT_NUMERIC</span></span>|<span data-ttu-id="48f69-145">0</span><span class="sxs-lookup"><span data-stu-id="48f69-145">0</span></span>|<span data-ttu-id="48f69-146">0 より大きく 28 以下で、有効桁数の値未満</span><span class="sxs-lookup"><span data-stu-id="48f69-146">Greater than 0 and less than or equal to 28, and less than Precision.</span></span>|<span data-ttu-id="48f69-147">1 以上 38 以下</span><span class="sxs-lookup"><span data-stu-id="48f69-147">Greater than or equal to 1 and less than or equal to 38.</span></span>|<span data-ttu-id="48f69-148">0</span><span class="sxs-lookup"><span data-stu-id="48f69-148">0</span></span>|  
|<span data-ttu-id="48f69-149">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="48f69-149">DT_BYTES</span></span>|<span data-ttu-id="48f69-150">0 より大きい</span><span class="sxs-lookup"><span data-stu-id="48f69-150">Greater than 0.</span></span>|<span data-ttu-id="48f69-151">0</span><span class="sxs-lookup"><span data-stu-id="48f69-151">0</span></span>|<span data-ttu-id="48f69-152">0</span><span class="sxs-lookup"><span data-stu-id="48f69-152">0</span></span>|<span data-ttu-id="48f69-153">0</span><span class="sxs-lookup"><span data-stu-id="48f69-153">0</span></span>|  
|<span data-ttu-id="48f69-154">DT_STR</span><span class="sxs-lookup"><span data-stu-id="48f69-154">DT_STR</span></span>|<span data-ttu-id="48f69-155">0 より大きく 8000 未満</span><span class="sxs-lookup"><span data-stu-id="48f69-155">Greater than 0 and less than 8000.</span></span>|<span data-ttu-id="48f69-156">0</span><span class="sxs-lookup"><span data-stu-id="48f69-156">0</span></span>|<span data-ttu-id="48f69-157">0</span><span class="sxs-lookup"><span data-stu-id="48f69-157">0</span></span>|<span data-ttu-id="48f69-158">0 以外の有効なコード ページ</span><span class="sxs-lookup"><span data-stu-id="48f69-158">Not 0, and a valid code page.</span></span>|  
|<span data-ttu-id="48f69-159">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="48f69-159">DT_WSTR</span></span>|<span data-ttu-id="48f69-160">0 より大きく 4000 未満</span><span class="sxs-lookup"><span data-stu-id="48f69-160">Greater than 0 and less than 4000.</span></span>|<span data-ttu-id="48f69-161">0</span><span class="sxs-lookup"><span data-stu-id="48f69-161">0</span></span>|<span data-ttu-id="48f69-162">0</span><span class="sxs-lookup"><span data-stu-id="48f69-162">0</span></span>|<span data-ttu-id="48f69-163">0</span><span class="sxs-lookup"><span data-stu-id="48f69-163">0</span></span>|  
  
 <span data-ttu-id="48f69-164">データ型プロパティの制約は出力列のデータ型に基づくため、マネージド型を処理する場合、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の正しいデータ型を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48f69-164">Because the restrictions on the data type properties are based on the data type of the output column, you must choose the correct [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type when you work with managed types.</span></span> <span data-ttu-id="48f69-165">基本クラスには、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>、および <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> の 3 つのヘルパー メソッドがあり、これを使用すると、マネージド コンポーネントの開発者は、マネージド型に対応する [!INCLUDE[ssIS](../../includes/ssis-md.md)] のデータ型を適切に選択できます。</span><span class="sxs-lookup"><span data-stu-id="48f69-165">The base class provides three helper methods, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> that assist managed component developers in selecting an [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type given a managed type.</span></span> <span data-ttu-id="48f69-166">これらのメソッドは、マネージド データ型と [!INCLUDE[ssIS](../../includes/ssis-md.md)] のデータ型を相互に変換します。</span><span class="sxs-lookup"><span data-stu-id="48f69-166">These methods convert managed data types to [!INCLUDE[ssIS](../../includes/ssis-md.md)] data types, and vice versa.</span></span>  
  
## <a name="run-time"></a><span data-ttu-id="48f69-167">実行時間</span><span class="sxs-lookup"><span data-stu-id="48f69-167">Run Time</span></span>  
 <span data-ttu-id="48f69-168">一般的に、コンポーネントのランタイム部分の実装は、コンポーネントの入力および出力列をバッファー内で検索するタスクと、受信バッファー行内にあるこれらの列の値を読み取りまたは書き込みするタスクの 2 つに分類されます。</span><span class="sxs-lookup"><span data-stu-id="48f69-168">Generally, the implementation of the run-time part of the component is categorized into two tasks-locating the input and output columns of the component in the buffer, and reading or writing the values of these columns in the incoming buffer rows.</span></span>  
  
### <a name="locating-columns-in-the-buffer"></a><span data-ttu-id="48f69-169">バッファー内の列の検索</span><span class="sxs-lookup"><span data-stu-id="48f69-169">Locating Columns in the Buffer</span></span>  
 <span data-ttu-id="48f69-170">実行中にコンポーネントに提供されるバッファー内の列数は、コンポーネントの入力または出力コレクション内の列数よりも大きい場合があります。</span><span class="sxs-lookup"><span data-stu-id="48f69-170">The number of columns in the buffers that are provided to a component during execution will likely exceed the number of columns in the input or output collections of the component.</span></span> <span data-ttu-id="48f69-171">各バッファーには、データ フローのコンポーネントで定義されているすべての出力列が含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="48f69-171">This is because each buffer contains all the output columns defined in the components in a data flow.</span></span> <span data-ttu-id="48f69-172">バッファーの列が入力または出力の列と正しく一致していることを確認するには、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48f69-172">To ensure that the buffer columns are correctly matched to the columns of the input or output, component developers must use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.</span></span> <span data-ttu-id="48f69-173">このメソッドは、特定のバッファー内の列を系列 ID によって検索します。</span><span class="sxs-lookup"><span data-stu-id="48f69-173">This method locates a column in the specified buffer by its lineage ID.</span></span> <span data-ttu-id="48f69-174">通常、列は <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> の実行中に検索されます。これは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> プロパティが使用できるようになる最初の実行時メソッドであるためです。</span><span class="sxs-lookup"><span data-stu-id="48f69-174">Typically columns are located during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> because this is the first run-time method where the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property becomes available.</span></span>  
  
 <span data-ttu-id="48f69-175">次のコード例は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> の実行中に、入力および出力列のコレクションで列のインデックスを検索するコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="48f69-175">The following code example shows a component that locates indexes of the columns in its input and output column collection during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>.</span></span> <span data-ttu-id="48f69-176">列インデックスは整数の配列に格納され、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> の実行中にコンポーネントからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="48f69-176">The column indexes are stored in an integer array, and can be accessed by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
```csharp  
int []inputColumns;  
int []outputColumns;  
  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
  
    inputColumns = new int[input.InputColumnCollection.Count];  
    outputColumns = new int[output.OutputColumnCollection.Count];  
  
    for(int col=0; col < input.InputColumnCollection.Count; col++)  
    {  
        IDTSInputColumn100 inputColumn = input.InputColumnCollection[col];  
        inputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID);  
    }  
  
    for(int col=0; col < output.OutputColumnCollection.Count; col++)  
    {  
        IDTSOutputColumn100 outputColumn = output.OutputColumnCollection[col];  
        outputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID);  
    }  
  
}  
```  
  
```vb  
Public Overrides Sub PreExecute()  
  
    Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
  
    ReDim inputColumns(input.InputColumnCollection.Count)  
    ReDim outputColumns(output.OutputColumnCollection.Count)  
  
    For col As Integer = 0 To input.InputColumnCollection.Count  
  
        Dim inputColumn As IDTSInputColumn100 = input.InputColumnCollection(col)  
        inputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID)  
    Next  
  
    For col As Integer = 0 To output.OutputColumnCollection.Count  
  
        Dim outputColumn As IDTSOutputColumn100 = output.OutputColumnCollection(col)  
        outputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID)  
    Next  
  
End Sub  
```  
  
### <a name="processing-rows"></a><span data-ttu-id="48f69-177">行の処理</span><span class="sxs-lookup"><span data-stu-id="48f69-177">Processing Rows</span></span>  
 <span data-ttu-id="48f69-178">コンポーネントは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> メソッドで、行および列を含む <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="48f69-178">Components receive <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects that contain rows and columns in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span> <span data-ttu-id="48f69-179">このメソッドではバッファー内の行が繰り返され、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> が読み取られて変更されている間に列が識別されます。</span><span class="sxs-lookup"><span data-stu-id="48f69-179">During this method the rows in the buffer are iterated, and the columns identified during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> are read and modified.</span></span> <span data-ttu-id="48f69-180">このメソッドは、上流コンポーネントから行が渡されなくなるまで、データ フロー タスクによって繰り返し呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="48f69-180">The method is called repeatedly by the data flow task until no more rows are provided from the upstream component.</span></span>  
  
 <span data-ttu-id="48f69-181">バッファー内の列は、配列のインデクサーにアクセスする方法を使用するか、`Get` または `Set` メソッドのいずれかを使用することにより、個別に読み取りまたは書き込みが行われます。</span><span class="sxs-lookup"><span data-stu-id="48f69-181">An individual column in the buffer is read or written by using the array indexer access method, or by using one of the `Get` or `Set` methods.</span></span> <span data-ttu-id="48f69-182">バッファー内の列のデータ型がわかっている場合には、`Get` および `Set` メソッドの方が効率的であり、こちらを使用するようお勧めします。</span><span class="sxs-lookup"><span data-stu-id="48f69-182">The `Get` and `Set` methods are more efficient and should be used when the data type of the column in the buffer is known.</span></span>  
  
 <span data-ttu-id="48f69-183">次のコード例では、受信行を処理する <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="48f69-183">The following code example shows an implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method that processes incoming rows.</span></span>  
  
```csharp  
public override void ProcessInput( int InputID, PipelineBuffer buffer)  
{  
       while( buffer.NextRow())  
       {  
            for(int x=0; x < inputColumns.Length;x++)  
            {  
                if(!buffer.IsNull(inputColumns[x]))  
                {  
                    object columnData = buffer[inputColumns[x]];  
                    // TODO: Modify the column data.  
                    buffer[inputColumns[x]] = columnData;  
                }  
            }  
  
      }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal InputID As Integer, ByVal buffer As PipelineBuffer)  
  
        While (buffer.NextRow())  
  
            For x As Integer = 0 To inputColumns.Length  
  
                if buffer.IsNull(inputColumns(x)) = false then  
  
                    Dim columnData As Object = buffer(inputColumns(x))  
                    ' TODO: Modify the column data.  
                    buffer(inputColumns(x)) = columnData  
  
                End If  
            Next  
  
        End While  
End Sub  
```  
  
## <a name="sample"></a><span data-ttu-id="48f69-184">サンプル</span><span class="sxs-lookup"><span data-stu-id="48f69-184">Sample</span></span>  
 <span data-ttu-id="48f69-185">次のサンプルは、すべての文字列型の列の値を大文字に変換する、簡単な同期出力型の変換コンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="48f69-185">The following sample shows a simple transformation component with synchronous outputs that converts the values of all string columns to uppercase.</span></span> <span data-ttu-id="48f69-186">ただし、この例ではここで説明したメソッドや機能のすべてが使われているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="48f69-186">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="48f69-187">同期出力型の変換コンポーネントで必ずオーバーライドしなければならない重要なメソッドは示していますが、デザイン時の検証のためのコードは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="48f69-187">It demonstrates the important methods that every custom transformation component with synchronous outputs must override, but does not contain code for design-time validation.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
namespace Uppercase  
{  
  [DtsPipelineComponent(DisplayName = "Uppercase")]  
  public class Uppercase : PipelineComponent  
  {  
    ArrayList m_ColumnIndexList = new ArrayList();  
  
    public override void ProvideComponentProperties()  
    {  
      base.ProvideComponentProperties();  
      ComponentMetaData.InputCollection[0].Name = "Uppercase Input";  
      ComponentMetaData.OutputCollection[0].Name = "Uppercase Output";  
    }  
  
    public override void PreExecute()  
    {  
      IDTSInput100 input = ComponentMetaData.InputCollection[0];  
      IDTSInputColumnCollection100 inputColumns = input.InputColumnCollection;  
  
      foreach (IDTSInputColumn100 column in inputColumns)  
      {  
        if (column.DataType == DataType.DT_STR || column.DataType == DataType.DT_WSTR)  
        {  
          m_ColumnIndexList.Add((int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID));  
        }  
      }  
    }  
  
    public override void ProcessInput(int inputID, PipelineBuffer buffer)  
    {  
      while (buffer.NextRow())  
      {  
        foreach (int columnIndex in m_ColumnIndexList)  
        {  
          string str = buffer.GetString(columnIndex);  
          buffer.SetString(columnIndex, str.ToUpper());  
        }  
      }  
    }  
  }  
}  
```  
  
```vb  
Imports System   
Imports System.Collections   
Imports Microsoft.SqlServer.Dts.Pipeline   
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper   
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper   
Namespace Uppercase   
  
 <DtsPipelineComponent(DisplayName="Uppercase")> _   
 Public Class Uppercase   
 Inherits PipelineComponent   
   Private m_ColumnIndexList As ArrayList = New ArrayList   
  
   Public  Overrides Sub ProvideComponentProperties()   
     MyBase.ProvideComponentProperties   
     ComponentMetaData.InputCollection(0).Name = "Uppercase Input"   
     ComponentMetaData.OutputCollection(0).Name = "Uppercase Output"   
   End Sub   
  
   Public  Overrides Sub PreExecute()   
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
     Dim inputColumns As IDTSInputColumnCollection100 = input.InputColumnCollection   
     For Each column As IDTSInputColumn100 In inputColumns   
       If column.DataType = DataType.DT_STR OrElse column.DataType = DataType.DT_WSTR Then   
         m_ColumnIndexList.Add(CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer))   
       End If   
     Next   
   End Sub   
  
   Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
     While buffer.NextRow   
       For Each columnIndex As Integer In m_ColumnIndexList   
         Dim str As String = buffer.GetString(columnIndex)   
         buffer.SetString(columnIndex, str.ToUpper)   
       Next   
     End While   
   End Sub   
 End Class   
End Namespace  
```  
  
<span data-ttu-id="48f69-188">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="48f69-188">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="48f69-189">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48f69-189">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="48f69-190">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="48f69-190">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="48f69-191">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="48f69-191">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f69-192">参照</span><span class="sxs-lookup"><span data-stu-id="48f69-192">See Also</span></span>  
 <span data-ttu-id="48f69-193">[非同期出力型のカスタム変換コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md) </span><span class="sxs-lookup"><span data-stu-id="48f69-193">[Developing a Custom Transformation Component with Asynchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md) </span></span>  
 <span data-ttu-id="48f69-194">[同期変換と非同期変換について](../understanding-synchronous-and-asynchronous-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="48f69-194">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) </span></span>  
 [<span data-ttu-id="48f69-195">スクリプト コンポーネントによる同期変換の作成</span><span class="sxs-lookup"><span data-stu-id="48f69-195">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
