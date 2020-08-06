---
title: カスタム変換先コンポーネントの開発 | Microsoft Docs
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
- validation [Integration Services], components
- destinations [Integration Services], components
- ProcessInput method
- external data sources [Integration Services]
- custom data flow components [Integration Services], destination components
- data flow components [Integration Services], destination components
ms.assetid: 24619363-9535-4c0e-8b62-1d22c6630e40
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6979d14afa0490638162c35bb660f15506803484
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710977"
---
# <a name="developing-a-custom-destination-component"></a><span data-ttu-id="1162a-102">カスタム変換先コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="1162a-102">Developing a Custom Destination Component</span></span>
  <span data-ttu-id="1162a-103">開発者は、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を使用すると、任意のカスタム データ ソースに接続してデータを格納するためのカスタム変換先コンポーネントを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="1162a-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] gives developers the ability to write custom destination components that can connect to and store data in any custom data source.</span></span> <span data-ttu-id="1162a-104">カスタム変換先コンポーネントは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれている、既存の変換先コンポーネントを使用してもアクセスできないデータ ソースに接続する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1162a-104">Custom destination components are useful when you need to connect to data sources that cannot be accessed by using one of the existing source components included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="1162a-105">変換先コンポーネントには 1 つ以上の入力がありますが、出力はありません。</span><span class="sxs-lookup"><span data-stu-id="1162a-105">Destination components have one or more inputs and zero outputs.</span></span> <span data-ttu-id="1162a-106">デザイン時に、外部データ ソースとの接続を作成して設定を行い、そこから列メタデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1162a-106">At design time, they create and configure connections and read column metadata from the external data source.</span></span> <span data-ttu-id="1162a-107">実行時には、外部データ ソースに接続し、データ フロー内で上流にあるコンポーネントから受け取った行を、この外部データ ソースに追加します。</span><span class="sxs-lookup"><span data-stu-id="1162a-107">During execution, they connect to their external data source and add rows that are received from the components upstream in the data flow to the external data source.</span></span> <span data-ttu-id="1162a-108">コンポーネントの実行前に外部データ ソースが存在する場合は、変換先コンポーネントにより、コンポーネントが受け取る列のデータ型が、外部データ ソースの列のデータ型と一致することを確認する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="1162a-108">If the external data source exists prior to execution of the component, the destination component must also ensure that the data types of the columns that the component receives match the data types of the columns at the external data source.</span></span>

 <span data-ttu-id="1162a-109">このセクションでは、変換先コンポーネントの開発方法の詳細について説明し、重要な概念をわかりやすくするため、コード例を示します。</span><span class="sxs-lookup"><span data-stu-id="1162a-109">This section discusses the details of how to develop destination components, and provides code examples to clarify important concepts.</span></span> <span data-ttu-id="1162a-110">データ フロー コンポーネントの開発全般の概要については、「[カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1162a-110">For a general overview of data flow component development, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>

## <a name="design-time"></a><span data-ttu-id="1162a-111">デザイン時</span><span class="sxs-lookup"><span data-stu-id="1162a-111">Design Time</span></span>
 <span data-ttu-id="1162a-112">変換先コンポーネントのデザイン時の機能を実装する作業には、外部データ ソースへの接続の指定、およびコンポーネントが正しく設定されているかどうかの検証が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1162a-112">Implementing the design-time functionality of a destination component involves specifying a connection to an external data source and validating that the component has been correctly configured.</span></span> <span data-ttu-id="1162a-113">定義上、変換先コンポーネントには 1 つの入力と、場合によって 1 つのエラー出力があります。</span><span class="sxs-lookup"><span data-stu-id="1162a-113">By definition, a destination component has one input and possibly one error output.</span></span>

### <a name="creating-the-component"></a><span data-ttu-id="1162a-114">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="1162a-114">Creating the Component</span></span>
 <span data-ttu-id="1162a-115">変換先コンポーネントは、パッケージで定義された <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトを使用して、外部データ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="1162a-115">Destination components connect to external data sources by using <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects defined in a package.</span></span> <span data-ttu-id="1162a-116">変換先コンポーネントは、接続マネージャーに関する要求を [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーやコンポーネントのユーザーに示すため、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> コレクションに要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="1162a-116">The destination component indicates its requirement for a connection manager to the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, and to users of the component, by adding an element to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> collection of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>.</span></span> <span data-ttu-id="1162a-117">このコレクションには 2 つの目的があります。1 つは、接続マネージャーの必要性を [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーに通知することで、もう 1 つは、ユーザーが接続マネージャーを選択または作成した後に、コンポーネントが使用する、パッケージ内の接続マネージャーへの参照を保持することです。</span><span class="sxs-lookup"><span data-stu-id="1162a-117">This collection serves two purposes: first, it advertises the need for a connection manager to [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer; then, after the user has selected or created a connection manager, it holds a reference to the connection manager in the package that is being used by the component.</span></span> <span data-ttu-id="1162a-118"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> がコレクションに追加されると、 **[詳細エディター]** は **[接続プロパティ]** タブを表示します。このタブでは、コンポーネントが使用する接続をパッケージ内で選択したり、新しく作成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="1162a-118">When an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> is added to the collection, the **Advanced Editor** displays the **Connection Properties** tab, to prompt the user to select or create a connection in the package for use by the component.</span></span>

 <span data-ttu-id="1162a-119">次のコード例は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> に入力を追加し、次に <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> オブジェクトを追加する <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> の実装を示します。</span><span class="sxs-lookup"><span data-stu-id="1162a-119">The following code sample shows an implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> that adds an input, and then adds a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> object to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    [DtsPipelineComponent(DisplayName = "Destination Component",ComponentType =ComponentType.DestinationAdapter)]
    public class DestinationComponent : PipelineComponent 
    {
        public override void ProvideComponentProperties()
        {
            // Reset the component.
            base.RemoveAllInputsOutputsAndCustomProperties();
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll();

            IDTSInput100 input = ComponentMetaData.InputCollection.New();
            input.Name = "Input";

            IDTSRuntimeConnection100 connection = ComponentMetaData.RuntimeConnectionCollection.New();
            connection.Name = "ADO.net";
        }
    }
}
```

```vb
Imports System
Imports System.Data
Imports System.Data.SqlClient
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime

Namespace Microsoft.Samples.SqlServer.Dts

    <DtsPipelineComponent(DisplayName:="Destination Component", ComponentType:=ComponentType.DestinationAdapter)> _
    Public Class DestinationComponent
        Inherits PipelineComponent

        Public Overrides Sub ProvideComponentProperties()

            ' Reset the component.
            Me.RemoveAllInputsOutputsAndCustomProperties()
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll()

            Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New()
            input.Name = "Input"

            Dim connection As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New()
            connection.Name = "ADO.net"

        End Sub
    End Class
End Namespace
```

### <a name="connecting-to-an-external-data-source"></a><span data-ttu-id="1162a-120">外部データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="1162a-120">Connecting to an External Data Source</span></span>
 <span data-ttu-id="1162a-121"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> に接続を追加した後、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> メソッドをオーバーライドして、外部データ ソースへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="1162a-121">After a connection is added to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>, you override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method to establish a connection to the external data source.</span></span> <span data-ttu-id="1162a-122">このメソッドは、デザイン時と実行時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1162a-122">This method is called at design time and at run time.</span></span> <span data-ttu-id="1162a-123">コンポーネントは、実行時の接続によって指定された接続マネージャーへの接続を確立し、続いて外部データ ソースへの接続を確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1162a-123">The component must establish a connection to the connection manager specified by the run-time connection, and subsequently, to the external data source.</span></span> <span data-ttu-id="1162a-124">接続が確立されると、コンポーネントは接続を内部にキャッシュし、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> が呼び出されると解放します。</span><span class="sxs-lookup"><span data-stu-id="1162a-124">Once established, the component should cache the connection internally and release it when <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> is called.</span></span> <span data-ttu-id="1162a-125">開発者はこのメソッドをオーバーライドし、コンポーネントが確立した接続を <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> の実行中に解放します。</span><span class="sxs-lookup"><span data-stu-id="1162a-125">Developers override this method, and release the connection established by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>.</span></span> <span data-ttu-id="1162a-126">これらの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> メソッドは、どちらもデザイン時と実行時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1162a-126">Both of these methods, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>, are called at design time and at run time.</span></span>

 <span data-ttu-id="1162a-127">次のコード例では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> メソッドで ADO.NET 接続へ接続し、次に <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> で接続を閉じるコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="1162a-127">The following code example shows a component that connects to an ADO.NET connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method, and then closes the connection in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>.</span></span>

```csharp
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

private SqlConnection sqlConnection;

public override void AcquireConnections(object transaction)
{
    if (ComponentMetaData.RuntimeConnectionCollection[0].ConnectionManager != null)
    {
        ConnectionManager cm = Microsoft.SqlServer.Dts.Runtime.DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection[0].ConnectionManager);
        ConnectionManagerAdoNet cmado = cm.InnerObject as ConnectionManagerAdoNet;

        if (cmado == null)
            throw new Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.");

        sqlConnection = cmado.AcquireConnection(transaction) as SqlConnection;
        sqlConnection.Open();
    }
}

public override void ReleaseConnections()
{
    if (sqlConnection != null && sqlConnection.State != ConnectionState.Closed)
        sqlConnection.Close();
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

Private sqlConnection As SqlConnection

Public Overrides Sub AcquireConnections(ByVal transaction As Object)

    If IsNothing(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager) = False Then

        Dim cm As ConnectionManager = DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager)
        Dim cmado As ConnectionManagerAdoNet = CType(cm.InnerObject,ConnectionManagerAdoNet)

        If IsNothing(cmado) Then
            Throw New Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.")
        End If

        sqlConnection = CType(cmado.AcquireConnection(transaction), SqlConnection)
        sqlConnection.Open()

    End If
End Sub

Public Overrides Sub ReleaseConnections()

    If IsNothing(sqlConnection) = False And sqlConnection.State <> ConnectionState.Closed Then
        sqlConnection.Close()
    End If

End Sub
```

### <a name="validating-the-component"></a><span data-ttu-id="1162a-128">コンポーネントの検証</span><span class="sxs-lookup"><span data-stu-id="1162a-128">Validating the Component</span></span>
 <span data-ttu-id="1162a-129">[コンポーネントの検証](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md)で説明しているように、変換先コンポーネントの開発者は検証を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1162a-129">Destination component developers should perform validation as described in [Component Validation](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md).</span></span> <span data-ttu-id="1162a-130">また、コンポーネントの入力列コレクションで定義されている列のデータ型プロパティが、外部データ ソースの列と一致することを検証する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="1162a-130">In addition, they should verify that the data type properties of the columns defined in the component's input column collection match the columns at the external data source.</span></span> <span data-ttu-id="1162a-131">ただし、コンポーネントまたは [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーが接続されていない状態の場合や、サーバーへのラウンド トリップが許可されない場合など、外部データ ソースに対する入力列の検証が不可能または望ましくないこともあります。</span><span class="sxs-lookup"><span data-stu-id="1162a-131">At times, verifying the input columns against the external data source can be impossible or undesirable, such as when the component or the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer is in a disconnected state, or when round trips to the server are not acceptable.</span></span> <span data-ttu-id="1162a-132">このような状況でも、入力オブジェクトの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.ExternalMetadataColumnCollection%2A> を使用して、入力列コレクションの列を検証することができます。</span><span class="sxs-lookup"><span data-stu-id="1162a-132">In these situations, the columns in the input column collection can still be validated by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.ExternalMetadataColumnCollection%2A> of the input object.</span></span>

 <span data-ttu-id="1162a-133">このコレクションは入力オブジェクトおよび出力オブジェクトの両方に存在し、コンポーネント開発者が外部データ ソースの列から設定します。</span><span class="sxs-lookup"><span data-stu-id="1162a-133">This collection exists on both input and output objects and must be populated by the component developer from the columns at the external data source.</span></span> <span data-ttu-id="1162a-134">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーがオフラインである場合、コンポーネントが接続されていない場合、または <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> プロパティが `false` である場合は、このコレクションを使用して入力列を検証できます。</span><span class="sxs-lookup"><span data-stu-id="1162a-134">This collection can be used to validate the input columns when the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer is offline, when the component is disconnected, or when the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> property is `false`.</span></span>

 <span data-ttu-id="1162a-135">次のコード例は、既存の入力列に基づく外部メタデータ列を追加します。</span><span class="sxs-lookup"><span data-stu-id="1162a-135">The following sample code adds an external metadata column based on an existing input column.</span></span>

```csharp
private void AddExternalMetaDataColumn(IDTSInput100 input,IDTSInputColumn100 inputColumn)
{
    // Set the properties of the external metadata column.
    IDTSExternalMetadataColumn100 externalColumn = input.ExternalMetadataColumnCollection.New();
    externalColumn.Name = inputColumn.Name;
    externalColumn.Precision = inputColumn.Precision;
    externalColumn.Length = inputColumn.Length;
    externalColumn.DataType = inputColumn.DataType;
    externalColumn.Scale = inputColumn.Scale;

    // Map the external column to the input column.
    inputColumn.ExternalMetadataColumnID = externalColumn.ID;
}
```

```vb
Private Sub AddExternalMetaDataColumn(ByVal input As IDTSInput100, ByVal inputColumn As IDTSInputColumn100)

    ' Set the properties of the external metadata column.
    Dim externalColumn As IDTSExternalMetadataColumn100 = input.ExternalMetadataColumnCollection.New()
    externalColumn.Name = inputColumn.Name
    externalColumn.Precision = inputColumn.Precision
    externalColumn.Length = inputColumn.Length
    externalColumn.DataType = inputColumn.DataType
    externalColumn.Scale = inputColumn.Scale

    ' Map the external column to the input column.
    inputColumn.ExternalMetadataColumnID = externalColumn.ID

End Sub
```

## <a name="run-time"></a><span data-ttu-id="1162a-136">実行時間</span><span class="sxs-lookup"><span data-stu-id="1162a-136">Run Time</span></span>
 <span data-ttu-id="1162a-137">実行中は、データでいっぱいになった <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> を上流コンポーネントから渡されるたびに、変換先コンポーネントは <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> メソッドに対する呼び出しを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1162a-137">During execution, the destination component receives a call to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method each time a full <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> is available from the upstream component.</span></span> <span data-ttu-id="1162a-138">このメソッドは、渡されるバッファーがなくなり、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> プロパティが `true` になるまで、繰り返して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1162a-138">This method is called repeatedly until there are no more buffers available and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property is `true`.</span></span> <span data-ttu-id="1162a-139">このメソッド内で、変換先コンポーネントはバッファー内の行と列を読み取り、外部データ ソースに追加します。</span><span class="sxs-lookup"><span data-stu-id="1162a-139">During this method, destination components read columns and rows in the buffer, and add them to the external data source.</span></span>

### <a name="locating-columns-in-the-buffer"></a><span data-ttu-id="1162a-140">バッファー内の列の検索</span><span class="sxs-lookup"><span data-stu-id="1162a-140">Locating Columns in the Buffer</span></span>
 <span data-ttu-id="1162a-141">コンポーネントの入力バッファーには、データ フロー内でそのコンポーネントの上流に位置するコンポーネントの出力列コレクションで定義された、すべての列が格納されています。</span><span class="sxs-lookup"><span data-stu-id="1162a-141">The input buffer for a component contains all the columns defined in the output column collections of the components upstream from the component in the data flow.</span></span> <span data-ttu-id="1162a-142">たとえば、変換元コンポーネントの出力に 3 つの列があり、その次のコンポーネントで出力列が 1 つ追加された場合、変換先コンポーネントが書き出す列が 2 つのみの場合でも、変換先コンポーネントに用意されたバッファーには 4 つの列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1162a-142">For example, if a source component provides three columns in its output, and the next component adds an additional output column, the buffer provided to the destination component contains four columns, even if the destination component will write only two columns.</span></span>

 <span data-ttu-id="1162a-143">入力バッファー内の列の順序は、変換先コンポーネントの入力列コレクション内の列のインデックスでは定義されません。</span><span class="sxs-lookup"><span data-stu-id="1162a-143">The order of the columns in the input buffer is not defined by the index of the column in the input column collection of the destination component.</span></span> <span data-ttu-id="1162a-144">バッファー行で列を確実に検索するには、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> メソッドを使用するしか方法がありません。</span><span class="sxs-lookup"><span data-stu-id="1162a-144">Columns can be reliably located in a buffer row only by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.</span></span> <span data-ttu-id="1162a-145">このメソッドは、指定されたバッファー内で指定された系列 ID の列を検索し、行内の位置を返します。</span><span class="sxs-lookup"><span data-stu-id="1162a-145">This method locates the column that has the specified lineage ID in the specified buffer, and returns its location in the row.</span></span> <span data-ttu-id="1162a-146">入力列のインデックスは、通常、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> メソッド内で検索され、後で <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> で使用するために開発者によってキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="1162a-146">The indexes of the input columns are typically located during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, and cached by the developer for use later during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>

 <span data-ttu-id="1162a-147">次のコード例は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> でバッファー内の入力列の位置を検索し、配列に保存します。</span><span class="sxs-lookup"><span data-stu-id="1162a-147">The following code example finds the location of the input columns in the buffer during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> and stores them in an array.</span></span> <span data-ttu-id="1162a-148">続いてこの配列を <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> の処理中に使用し、バッファー内の列の値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="1162a-148">The array is subsequently used during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> to read the values of the columns in the buffer.</span></span>

```csharp
int[] cols;

public override void PreExecute()
{
    IDTSInput100 input = ComponentMetaData.InputCollection[0];

    cols = new int[input.InputColumnCollection.Count];

    for (int x = 0; x < input.InputColumnCollection.Count; x++)
    {
        cols[x] = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection[x].LineageID);
    }
}
```

```vb
Private cols As Integer()

Public Overrides Sub PreExecute()

    Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)

    ReDim cols(input.InputColumnCollection.Count)

    For x As Integer = 0 To input.InputColumnCollection.Count

        cols(x) = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection(x).LineageID)
    Next x

End Sub
```

### <a name="processing-rows"></a><span data-ttu-id="1162a-149">行の処理</span><span class="sxs-lookup"><span data-stu-id="1162a-149">Processing Rows</span></span>
 <span data-ttu-id="1162a-150">バッファー内の入力列を検索したら、列の値を読み取って外部データ ソースに書き出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1162a-150">Once the input columns have been located in the buffer, they can be read and written to the external data source.</span></span>

 <span data-ttu-id="1162a-151">変換先コンポーネントが行を外部データ ソースに書き込んでいる間に、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> メソッドを呼び出して "Rows read" または "BLOB bytes read" パフォーマンス カウンターを更新することができます。</span><span class="sxs-lookup"><span data-stu-id="1162a-151">While the destination component writes rows to the external data source, you may want to update the "Rows read" or "BLOB bytes read" performance counters by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> method.</span></span> <span data-ttu-id="1162a-152">これらのパフォーマンス カウンターの詳細については、「 [パフォーマンス カウンター](../performance/performance-counters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1162a-152">For more information, see [Performance Counters](../performance/performance-counters.md).</span></span>

 <span data-ttu-id="1162a-153">次の例は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> で提供されるバッファーから行を読み取るコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="1162a-153">The following example shows a component that reads rows from the buffer provided in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span> <span data-ttu-id="1162a-154">バッファー内の列のインデックスは、先のコード例にある <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 内で検索したものを使用しています。</span><span class="sxs-lookup"><span data-stu-id="1162a-154">The indexes of the columns in the buffer were located during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> in the preceding code example.</span></span>

```csharp
public override void ProcessInput(int inputID, PipelineBuffer buffer)
{
        while (buffer.NextRow())
        {
            foreach (int col in cols)
            {
                if (!buffer.IsNull(col))
                {
                    //  TODO: Read the column data.
                }
            }
        }
}
```

```vb
Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)

        While (buffer.NextRow())

            For Each col As Integer In cols

                If buffer.IsNull(col) = False Then

                    '  TODO: Read the column data.
                End If

            Next col
        End While
End Sub
```

## <a name="sample"></a><span data-ttu-id="1162a-155">サンプル</span><span class="sxs-lookup"><span data-stu-id="1162a-155">Sample</span></span>
 <span data-ttu-id="1162a-156">次の例は、ファイル接続マネージャーを使用して、データ フローからのバイナリ データをファイルに保存する、簡単な変換先コンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="1162a-156">The following sample shows a simple destination component that uses a File connection manager to save binary data from the data flow into files.</span></span> <span data-ttu-id="1162a-157">ただし、この例ではここで説明したメソッドや機能のすべてが使われているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="1162a-157">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="1162a-158">変換先コンポーネントが必ずオーバーライドしなければならない重要なメソッドは示していますが、デザイン時の検証のためのコードは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="1162a-158">It demonstrates the important methods that every custom destination component must override, but does not contain code for design-time validation.</span></span>

```csharp
using System;
using System.IO;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace BlobDst
{
  [DtsPipelineComponent(DisplayName = "BLOB Extractor Destination", Description = "Writes values of BLOB columns to files")]
  public class BlobDst : PipelineComponent
  {
    string m_DestDir;
    int m_FileNameColumnIndex = -1;
    int m_BlobColumnIndex = -1;

    public override void ProvideComponentProperties()
    {
      IDTSInput100 input = ComponentMetaData.InputCollection.New();
      input.Name = "BLOB Extractor Destination Input";
      input.HasSideEffects = true;

      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection.New();
      conn.Name = "FileConnection";
    }

    public override void AcquireConnections(object transaction)
    {
      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection[0];
      m_DestDir = (string)conn.ConnectionManager.AcquireConnection(null);

      if (m_DestDir.Length > 0 && m_DestDir[m_DestDir.Length - 1] != '\\')
        m_DestDir += "\\";
    }

    public override IDTSInputColumn100 SetUsageType(int inputID, IDTSVirtualInput100 virtualInput, int lineageID, DTSUsageType usageType)
    {
      IDTSInputColumn100 inputColumn = base.SetUsageType(inputID, virtualInput, lineageID, usageType);
      IDTSCustomProperty100 custProp;

      custProp = inputColumn.CustomPropertyCollection.New();
      custProp.Name = "IsFileName";
      custProp.Value = (object)false;

      custProp = inputColumn.CustomPropertyCollection.New();
      custProp.Name = "IsBLOB";
      custProp.Value = (object)false;

      return inputColumn;
    }

    public override void PreExecute()
    {
      IDTSInput100 input = ComponentMetaData.InputCollection[0];
      IDTSInputColumnCollection100 inputColumns = input.InputColumnCollection;
      IDTSCustomProperty100 custProp;

      foreach (IDTSInputColumn100 column in inputColumns)
      {
        custProp = column.CustomPropertyCollection["IsFileName"];
        if ((bool)custProp.Value == true)
        {
          m_FileNameColumnIndex = (int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID);
        }

        custProp = column.CustomPropertyCollection["IsBLOB"];
        if ((bool)custProp.Value == true)
        {
          m_BlobColumnIndex = (int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID);
        }
      }
    }

    public override void ProcessInput(int inputID, PipelineBuffer buffer)
    {
      while (buffer.NextRow())
      {
        string strFileName = buffer.GetString(m_FileNameColumnIndex);
        int blobLength = (int)buffer.GetBlobLength(m_BlobColumnIndex);
        byte[] blobData = buffer.GetBlobData(m_BlobColumnIndex, 0, blobLength);

        strFileName = TranslateFileName(strFileName);

        // Make sure directory exists before creating file.
        FileInfo fi = new FileInfo(strFileName);
        if (!fi.Directory.Exists)
          fi.Directory.Create();

        // Write the data to the file.
        FileStream fs = new FileStream(strFileName, FileMode.Create, FileAccess.Write, FileShare.None);
        fs.Write(blobData, 0, blobLength);
        fs.Close();
      }
    }

    private string TranslateFileName(string fileName)
    {
      if (fileName.Length > 2 && fileName[1] == ':')
        return m_DestDir + fileName.Substring(3, fileName.Length - 3);
      else
        return m_DestDir + fileName;
    }
  }
}
```

```vb
Imports System 
Imports System.IO 
Imports Microsoft.SqlServer.Dts.Pipeline 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Namespace BlobDst 

 <DtsPipelineComponent(DisplayName="BLOB Extractor Destination", Description="Writes values of BLOB columns to files")> _ 
 Public Class BlobDst 
 Inherits PipelineComponent 
   Private m_DestDir As String 
   Private m_FileNameColumnIndex As Integer = -1 
   Private m_BlobColumnIndex As Integer = -1 

   Public  Overrides Sub ProvideComponentProperties() 
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New 
     input.Name = "BLOB Extractor Destination Input" 
     input.HasSideEffects = True 
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New 
     conn.Name = "FileConnection" 
   End Sub 

   Public  Overrides Sub AcquireConnections(ByVal transaction As Object) 
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection(0) 
     m_DestDir = CType(conn.ConnectionManager.AcquireConnection(Nothing), String) 
     If m_DestDir.Length > 0 AndAlso Not (m_DestDir(m_DestDir.Length - 1) = "\"C) Then 
       m_DestDir += "\" 
     End If 
   End Sub 

   Public  Overrides Function SetUsageType(ByVal inputID As Integer, ByVal virtualInput As IDTSVirtualInput100, ByVal lineageID As Integer, ByVal usageType As DTSUsageType) As IDTSInputColumn100 
     Dim inputColumn As IDTSInputColumn100 = MyBase.SetUsageType(inputID, virtualInput, lineageID, usageType) 
     Dim custProp As IDTSCustomProperty100 
     custProp = inputColumn.CustomPropertyCollection.New 
     custProp.Name = "IsFileName" 
     custProp.Value = CType(False, Object) 
     custProp = inputColumn.CustomPropertyCollection.New 
     custProp.Name = "IsBLOB" 
     custProp.Value = CType(False, Object) 
     Return inputColumn 
   End Function 

   Public  Overrides Sub PreExecute() 
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0) 
     Dim inputColumns As IDTSInputColumnCollection100 = input.InputColumnCollection 
     Dim custProp As IDTSCustomProperty100 
     For Each column As IDTSInputColumn100 In inputColumns 
       custProp = column.CustomPropertyCollection("IsFileName") 
       If CType(custProp.Value, Boolean) = True Then 
         m_FileNameColumnIndex = CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer) 
       End If 
       custProp = column.CustomPropertyCollection("IsBLOB") 
       If CType(custProp.Value, Boolean) = True Then 
         m_BlobColumnIndex = CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer) 
       End If 
     Next 
   End Sub 

   Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer) 
     While buffer.NextRow 
       Dim strFileName As String = buffer.GetString(m_FileNameColumnIndex) 
       Dim blobLength As Integer = CType(buffer.GetBlobLength(m_BlobColumnIndex), Integer) 
       Dim blobData As Byte() = buffer.GetBlobData(m_BlobColumnIndex, 0, blobLength) 
       strFileName = TranslateFileName(strFileName) 
       Dim fi As FileInfo = New FileInfo(strFileName) 
       ' Make sure directory exists before creating file.
       If Not fi.Directory.Exists Then 
         fi.Directory.Create 
       End If 
       ' Write the data to the file.
       Dim fs As FileStream = New FileStream(strFileName, FileMode.Create, FileAccess.Write, FileShare.None) 
       fs.Write(blobData, 0, blobLength) 
       fs.Close 
     End While 
   End Sub 

   Private Function TranslateFileName(ByVal fileName As String) As String 
     If fileName.Length > 2 AndAlso fileName(1) = ":"C Then 
       Return m_DestDir + fileName.Substring(3, fileName.Length - 3) 
     Else 
       Return m_DestDir + fileName 
     End If 
   End Function 
 End Class 
End Namespace
```

<span data-ttu-id="1162a-159">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="1162a-159">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1162a-160">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1162a-160">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1162a-161">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="1162a-161">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1162a-162">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="1162a-162">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="1162a-163">参照</span><span class="sxs-lookup"><span data-stu-id="1162a-163">See Also</span></span>
 <span data-ttu-id="1162a-164">[カスタム変換元コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)[スクリプトコンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)</span><span class="sxs-lookup"><span data-stu-id="1162a-164">[Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)</span></span>


