---
title: カスタム変換元コンポーネントの開発 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [Integration Services], components
- external data sources [Integration Services]
- data flow components [Integration Services], source components
- output columns [Integration Services]
- custom data flow components [Integration Services], source components
- custom sources [Integration Services]
- source components [Integration Services]
ms.assetid: 4dc0f631-8fd6-4007-b573-ca67f58ca068
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6679b28463a09efe069235a5aef9dca54a381d62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736619"
---
# <a name="developing-a-custom-source-component"></a><span data-ttu-id="8f099-102">カスタム変換元コンポーネントの開発</span><span class="sxs-lookup"><span data-stu-id="8f099-102">Developing a Custom Source Component</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8f099-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を使用することで、開発者は、データ フロー タスクでカスタム データ ソースに接続して、変換元のデータを他のコンポーネントに提供する変換元コンポーネントを記述できます。</span><span class="sxs-lookup"><span data-stu-id="8f099-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] gives developers the ability to write source components that can connect to custom data sources and supply data from those sources to other components in a data flow task.</span></span> <span data-ttu-id="8f099-104">カスタム変換元を作成できると、既存の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 変換元のいずれかを使用してアクセスできないデータ ソースに接続する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="8f099-104">The ability to create custom sources is valuable when you must connect to data sources that cannot be accessed by using one of the existing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sources.</span></span>

 <span data-ttu-id="8f099-105">変換元コンポーネントには 1 つ以上の出力がありますが、入力はありません。</span><span class="sxs-lookup"><span data-stu-id="8f099-105">Source components have one or more outputs and zero inputs.</span></span> <span data-ttu-id="8f099-106">デザイン時には、変換元コンポーネントを使用して接続を作成、設定し、外部データ ソースから列メタデータを読み取って、外部データ ソースに基づいて変換元の出力列を設定します。</span><span class="sxs-lookup"><span data-stu-id="8f099-106">At design time, source components are used to create and configure connections, read column metadata from the external data source, and configure the source's output columns based on the external data source.</span></span> <span data-ttu-id="8f099-107">実行時には、外部データ ソースに接続し、出力バッファーに行を追加します。</span><span class="sxs-lookup"><span data-stu-id="8f099-107">During execution they connect to the external data source and add rows to an output buffer.</span></span> <span data-ttu-id="8f099-108">データ フロー タスクは、次にデータ行のバッファーを下流コンポーネントに渡します。</span><span class="sxs-lookup"><span data-stu-id="8f099-108">The data flow task then provides this buffer of data rows to downstream components.</span></span>

 <span data-ttu-id="8f099-109">データ フロー コンポーネントの開発全般の概要については、「[カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f099-109">For a general overview of data flow component development, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>

## <a name="design-time"></a><span data-ttu-id="8f099-110">デザイン時</span><span class="sxs-lookup"><span data-stu-id="8f099-110">Design Time</span></span>
 <span data-ttu-id="8f099-111">変換元コンポーネントのデザイン時の機能を実装する作業には、外部データ ソースへの接続の指定、データ ソースを反映する出力列の追加と設定、およびコンポーネントが実行可能かどうかの検証が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8f099-111">Implementing the design-time functionality of a source component involves specifying a connection to an external data source, adding and configuring output columns that reflect the data source, and validating that the component is ready to execute.</span></span> <span data-ttu-id="8f099-112">定義上、変換元コンポーネントには入力がなく、1 つ以上の非同期出力があります。</span><span class="sxs-lookup"><span data-stu-id="8f099-112">By definition, a source component has zero inputs and one or more asynchronous outputs.</span></span>

### <a name="creating-the-component"></a><span data-ttu-id="8f099-113">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="8f099-113">Creating the Component</span></span>
 <span data-ttu-id="8f099-114">変換元コンポーネントは、パッケージで定義された <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトを使用して、外部データ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="8f099-114">Source components connect to external data sources by using <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects defined in a package.</span></span> <span data-ttu-id="8f099-115">変換元コンポーネントで、接続マネージャーに対する要求を示すには、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> プロパティの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> コレクションに要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="8f099-115">They indicate their requirement for a connection manager by adding an element to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> collection of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property.</span></span> <span data-ttu-id="8f099-116">このコレクションには 2 つの目的があります。それは、コンポーネントが使用する、パッケージ内の接続マネージャーへの参照を保持することと、接続マネージャーの必要性をデザイナーに通知することです。</span><span class="sxs-lookup"><span data-stu-id="8f099-116">This collection serves two purposes-to hold references to connection managers in the package used by the component, and to advertise the need for a connection manager to the designer.</span></span> <span data-ttu-id="8f099-117"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> がコレクションに追加されると、 **[詳細エディター]** に **[接続プロパティ]** タブが表示されます。このタブを使用することで、ユーザーはパッケージ内で接続を選択したり、作成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8f099-117">When an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> has been added to the collection, the **Advanced Editor** displays the **Connection Properties** tab, which lets users select or create a connection in the package.</span></span>

 <span data-ttu-id="8f099-118">次のコード例は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> に出力と <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> オブジェクトを追加する <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> の実装を示します。</span><span class="sxs-lookup"><span data-stu-id="8f099-118">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> that adds an output, and adds a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> object to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.</span></span>

```csharp
using System;
using System.Collections;
using System.Data;
using System.Data.SqlClient;
using System.Data.OleDb;
using Microsoft.SqlServer.Dts.Runtime;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
    [DtsPipelineComponent(DisplayName = "MySourceComponent",ComponentType = ComponentType.SourceAdapter)]
    public class MyComponent : PipelineComponent
    {
        public override void ProvideComponentProperties()
        {
            // Reset the component.
            base.RemoveAllInputsOutputsAndCustomProperties();
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll();

            IDTSOutput100 output = ComponentMetaData.OutputCollection.New();
            output.Name = "Output";

            IDTSRuntimeConnection100 connection = ComponentMetaData.RuntimeConnectionCollection.New();
            connection.Name = "ADO.NET";
        }
```

```vb
Imports System.Data
Imports System.Data.SqlClient
Imports Microsoft.SqlServer.Dts.Runtime
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper

<DtsPipelineComponent(DisplayName:="MySourceComponent", ComponentType:=ComponentType.SourceAdapter)> _
Public Class MySourceComponent
    Inherits PipelineComponent

    Public Overrides Sub ProvideComponentProperties()

        ' Allow for resetting the component.
        RemoveAllInputsOutputsAndCustomProperties()
        ComponentMetaData.RuntimeConnectionCollection.RemoveAll()

        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New()
        output.Name = "Output"

        Dim connection As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New()
        connection.Name = "ADO.NET"

    End Sub
End Class
```

### <a name="connecting-to-an-external-data-source"></a><span data-ttu-id="8f099-119">外部データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="8f099-119">Connecting to an External Data Source</span></span>
 <span data-ttu-id="8f099-120"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> に接続を追加した後、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> メソッドをオーバーライドして、外部データ ソースへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="8f099-120">After a connection has been added to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>, you override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method to establish a connection to the external data source.</span></span> <span data-ttu-id="8f099-121">このメソッドは、デザイン時と実行時の両方で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8f099-121">This method is called during both design and execution time.</span></span> <span data-ttu-id="8f099-122">コンポーネントは、実行時の接続によって指定された接続マネージャーへの接続を確立し、続いて外部データ ソースへの接続を確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f099-122">The component should establish a connection to the connection manager specified by the run-time connection, and subsequently, to the external data source.</span></span>

 <span data-ttu-id="8f099-123">接続は、確立後にコンポーネントによって内部でキャッシュされ、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> メソッドの呼び出し時に解放される必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f099-123">After the connection is established, it should be cached internally by the component and released when the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> method is called.</span></span> <span data-ttu-id="8f099-124"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> メソッドは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> メソッドと同様、デザイン時と実行時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8f099-124">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> method is called at design and execution time, like the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method.</span></span> <span data-ttu-id="8f099-125">開発者はこのメソッドをオーバーライドし、コンポーネントが確立した接続を <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> の実行中に解放します。</span><span class="sxs-lookup"><span data-stu-id="8f099-125">Developers override this method, and release the connection established by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>.</span></span>

 <span data-ttu-id="8f099-126">次のコード例では、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> メソッドで ADO.NET 接続へ接続し、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> で接続を閉じるコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="8f099-126">The following code example shows a component that connects to an ADO.NET connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method and closes the connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> method.</span></span>

```csharp
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
Private sqlConnection As SqlConnection

Public Overrides Sub AcquireConnections(ByVal transaction As Object)

    If Not IsNothing(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager) Then

        Dim cm As ConnectionManager = Microsoft.SqlServer.Dts.Runtime.DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager)
        Dim cmado As ConnectionManagerAdoNet = CType(cm.InnerObject, ConnectionManagerAdoNet)

        If IsNothing(cmado) Then
            Throw New Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.")
        End If

        sqlConnection = CType(cmado.AcquireConnection(transaction), SqlConnection)
        sqlConnection.Open()

    End If
End Sub

Public Overrides Sub ReleaseConnections()

    If Not IsNothing(sqlConnection) And sqlConnection.State <> ConnectionState.Closed Then
        sqlConnection.Close()
    End If

End Sub
```

### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="8f099-127">出力列の作成と設定</span><span class="sxs-lookup"><span data-stu-id="8f099-127">Creating and Configuring Output Columns</span></span>
 <span data-ttu-id="8f099-128">変換元コンポーネントの出力列は、実行中にコンポーネントがデータ フローに追加する外部データ ソースの列を反映しています。</span><span class="sxs-lookup"><span data-stu-id="8f099-128">The output columns of a source component reflect the columns from the external data source that the component adds to the data flow during execution.</span></span> <span data-ttu-id="8f099-129">デザイン時は、外部データ ソースに接続するようにコンポーネントを設定した後で、出力列を追加します。</span><span class="sxs-lookup"><span data-stu-id="8f099-129">At design time, you add output columns after the component has been configured to connect to an external data source.</span></span> <span data-ttu-id="8f099-130">出力コレクションに列を追加するため、デザイン時にコンポーネントが使用するメソッドは、そのコンポーネントの要件に応じて異なります。ただし、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> や <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> の実行中には追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="8f099-130">The design-time method that a component uses to add the columns to its output collection can vary based on the needs of the component, although they should not be added during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>.</span></span> <span data-ttu-id="8f099-131">たとえば、コンポーネントのデータセットを制御するカスタム プロパティに SQL ステートメントが含まれると、コンポーネントは <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetComponentProperty%2A> メソッドで出力列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="8f099-131">For example, a component that contains a SQL statement in a custom property that controls the data set for the component may add its output columns during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetComponentProperty%2A> method.</span></span> <span data-ttu-id="8f099-132">コンポーネントは接続がキャッシュされているかどうかを確認し、キャッシュされている場合、データ ソースに接続して出力列を生成します。</span><span class="sxs-lookup"><span data-stu-id="8f099-132">The component checks to see whether it has a cached connection, and, if it does, connects to the data source and generates its output columns.</span></span>

 <span data-ttu-id="8f099-133">出力列を作成したら、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> メソッドを呼び出して、そのデータ型プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="8f099-133">After an output column has been created, set its data type properties by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> method.</span></span> <span data-ttu-id="8f099-134">このメソッドが必要なのは、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A>、および <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> の各プロパティが読み取り専用で、各プロパティの設定が他の設定に依存しているためです。</span><span class="sxs-lookup"><span data-stu-id="8f099-134">This method is necessary because the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> properties are read-only and each property is dependent on the settings of the other.</span></span> <span data-ttu-id="8f099-135">このメソッドを使用すると、これらの値に対する要件が一貫性を持つように設定され、データ フロー タスクで、設定が正しいかどうか検証されます。</span><span class="sxs-lookup"><span data-stu-id="8f099-135">This method enforces the need for these values to be set consistently, and the data flow task validates that they are set correctly.</span></span>

 <span data-ttu-id="8f099-136">列の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> により、他のプロパティに設定される値が決定されます。</span><span class="sxs-lookup"><span data-stu-id="8f099-136">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> of the column determines the values that are set for the other properties.</span></span> <span data-ttu-id="8f099-137">次の表は、各 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> の依存するプロパティの要件を示しています。</span><span class="sxs-lookup"><span data-stu-id="8f099-137">The following table shows the requirements on the dependent properties for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>.</span></span> <span data-ttu-id="8f099-138">ここに示されていないデータ型の場合、依存するプロパティは 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="8f099-138">The data types not listed have their dependent properties set to zero.</span></span>

|<span data-ttu-id="8f099-139">DataType</span><span class="sxs-lookup"><span data-stu-id="8f099-139">DataType</span></span>|<span data-ttu-id="8f099-140">長さ</span><span class="sxs-lookup"><span data-stu-id="8f099-140">Length</span></span>|<span data-ttu-id="8f099-141">スケール</span><span class="sxs-lookup"><span data-stu-id="8f099-141">Scale</span></span>|<span data-ttu-id="8f099-142">Precision</span><span class="sxs-lookup"><span data-stu-id="8f099-142">Precision</span></span>|<span data-ttu-id="8f099-143">CodePage</span><span class="sxs-lookup"><span data-stu-id="8f099-143">CodePage</span></span>|
|--------------|------------|-----------|---------------|--------------|
|<span data-ttu-id="8f099-144">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="8f099-144">DT_DECIMAL</span></span>|<span data-ttu-id="8f099-145">0</span><span class="sxs-lookup"><span data-stu-id="8f099-145">0</span></span>|<span data-ttu-id="8f099-146">0 より大きく 28 以下。</span><span class="sxs-lookup"><span data-stu-id="8f099-146">Greater than 0 and less than or equal to 28.</span></span>|<span data-ttu-id="8f099-147">0</span><span class="sxs-lookup"><span data-stu-id="8f099-147">0</span></span>|<span data-ttu-id="8f099-148">0</span><span class="sxs-lookup"><span data-stu-id="8f099-148">0</span></span>|
|<span data-ttu-id="8f099-149">DT_CY</span><span class="sxs-lookup"><span data-stu-id="8f099-149">DT_CY</span></span>|<span data-ttu-id="8f099-150">0</span><span class="sxs-lookup"><span data-stu-id="8f099-150">0</span></span>|<span data-ttu-id="8f099-151">0</span><span class="sxs-lookup"><span data-stu-id="8f099-151">0</span></span>|<span data-ttu-id="8f099-152">0</span><span class="sxs-lookup"><span data-stu-id="8f099-152">0</span></span>|<span data-ttu-id="8f099-153">0</span><span class="sxs-lookup"><span data-stu-id="8f099-153">0</span></span>|
|<span data-ttu-id="8f099-154">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="8f099-154">DT_NUMERIC</span></span>|<span data-ttu-id="8f099-155">0</span><span class="sxs-lookup"><span data-stu-id="8f099-155">0</span></span>|<span data-ttu-id="8f099-156">0 より大きく 28 以下で、有効桁数の値未満</span><span class="sxs-lookup"><span data-stu-id="8f099-156">Greater than 0 and less than or equal to 28, and less than Precision.</span></span>|<span data-ttu-id="8f099-157">1 以上 38 以下</span><span class="sxs-lookup"><span data-stu-id="8f099-157">Greater than or equal to 1 and less than or equal to 38.</span></span>|<span data-ttu-id="8f099-158">0</span><span class="sxs-lookup"><span data-stu-id="8f099-158">0</span></span>|
|<span data-ttu-id="8f099-159">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="8f099-159">DT_BYTES</span></span>|<span data-ttu-id="8f099-160">0 より大きい</span><span class="sxs-lookup"><span data-stu-id="8f099-160">Greater than 0.</span></span>|<span data-ttu-id="8f099-161">0</span><span class="sxs-lookup"><span data-stu-id="8f099-161">0</span></span>|<span data-ttu-id="8f099-162">0</span><span class="sxs-lookup"><span data-stu-id="8f099-162">0</span></span>|<span data-ttu-id="8f099-163">0</span><span class="sxs-lookup"><span data-stu-id="8f099-163">0</span></span>|
|<span data-ttu-id="8f099-164">DT_STR</span><span class="sxs-lookup"><span data-stu-id="8f099-164">DT_STR</span></span>|<span data-ttu-id="8f099-165">0 より大きく 8000 未満</span><span class="sxs-lookup"><span data-stu-id="8f099-165">Greater than 0 and less than 8000.</span></span>|<span data-ttu-id="8f099-166">0</span><span class="sxs-lookup"><span data-stu-id="8f099-166">0</span></span>|<span data-ttu-id="8f099-167">0</span><span class="sxs-lookup"><span data-stu-id="8f099-167">0</span></span>|<span data-ttu-id="8f099-168">0 以外の有効なコード ページ</span><span class="sxs-lookup"><span data-stu-id="8f099-168">Not 0, and a valid code page.</span></span>|
|<span data-ttu-id="8f099-169">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="8f099-169">DT_WSTR</span></span>|<span data-ttu-id="8f099-170">0 より大きく 4000 未満</span><span class="sxs-lookup"><span data-stu-id="8f099-170">Greater than 0 and less than 4000.</span></span>|<span data-ttu-id="8f099-171">0</span><span class="sxs-lookup"><span data-stu-id="8f099-171">0</span></span>|<span data-ttu-id="8f099-172">0</span><span class="sxs-lookup"><span data-stu-id="8f099-172">0</span></span>|<span data-ttu-id="8f099-173">0</span><span class="sxs-lookup"><span data-stu-id="8f099-173">0</span></span>|

 <span data-ttu-id="8f099-174">データ型プロパティの制約は出力列のデータ型に基づくため、マネージド型を処理する場合、[!INCLUDE[ssIS](../../includes/ssis-md.md)] の正しいデータ型を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f099-174">Because the restrictions on the data type properties are based on the data type of the output column, you must choose the correct [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type when you work with managed types.</span></span> <span data-ttu-id="8f099-175">基本クラスでは、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>、および <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> の 3 つのヘルパー メソッドが提供され、これを使用すると、マネージド コンポーネントの開発者は、マネージド型に対応する [!INCLUDE[ssIS](../../includes/ssis-md.md)] のデータ型を適切に選択できます。</span><span class="sxs-lookup"><span data-stu-id="8f099-175">The base class provides three helper methods, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>, to assist managed component developers in selecting an [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type given a managed type.</span></span> <span data-ttu-id="8f099-176">これらのメソッドは、マネージド データ型と [!INCLUDE[ssIS](../../includes/ssis-md.md)] のデータ型を相互に変換します。</span><span class="sxs-lookup"><span data-stu-id="8f099-176">These methods convert managed data types to [!INCLUDE[ssIS](../../includes/ssis-md.md)] data types, and vice versa.</span></span>

 <span data-ttu-id="8f099-177">次のコード例は、テーブルのスキーマに基づいて、コンポーネントの出力列コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8f099-177">The following code example shows how the output column collection of a component is populated based on the schema of a table.</span></span> <span data-ttu-id="8f099-178">基本クラスのヘルパー メソッドを使用して列のデータ型を設定し、そのデータ型に基づいて依存するプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="8f099-178">The helper methods of the base class are used to set the data type of the column, and the dependent properties are set based on the data type.</span></span>

```csharp
SqlCommand sqlCommand;

private void CreateColumnsFromDataTable()
{
    // Get the output.
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

    // Start clean, and remove the columns from both collections.
    output.OutputColumnCollection.RemoveAll();
    output.ExternalMetadataColumnCollection.RemoveAll();

    this.sqlCommand = sqlConnection.CreateCommand();
    this.sqlCommand.CommandType = CommandType.Text;
    this.sqlCommand.CommandText = (string)ComponentMetaData.CustomPropertyCollection["SqlStatement"].Value;
    SqlDataReader schemaReader = this.sqlCommand.ExecuteReader(CommandBehavior.SchemaOnly);
    DataTable dataTable = schemaReader.GetSchemaTable();

    // Walk the columns in the schema, 
    // and for each data column create an output column and an external metadata column.
    foreach (DataRow row in dataTable.Rows)
    {
        IDTSOutputColumn100 outColumn = output.OutputColumnCollection.New();
        IDTSExternalMetadataColumn100 exColumn = output.ExternalMetadataColumnCollection.New();

        // Set column data type properties.
        bool isLong = false;
        DataType dt = DataRecordTypeToBufferType((Type)row["DataType"]);
        dt = ConvertBufferDataTypeToFitManaged(dt, ref isLong);
        int length = 0;
        int precision = (short)row["NumericPrecision"];
        int scale = (short)row["NumericScale"];
        int codepage = dataTable.Locale.TextInfo.ANSICodePage;

        switch (dt)
        {
            // The length cannot be zero, and the code page property must contain a valid code page.
            case DataType.DT_STR:
            case DataType.DT_TEXT:
                length = precision;
                precision = 0;
                scale = 0;
                break;

            case DataType.DT_WSTR:
                length = precision;
                codepage = 0;
                scale = 0;
                precision = 0;
                break;

            case DataType.DT_BYTES:
                precision = 0;
                scale = 0;
                codepage = 0;
                break;

            case DataType.DT_NUMERIC:
                length = 0;
                codepage = 0;

                if (precision > 38)
                    precision = 38;

                if (scale > 6)
                    scale = 6;
                break;

            case DataType.DT_DECIMAL:
                length = 0;
                precision = 0;
                codepage = 0;
                break;

            default:
                length = 0;
                precision = 0;
                codepage = 0;
                scale = 0;
                break;

        }

        // Set the properties of the output column.
        outColumn.Name = (string)row["ColumnName"];
        outColumn.SetDataTypeProperties(dt, length, precision, scale, codepage);
    }
}
```

```vb
Private sqlCommand As SqlCommand

Private Sub CreateColumnsFromDataTable()

    ' Get the output.
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

    ' Start clean, and remove the columns from both collections.
    output.OutputColumnCollection.RemoveAll()
    output.ExternalMetadataColumnCollection.RemoveAll()

    Me.sqlCommand = sqlConnection.CreateCommand()
    Me.sqlCommand.CommandType = CommandType.Text
    Me.sqlCommand.CommandText = CStr(ComponentMetaData.CustomPropertyCollection("SqlStatement").Value)

    Dim schemaReader As SqlDataReader = Me.sqlCommand.ExecuteReader(CommandBehavior.SchemaOnly)
    Dim dataTable As DataTable = schemaReader.GetSchemaTable()

    ' Walk the columns in the schema, 
    ' and for each data column create an output column and an external metadata column.
    For Each row As DataRow In dataTable.Rows

        Dim outColumn As IDTSOutputColumn100 = output.OutputColumnCollection.New()
        Dim exColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New()

        ' Set column data type properties.
        Dim isLong As Boolean = False
        Dim dt As DataType = DataRecordTypeToBufferType(CType(row("DataType"), Type))
        dt = ConvertBufferDataTypeToFitManaged(dt, isLong)
        Dim length As Integer = 0
        Dim precision As Integer = CType(row("NumericPrecision"), Short)
        Dim scale As Integer = CType(row("NumericScale"), Short)
        Dim codepage As Integer = dataTable.Locale.TextInfo.ANSICodePage

        Select Case dt

            ' The length cannot be zero, and the code page property must contain a valid code page.
            Case DataType.DT_STR
            Case DataType.DT_TEXT
                length = precision
                precision = 0
                scale = 0

            Case DataType.DT_WSTR
                length = precision
                codepage = 0
                scale = 0
                precision = 0

            Case DataType.DT_BYTES
                precision = 0
                scale = 0
                codepage = 0

            Case DataType.DT_NUMERIC
                length = 0
                codepage = 0

                If precision > 38 Then
                    precision = 38
                End If

                If scale > 6 Then
                    scale = 6
                End If

            Case DataType.DT_DECIMAL
                length = 0
                precision = 0
                codepage = 0

            Case Else
                length = 0
                precision = 0
                codepage = 0
                scale = 0
        End Select

        ' Set the properties of the output column.
        outColumn.Name = CStr(row("ColumnName"))
        outColumn.SetDataTypeProperties(dt, length, precision, scale, codepage)
    Next
End Sub
```

### <a name="validating-the-component"></a><span data-ttu-id="8f099-179">コンポーネントの検証</span><span class="sxs-lookup"><span data-stu-id="8f099-179">Validating the Component</span></span>
 <span data-ttu-id="8f099-180">変換元コンポーネントを検証して、出力列コレクションに定義された列が、外部データ ソースの列と一致することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f099-180">You should validate a source component and verify that the columns defined in its output column collections match the columns at the external data source.</span></span> <span data-ttu-id="8f099-181">ただし、接続状態でない場合や、サーバーへの長いラウンド トリップを避けたほうがよい場合など、外部データ ソースに対する出力列の検証が不可能なこともあります。</span><span class="sxs-lookup"><span data-stu-id="8f099-181">Sometimes, verifying the output columns against the external data source can be impossible, such as in a disconnected state, or when it is preferable to avoid lengthy round trips to the server.</span></span> <span data-ttu-id="8f099-182">このような状況でも、出力オブジェクトの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExternalMetadataColumnCollection%2A> を使用して、出力の列を検証することができます。</span><span class="sxs-lookup"><span data-stu-id="8f099-182">In these situations, the columns in the output can still be validated by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExternalMetadataColumnCollection%2A> of the output object.</span></span> <span data-ttu-id="8f099-183">詳細については、「[データ フロー コンポーネントの検証](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f099-183">For more information, see [Validating a Data Flow Component](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md).</span></span>

 <span data-ttu-id="8f099-184">このコレクションは入力オブジェクトと出力オブジェクトのどちらにも存在し、外部データ ソースの列によって作成できます。</span><span class="sxs-lookup"><span data-stu-id="8f099-184">This collection exists on both input and output objects and you can populate it with the columns from the external data source.</span></span> <span data-ttu-id="8f099-185">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーがオフラインである場合、コンポーネントが接続されていない場合、または <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> プロパティが `false` の場合に、このコレクションを使用して出力列を検証できます。</span><span class="sxs-lookup"><span data-stu-id="8f099-185">You can use this collection to validate the output columns when [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer is offline, when the component is disconnected, or when the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> property is `false`.</span></span> <span data-ttu-id="8f099-186">コレクションは、出力列の作成と同時に設定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f099-186">The collection should be first populated at the same time that the output columns are created.</span></span> <span data-ttu-id="8f099-187">外部メタデータ列は初期状態で出力列と一致しているため、コレクションに外部メタデータ列を追加するのは比較的簡単です。</span><span class="sxs-lookup"><span data-stu-id="8f099-187">Adding external metadata columns to the collection is relatively easy because the external metadata column should initially match the output column.</span></span> <span data-ttu-id="8f099-188">列のデータ型プロパティは、あらかじめ正しく設定されている必要があります。また、プロパティは <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100> オブジェクトに直接コピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="8f099-188">The data type properties of the column should have already been set correctly, and the properties can be copied directly to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100> object.</span></span>

 <span data-ttu-id="8f099-189">次のコード例は、新しく作成された出力列に基づく外部メタデータ列を追加します。</span><span class="sxs-lookup"><span data-stu-id="8f099-189">The following sample code adds an external metadata column that is based on a newly created output column.</span></span> <span data-ttu-id="8f099-190">出力列はあらかじめ作成されているものとします。</span><span class="sxs-lookup"><span data-stu-id="8f099-190">It assumes that the output column has already been created.</span></span>

```csharp
private void CreateExternalMetaDataColumn(IDTSOutput100 output, IDTSOutputColumn100 outputColumn)
{

    // Set the properties of the external metadata column.
    IDTSExternalMetadataColumn100 externalColumn = output.ExternalMetadataColumnCollection.New();
    externalColumn.Name = outputColumn.Name;
    externalColumn.Precision = outputColumn.Precision;
    externalColumn.Length = outputColumn.Length;
    externalColumn.DataType = outputColumn.DataType;
    externalColumn.Scale = outputColumn.Scale;

    // Map the external column to the output column.
    outputColumn.ExternalMetadataColumnID = externalColumn.ID;

}
```

```vb
Private Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumn As IDTSOutputColumn100)

        ' Set the properties of the external metadata column.
        Dim externalColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New()
        externalColumn.Name = outputColumn.Name
        externalColumn.Precision = outputColumn.Precision
        externalColumn.Length = outputColumn.Length
        externalColumn.DataType = outputColumn.DataType
        externalColumn.Scale = outputColumn.Scale

        ' Map the external column to the output column.
        outputColumn.ExternalMetadataColumnID = externalColumn.ID

    End Sub
```

## <a name="run-time"></a><span data-ttu-id="8f099-191">実行時間</span><span class="sxs-lookup"><span data-stu-id="8f099-191">Run Time</span></span>
 <span data-ttu-id="8f099-192">実行中、コンポーネントは、データ フロー タスクによって作成され、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> でコンポーネントに渡される出力バッファーに行を追加します。</span><span class="sxs-lookup"><span data-stu-id="8f099-192">During execution, components add rows to output buffers that are created by the data flow task and provided to the component in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.</span></span> <span data-ttu-id="8f099-193">変換元コンポーネントでこのメソッドが呼び出されると、メソッドは、下流コンポーネントに接続されたコンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> ごとに出力バッファーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="8f099-193">Called once for source components, the method receives an output buffer for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the component that is connected to a downstream component.</span></span>

### <a name="locating-columns-in-the-buffer"></a><span data-ttu-id="8f099-194">バッファー内の列の検索</span><span class="sxs-lookup"><span data-stu-id="8f099-194">Locating Columns in the Buffer</span></span>
 <span data-ttu-id="8f099-195">コンポーネントの出力バッファーには、このコンポーネントで定義されている列、および下流コンポーネントの出力に追加されたすべての列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8f099-195">The output buffer for a component contains the columns defined by the component and any columns added to the output of a downstream component.</span></span> <span data-ttu-id="8f099-196">たとえば、変換元コンポーネントの出力に 3 つの列があり、次のコンポーネントでもう 1 つ出力列を追加している場合、変換元コンポーネントによって提供された出力バッファーには 4 つの列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8f099-196">For example, if a source component provides three columns in its output, and the next component adds a fourth output column, the output buffer provided for use by the source component contains these four columns.</span></span>

 <span data-ttu-id="8f099-197">バッファー行の列の順序は、出力列コレクション内の出力列のインデックスでは定義されません。</span><span class="sxs-lookup"><span data-stu-id="8f099-197">The order of the columns in a buffer row is not defined by the index of the output column in the output column collection.</span></span> <span data-ttu-id="8f099-198">バッファー行で出力列を正確に検索するには、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSBufferManagerClass.FindColumnByLineageID%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> メソッドを使用するしか方法がありません。</span><span class="sxs-lookup"><span data-stu-id="8f099-198">An output column can only be accurately located in a buffer row by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSBufferManagerClass.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.</span></span> <span data-ttu-id="8f099-199">このメソッドは、指定されたバッファー内で指定された系列 ID の列を検索し、行内の位置を返します。</span><span class="sxs-lookup"><span data-stu-id="8f099-199">This method locates the column with the specified lineage ID in the specified buffer, and returns its location in the row.</span></span> <span data-ttu-id="8f099-200">出力列のインデックスは、通常、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> メソッド内で検索され、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> で使用するために保存されます。</span><span class="sxs-lookup"><span data-stu-id="8f099-200">The indexes of the output columns are typically located in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, and stored for use during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.</span></span>

 <span data-ttu-id="8f099-201">次のコード例は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> を呼び出して出力バッファー内の出力列の位置を検索し、内部構造に保存します。</span><span class="sxs-lookup"><span data-stu-id="8f099-201">The following code example finds the location of the output columns in the output buffer during a call to <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>, and stores them in an internal structure.</span></span> <span data-ttu-id="8f099-202">列の名前もこの構造に保存され、このトピックの次のセクションで、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> メソッドのコード例で使用されています。</span><span class="sxs-lookup"><span data-stu-id="8f099-202">The name of the column is also stored in the structure and is used in the code example for the  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method in the next section of this topic.</span></span>

```csharp
ArrayList columnInformation;

private struct ColumnInfo
{
    public int BufferColumnIndex;
    public string ColumnName;
}

public override void PreExecute()
{
    this.columnInformation = new ArrayList();
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

    foreach (IDTSOutputColumn100 col in output.OutputColumnCollection)
    {
        ColumnInfo ci = new ColumnInfo();
        ci.BufferColumnIndex = BufferManager.FindColumnByLineageID(output.Buffer, col.LineageID);
        ci.ColumnName = col.Name;
        columnInformation.Add(ci);
    }
}
```

```vb
Public Overrides Sub PreExecute()

    Me.columnInformation = New ArrayList()
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

    For Each col As IDTSOutputColumn100 In output.OutputColumnCollection

        Dim ci As ColumnInfo = New ColumnInfo()
        ci.BufferColumnIndex = BufferManager.FindColumnByLineageID(output.Buffer, col.LineageID)
        ci.ColumnName = col.Name
        columnInformation.Add(ci)
    Next
End Sub
```

### <a name="processing-rows"></a><span data-ttu-id="8f099-203">行の処理</span><span class="sxs-lookup"><span data-stu-id="8f099-203">Processing Rows</span></span>
 <span data-ttu-id="8f099-204">出力バッファーに行を追加するには、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> メソッドを呼び出します。このメソッドは、新しいバッファー行を作成して、列に空の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="8f099-204">Rows are added to the output buffer by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> method, which creates a new buffer row with empty values in its columns.</span></span> <span data-ttu-id="8f099-205">次に、コンポーネントは個々の列に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8f099-205">The component then assigns values to the individual columns.</span></span> <span data-ttu-id="8f099-206">コンポーネントに提供される出力バッファーは、データ フロー タスクによって作成され、監視されます。</span><span class="sxs-lookup"><span data-stu-id="8f099-206">The output buffers provided to a component are created and monitored by the data flow task.</span></span> <span data-ttu-id="8f099-207">バッファーがいっぱいになると、バッファーの行が次のコンポーネントに移動します。</span><span class="sxs-lookup"><span data-stu-id="8f099-207">As they become full, the rows in the buffer are moved to the next component.</span></span> <span data-ttu-id="8f099-208">コンポーネント開発者は、データ フロー タスクによる行の移動を意識することがなく、出力バッファーでは <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RowCount%2A> プロパティは常に 0 のままであるため、行の一部が次のコンポーネントに送られるタイミングを確認する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="8f099-208">There is no way to determine when a batch of rows has been sent to the next component because the movement of rows by the data flow task is transparent to the component developer, and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RowCount%2A> property is always zero on output buffers.</span></span> <span data-ttu-id="8f099-209">変換元コンポーネントは、出力バッファーに対する行の追加を終了すると、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> メソッドを呼び出し、バッファー内の残りの行を次のコンポーネントに渡して、追加が終了したことをデータ フロー タスクに通知します。</span><span class="sxs-lookup"><span data-stu-id="8f099-209">When a source component is finished adding rows to its output buffer, it notifies the data flow task by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>, and the remaining rows in the buffer are passed to the next component.</span></span>

 <span data-ttu-id="8f099-210">変換元コンポーネントが行を外部データ ソースから読み込んでいる間に、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> メソッドを呼び出して "Rows read" または "BLOB bytes read" パフォーマンス カウンターを更新することができます。</span><span class="sxs-lookup"><span data-stu-id="8f099-210">While the source component reads rows from the external data source, you may want to update the "Rows read" or "BLOB bytes read" performance counters by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> method.</span></span> <span data-ttu-id="8f099-211">これらのパフォーマンス カウンターの詳細については、「 [パフォーマンス カウンター](../performance/performance-counters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f099-211">For more information, see [Performance Counters](../performance/performance-counters.md).</span></span>

 <span data-ttu-id="8f099-212">次のコード例は、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> で出力バッファーに行を追加します。</span><span class="sxs-lookup"><span data-stu-id="8f099-212">The following code example shows a component that adds rows to an output buffer in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.</span></span> <span data-ttu-id="8f099-213">バッファー内の出力列のインデックスは、先のコード例にある <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 内で検索したものを使用します。</span><span class="sxs-lookup"><span data-stu-id="8f099-213">The indexes of the output columns in the buffer were located using <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> in the previous code example.</span></span>

```csharp
public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
{
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
    PipelineBuffer buffer = buffers[0];

    SqlDataReader dataReader = sqlCommand.ExecuteReader();

    // Loop over the rows in the DataReader, 
    // and add them to the output buffer.
    while (dataReader.Read())
    {
        // Add a row to the output buffer.
        buffer.AddRow();

        for (int x = 0; x < columnInformation.Count; x++)
        {
            ColumnInfo ci = (ColumnInfo)columnInformation[x];
            int ordinal = dataReader.GetOrdinal(ci.ColumnName);

            if (dataReader.IsDBNull(ordinal))
                buffer.SetNull(ci.BufferColumnIndex);
            else
            {
                buffer[ci.BufferColumnIndex] = dataReader[ci.ColumnName];
            }
        }
    }
    buffer.SetEndOfRowset();
}
```

```vb
Public Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())

    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
    Dim buffer As PipelineBuffer = buffers(0)

    Dim dataReader As SqlDataReader = sqlCommand.ExecuteReader()

    ' Loop over the rows in the DataReader, 
    ' and add them to the output buffer.
    While (dataReader.Read())

        ' Add a row to the output buffer.
        buffer.AddRow()

        For x As Integer = 0 To columnInformation.Count

            Dim ci As ColumnInfo = CType(columnInformation(x), ColumnInfo)

            Dim ordinal As Integer = dataReader.GetOrdinal(ci.ColumnName)

            If (dataReader.IsDBNull(ordinal)) Then
                buffer.SetNull(ci.BufferColumnIndex)
            Else
                buffer(ci.BufferColumnIndex) = dataReader(ci.ColumnName)

            End If
        Next

    End While

    buffer.SetEndOfRowset()
End Sub
```

## <a name="sample"></a><span data-ttu-id="8f099-214">サンプル</span><span class="sxs-lookup"><span data-stu-id="8f099-214">Sample</span></span>
 <span data-ttu-id="8f099-215">次の例は、ファイル接続マネージャーを使用して、ファイルのバイナリ コンテンツをデータ フローに読み込む、簡単な変換元コンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="8f099-215">The following sample shows a simple source component that uses a File connection manager to load the binary contents of files into the data flow.</span></span> <span data-ttu-id="8f099-216">ただし、この例ではここで説明したメソッドや機能のすべてが使われているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="8f099-216">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="8f099-217">変換元コンポーネントが必ずオーバーライドしなければならない重要なメソッドは示していますが、デザイン時の検証のためのコードは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="8f099-217">It demonstrates the important methods that every custom source component must override, but does not contain code for design-time validation.</span></span>

```csharp
using System;
using System.IO;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

namespace BlobSrc
{
  [DtsPipelineComponent(DisplayName = "BLOB Inserter Source", Description = "Inserts files into the data flow as BLOBs")]
  public class BlobSrc : PipelineComponent
  {
    IDTSConnectionManager100 m_ConnMgr;
    int m_FileNameColumnIndex = -1;
    int m_FileBlobColumnIndex = -1;

    public override void ProvideComponentProperties()
    {
      IDTSOutput100 output = ComponentMetaData.OutputCollection.New();
      output.Name = "BLOB File Inserter Output";

      IDTSOutputColumn100 column = output.OutputColumnCollection.New();
      column.Name = "FileName";
      column.SetDataTypeProperties(DataType.DT_WSTR, 256, 0, 0, 0);

      column = output.OutputColumnCollection.New();
      column.Name = "FileBLOB";
      column.SetDataTypeProperties(DataType.DT_IMAGE, 0, 0, 0, 0);

      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection.New();
      conn.Name = "FileConnection";
    }

    public override void AcquireConnections(object transaction)
    {
      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection[0];
      m_ConnMgr = conn.ConnectionManager;
    }

    public override void ReleaseConnections()
    {
      m_ConnMgr = null;
    }

    public override void PreExecute()
    {
      IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

      m_FileNameColumnIndex = (int)BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[0].LineageID);
      m_FileBlobColumnIndex = (int)BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[1].LineageID);
    }

    public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
    {
      string strFileName = (string)m_ConnMgr.AcquireConnection(null);

      while (strFileName != null)
      {
        buffers[0].AddRow();

        buffers[0].SetString(m_FileNameColumnIndex, strFileName);

        FileInfo fileInfo = new FileInfo(strFileName);
        byte[] fileData = new byte[fileInfo.Length];
        FileStream fs = new FileStream(strFileName, FileMode.Open, FileAccess.Read, FileShare.Read);
        fs.Read(fileData, 0, fileData.Length);

        buffers[0].AddBlobData(m_FileBlobColumnIndex, fileData);

        strFileName = (string)m_ConnMgr.AcquireConnection(null);
      }

      buffers[0].SetEndOfRowset();
    }
  }
}
```

```vb
Imports System 
Imports System.IO 
Imports Microsoft.SqlServer.Dts.Pipeline 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper 
Namespace BlobSrc 

 <DtsPipelineComponent(DisplayName="BLOB Inserter Source", Description="Inserts files into the data flow as BLOBs")> _ 
 Public Class BlobSrc 
 Inherits PipelineComponent 
   Private m_ConnMgr As IDTSConnectionManager100 
   Private m_FileNameColumnIndex As Integer = -1 
   Private m_FileBlobColumnIndex As Integer = -1 

   Public  Overrides Sub ProvideComponentProperties() 
     Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New 
     output.Name = "BLOB File Inserter Output" 
     Dim column As IDTSOutputColumn100 = output.OutputColumnCollection.New 
     column.Name = "FileName" 
     column.SetDataTypeProperties(DataType.DT_WSTR, 256, 0, 0, 0) 
     column = output.OutputColumnCollection.New 
     column.Name = "FileBLOB" 
     column.SetDataTypeProperties(DataType.DT_IMAGE, 0, 0, 0, 0) 
     Dim conn As IDTSRuntimeConnection90 = ComponentMetaData.RuntimeConnectionCollection.New 
     conn.Name = "FileConnection" 
   End Sub 

   Public  Overrides Sub AcquireConnections(ByVal transaction As Object) 
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection(0) 
     m_ConnMgr = conn.ConnectionManager 
   End Sub 

   Public  Overrides Sub ReleaseConnections() 
     m_ConnMgr = Nothing 
   End Sub 

   Public  Overrides Sub PreExecute() 
     Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0) 
     m_FileNameColumnIndex = CType(BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(0).LineageID), Integer) 
     m_FileBlobColumnIndex = CType(BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(1).LineageID), Integer) 
   End Sub 

   Public  Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer()) 
     Dim strFileName As String = CType(m_ConnMgr.AcquireConnection(Nothing), String) 
     While Not (strFileName Is Nothing) 
       buffers(0).AddRow 
       buffers(0).SetString(m_FileNameColumnIndex, strFileName) 
       Dim fileInfo As FileInfo = New FileInfo(strFileName) 
       Dim fileData(fileInfo.Length) As Byte 
       Dim fs As FileStream = New FileStream(strFileName, FileMode.Open, FileAccess.Read, FileShare.Read) 
       fs.Read(fileData, 0, fileData.Length) 
       buffers(0).AddBlobData(m_FileBlobColumnIndex, fileData) 
       strFileName = CType(m_ConnMgr.AcquireConnection(Nothing), String) 
     End While 
     buffers(0).SetEndOfRowset 
   End Sub 
 End Class 
End Namespace
```

<span data-ttu-id="8f099-218">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="8f099-218">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="8f099-219">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f099-219">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="8f099-220">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="8f099-220">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="8f099-221">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="8f099-221">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f099-222">参照</span><span class="sxs-lookup"><span data-stu-id="8f099-222">See Also</span></span>
 <span data-ttu-id="8f099-223">[カスタム変換先コンポーネントの開発](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)[スクリプトコンポーネントを使用したソースの作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)</span><span class="sxs-lookup"><span data-stu-id="8f099-223">[Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) [Creating a Source with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)</span></span>


