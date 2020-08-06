---
title: スクリプト コンポーネントのオブジェクト モデルについて | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a11556b00efc5749e8ddb895712d6c61f2459d8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640154"
---
# <a name="understanding-the-script-component-object-model"></a><span data-ttu-id="97315-102">スクリプト コンポーネントのオブジェクト モデルについて</span><span class="sxs-lookup"><span data-stu-id="97315-102">Understanding the Script Component Object Model</span></span>
  <span data-ttu-id="97315-103">「スクリプトコンポーネントのコーディングおよびデバッグ」 (../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md、スクリプトコンポーネントプロジェクトには、次の3つのプロジェクト項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="97315-103">As discussed in [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md, the Script component project contains three project items:</span></span>

1.  <span data-ttu-id="97315-104">`ScriptMain` アイテム。`ScriptMain` クラスを含み、ここにカスタム コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="97315-104">The `ScriptMain` item, which contains the `ScriptMain` class in which you write your code.</span></span> <span data-ttu-id="97315-105">`ScriptMain` クラスは `UserComponent` クラスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="97315-105">The `ScriptMain` class inherits from the `UserComponent` class.</span></span>

2.  <span data-ttu-id="97315-106">`ComponentWrapper` アイテム。`UserComponent` クラスを含みます。これは <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> のインスタンスで、データの処理やパッケージとのやり取りで使用するメソッドとプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97315-106">The `ComponentWrapper` item, which contains the `UserComponent` class, an instance of <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> that contains the methods and properties that you will use to process data and to interact with the package.</span></span> <span data-ttu-id="97315-107">`ComponentWrapper` アイテムには、`Connections` や `Variables` の各コレクション クラスも含まれています。</span><span class="sxs-lookup"><span data-stu-id="97315-107">The `ComponentWrapper` item also contains `Connections` and `Variables` collection classes.</span></span>

3.  <span data-ttu-id="97315-108">`BufferWrapper` アイテム。各入力および各出力に対して <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> から継承されるクラス、および各列に対する型指定されたプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97315-108">The `BufferWrapper` item, which contains classes that inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> for each input and output, and typed properties for each column.</span></span>

 <span data-ttu-id="97315-109">`ScriptMain` アイテムにコードを記述する際には、このトピックで説明するオブジェクト、メソッド、およびプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="97315-109">As you write your code in the `ScriptMain` item, you will use the objects, methods, and properties discussed in this topic.</span></span> <span data-ttu-id="97315-110">ここで一覧されているすべてのメソッドを各コンポーネントが使用するわけではありませんが、使用される場合は、ここで示した順序で使用されます。</span><span class="sxs-lookup"><span data-stu-id="97315-110">Each component will not use all the methods listed here; however, when used, they are used in the sequence shown.</span></span>

 <span data-ttu-id="97315-111">基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> には、ここで説明しているメソッドのコードは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="97315-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class does not contain any implementation code for the methods discussed in this topic.</span></span> <span data-ttu-id="97315-112">したがって、メソッド独自の実装に基本クラスの実装の呼び出しを追加する必要はありませんが、追加した場合でも問題は生じません。</span><span class="sxs-lookup"><span data-stu-id="97315-112">Therefore it is unnecessary, but harmless, to add a call to the base class implementation to your own implementation of the method.</span></span>

 <span data-ttu-id="97315-113">特定の種類のスクリプト コンポーネントで、これらのクラスのメソッドおよびプロパティを使用する方法については、セクション「[その他のスクリプト コンポーネントの例](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97315-113">For information about how to use the methods and properties of these classes in a particular type of Script component, see the section [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span> <span data-ttu-id="97315-114">サンプルについてのトピックでは、完全なコード例も示します。</span><span class="sxs-lookup"><span data-stu-id="97315-114">The example topics also contain complete code samples.</span></span>

## <a name="acquireconnections-method"></a><span data-ttu-id="97315-115">AcquireConnections メソッド</span><span class="sxs-lookup"><span data-stu-id="97315-115">AcquireConnections Method</span></span>
 <span data-ttu-id="97315-116">通常、変換元および変換先は外部データ ソースに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97315-116">Sources and destinations generally must connect to an external data source.</span></span> <span data-ttu-id="97315-117">基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドして、適切な接続マネージャーから、接続または接続情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="97315-117">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class to retrieve the connection or the connection information from the appropriate connection manager.</span></span>

 <span data-ttu-id="97315-118">次の例は、ADO.NET 接続マネージャーから `System.Data.SqlClient.SqlConnection` を返します。</span><span class="sxs-lookup"><span data-stu-id="97315-118">The following example returns a `System.Data.SqlClient.SqlConnection` from an ADO.NET connection manager.</span></span>

```vb
Dim connMgr As IDTSConnectionManager100
Dim sqlConn As SqlConnection

Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    connMgr = Me.Connections.MyADONETConnection
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

End Sub
```

 <span data-ttu-id="97315-119">次の例は、フラット ファイル接続マネージャーから完全パスおよびファイル名を返し、`System.IO.StreamReader` を使用してこのファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="97315-119">The following example returns a complete path and file name from a Flat File Connection Manager, and then opens the file by using a `System.IO.StreamReader`.</span></span>

```vb
Private textReader As StreamReader
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    Dim connMgr As IDTSConnectionManager100 = _
        Me.Connections.MyFlatFileSrcConnectionManager
    Dim exportedAddressFile As String = _
        CType(connMgr.AcquireConnection(Nothing), String)
    textReader = New StreamReader(exportedAddressFile)

End Sub
```

## <a name="preexecute-method"></a><span data-ttu-id="97315-120">PreExecute メソッド</span><span class="sxs-lookup"><span data-stu-id="97315-120">PreExecute Method</span></span>
 <span data-ttu-id="97315-121">データの行の処理を開始する前に 1 回だけ実行する必要のある処理がある場合は、基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="97315-121">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class whenever you have processing that you must perform one time only before you start processing rows of data.</span></span> <span data-ttu-id="97315-122">たとえば、データの各行をデータ ソースに挿入するために変換先が使用するパラメーター化コマンドを、変換先に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="97315-122">For example, in a destination, you may want to configure the parameterized command that the destination will use to insert each row of data into the data source.</span></span>

```vb
    Dim sqlConn As SqlConnection
    Dim sqlCmd As SqlCommand
    Dim sqlParam As SqlParameter
...
    Public Overrides Sub PreExecute()

        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _
            "VALUES(@addressid, @city)", sqlConn)
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)
        sqlCmd.Parameters.Add(sqlParam)
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)
        sqlCmd.Parameters.Add(sqlParam)

    End Sub
```

```csharp
SqlConnection sqlConn; 
SqlCommand sqlCmd; 
SqlParameter sqlParam; 

public override void PreExecute() 
{ 

    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn); 
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int); 
    sqlCmd.Parameters.Add(sqlParam); 
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30); 
    sqlCmd.Parameters.Add(sqlParam); 

}
```

## <a name="processing-inputs-and-outputs"></a><span data-ttu-id="97315-123">入力および出力の処理</span><span class="sxs-lookup"><span data-stu-id="97315-123">Processing Inputs and Outputs</span></span>

### <a name="processing-inputs"></a><span data-ttu-id="97315-124">入力の処理</span><span class="sxs-lookup"><span data-stu-id="97315-124">Processing Inputs</span></span>
 <span data-ttu-id="97315-125">変換または変換先として構成されたスクリプト コンポーネントには、1 つの入力があります。</span><span class="sxs-lookup"><span data-stu-id="97315-125">Script components that are configured as transformations or destinations have one input.</span></span>

#### <a name="what-the-bufferwrapper-project-item-provides"></a><span data-ttu-id="97315-126">プロジェクト アイテム BufferWrapper が提供する機能</span><span class="sxs-lookup"><span data-stu-id="97315-126">What the BufferWrapper Project Item Provides</span></span>
 <span data-ttu-id="97315-127">構成したコンポーネントの入力ごとに、プロジェクト アイテム `BufferWrapper` には、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> から派生した、入力と同じ名前のクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="97315-127">For each input that you have configured, the `BufferWrapper` project item contains a class that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> and has the same name as the input.</span></span> <span data-ttu-id="97315-128">各入力バッファー クラスには、次のプロパティ、関数、およびメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97315-128">Each input buffer class contains the following properties, functions, and methods:</span></span>

-   <span data-ttu-id="97315-129">選択された各入力列の、型指定された名前付きのアクセサー プロパティ。</span><span class="sxs-lookup"><span data-stu-id="97315-129">Named, typed accessor properties for each selected input column.</span></span> <span data-ttu-id="97315-130">これらのプロパティが読み取り専用か読み取り/書き込み可能かどうかは、 **[スクリプト変換エディター]** の **[入力列]** ページで、列に対して指定され **[使用法の種類]** によって決まります。</span><span class="sxs-lookup"><span data-stu-id="97315-130">These properties are read-only or read/write depending on the **Usage Type** specified for the column on the **Input Columns** page of the **Script Transformation Editor**.</span></span>

-   <span data-ttu-id="97315-131">選択された各入力列の **\<column>_IsNull** プロパティ。</span><span class="sxs-lookup"><span data-stu-id="97315-131">A **\<column>_IsNull** property for each selected input column.</span></span> <span data-ttu-id="97315-132">このプロパティが読み取り専用か読み取り/書き込み可能かどうかも、列に対して指定された **[使用法の種類]** によって決まります。</span><span class="sxs-lookup"><span data-stu-id="97315-132">This property is also read-only or read/write depending on the **Usage Type** specified for the column.</span></span>

-   <span data-ttu-id="97315-133">設定された各出力の **DirectRowTo\<outputbuffer>** メソッド。</span><span class="sxs-lookup"><span data-stu-id="97315-133">A **DirectRowTo\<outputbuffer>** method for each configured output.</span></span> <span data-ttu-id="97315-134">行をフィルター選択して、同じ `ExclusionGroup` 内の複数の出力のいずれかに行を出力する場合、このメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="97315-134">You will use these methods when filtering rows to one of several outputs in the same `ExclusionGroup`.</span></span>

-   <span data-ttu-id="97315-135">次の入力行を取得するための `NextRow` 関数、およびデータの最後のバッファーが処理されたかどうかを確認するための `EndOfRowset` 関数。</span><span class="sxs-lookup"><span data-stu-id="97315-135">A `NextRow` function to get the next input row, and an `EndOfRowset` function to determine whether the last buffer of data has been processed.</span></span> <span data-ttu-id="97315-136">通常、基本クラス `UserComponent` に実装された入力処理メソッドを使用する場合、この関数は必要はありません。</span><span class="sxs-lookup"><span data-stu-id="97315-136">You typically do not need these functions when you use the input processing methods implemented in the `UserComponent` base class.</span></span> <span data-ttu-id="97315-137">次のセクションでは、基本クラス `UserComponent` について詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="97315-137">The next section provides more information about the `UserComponent` base class.</span></span>

#### <a name="what-the-componentwrapper-project-item-provides"></a><span data-ttu-id="97315-138">プロジェクト アイテム ComponentWrapper が提供する機能</span><span class="sxs-lookup"><span data-stu-id="97315-138">What the ComponentWrapper Project Item Provides</span></span>
 <span data-ttu-id="97315-139">プロジェクト アイテム ComponentWrapper には、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> から派生する `UserComponent` という名前のクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="97315-139">The ComponentWrapper project item contains a class named `UserComponent` that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>.</span></span> <span data-ttu-id="97315-140">また、カスタム コードを記述する `ScriptMain` クラスは、`UserComponent` から派生します。</span><span class="sxs-lookup"><span data-stu-id="97315-140">The `ScriptMain` class in which you write your custom code derives in turn from `UserComponent`.</span></span> <span data-ttu-id="97315-141">`UserComponent` クラスには次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97315-141">The `UserComponent` class contains the following methods:</span></span>

-   <span data-ttu-id="97315-142">`ProcessInput` メソッドをオーバーライドして実装したメソッド。</span><span class="sxs-lookup"><span data-stu-id="97315-142">An overridden implementation of the `ProcessInput` method.</span></span> <span data-ttu-id="97315-143">これは、データ フロー エンジンが実行時に `PreExecute` メソッドの次に呼び出すメソッドで、繰り返し呼び出される場合があります。</span><span class="sxs-lookup"><span data-stu-id="97315-143">This is the method that the data flow engine calls next at run time after the `PreExecute` method, and it may be called multiple times.</span></span> <span data-ttu-id="97315-144">`ProcessInput`\*\* \<inputbuffer> _ProcessInput\*\*メソッドに処理を渡します。</span><span class="sxs-lookup"><span data-stu-id="97315-144">`ProcessInput` hands off processing to the **\<inputbuffer>_ProcessInput** method.</span></span> <span data-ttu-id="97315-145">次に `ProcessInput` メソッドは入力バッファーが末尾に達しているかどうかを確認し、達している場合は、オーバーライド可能な `FinishOutputs` メソッドと private メソッド `MarkOutputsAsFinished` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="97315-145">Then the `ProcessInput` method checks for the end of the input buffer and, if the end of the buffer has been reached, calls the overridable `FinishOutputs` method and the private `MarkOutputsAsFinished` method.</span></span> <span data-ttu-id="97315-146">`MarkOutputsAsFinished` メソッドは、次に最後の出力バッファーの `SetEndOfRowset` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="97315-146">The `MarkOutputsAsFinished` method then calls `SetEndOfRowset` on the last output buffer.</span></span>

-   <span data-ttu-id="97315-147">**\<inputbuffer>_ProcessInput** メソッドのオーバーライド可能な実装。</span><span class="sxs-lookup"><span data-stu-id="97315-147">An overridable implementation of the **\<inputbuffer>_ProcessInput** method.</span></span> <span data-ttu-id="97315-148">この既定の実装では、単に各入力行をループし、 **\<inputbuffer>_ProcessInputRow** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="97315-148">This default implementation simply loops through each input row and calls **\<inputbuffer>_ProcessInputRow**.</span></span>

-   <span data-ttu-id="97315-149">**\<inputbuffer>_ProcessInputRow** メソッドのオーバーライド可能な実装。</span><span class="sxs-lookup"><span data-stu-id="97315-149">An overridable implementation of the **\<inputbuffer>_ProcessInputRow** method.</span></span> <span data-ttu-id="97315-150">既定の実装では、空のままです。</span><span class="sxs-lookup"><span data-stu-id="97315-150">The default implementation is empty.</span></span> <span data-ttu-id="97315-151">このメソッドは、カスタム データ処理コードを記述するために、通常はオーバーライドして使用します。</span><span class="sxs-lookup"><span data-stu-id="97315-151">This is the method that you will normally override to write your custom data processing code.</span></span>

#### <a name="what-your-custom-code-should-do"></a><span data-ttu-id="97315-152">カスタム コードとして組み込むべき機能</span><span class="sxs-lookup"><span data-stu-id="97315-152">What Your Custom Code Should Do</span></span>
 <span data-ttu-id="97315-153">`ScriptMain` クラスの入力を処理するには、次のメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="97315-153">You can use the following methods to process input in the `ScriptMain` class:</span></span>

-   <span data-ttu-id="97315-154">入力行が渡されるたびにそのデータを処理するには、 **\<inputbuffer>_ProcessInputRow** をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="97315-154">Override **\<inputbuffer>_ProcessInputRow** to process the data in each input row as it passes through.</span></span>

-   <span data-ttu-id="97315-155">入力行をループするときに追加の処理を行う必要がある場合にのみ、 **\<inputbuffer>_ProcessInput** をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="97315-155">Override **\<inputbuffer>_ProcessInput** only if you have to do something additional while looping through input rows.</span></span> <span data-ttu-id="97315-156">(たとえば、 `EndOfRowset` すべての行が処理された後に、他のアクションを実行するためにをテストする必要があります)。行の処理を実行するには、 \*\* \<inputbuffer> _ProcessInputRow\*\*を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="97315-156">(For example, you have to test for `EndOfRowset` to take some other action after all rows have been processed.) Call **\<inputbuffer>_ProcessInputRow** to perform the row processing.</span></span>

-   <span data-ttu-id="97315-157">出力を閉じる前に、出力に対して何らかの処理を行う場合は、`FinishOutputs` をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="97315-157">Override `FinishOutputs` if you have to do something to the outputs before they are closed.</span></span>

 <span data-ttu-id="97315-158">`ProcessInput` メソッドは、これらのメソッドが適切な時点で確実に呼び出されるようにするものです。</span><span class="sxs-lookup"><span data-stu-id="97315-158">The `ProcessInput` method ensures that these methods are called at the appropriate times.</span></span>

### <a name="processing-outputs"></a><span data-ttu-id="97315-159">出力の処理</span><span class="sxs-lookup"><span data-stu-id="97315-159">Processing Outputs</span></span>
 <span data-ttu-id="97315-160">変換元または変換として構成されたスクリプト コンポーネントには、1 つ以上の出力があります。</span><span class="sxs-lookup"><span data-stu-id="97315-160">Script components configured as sources or transformations have one or more outputs.</span></span>

#### <a name="what-the-bufferwrapper-project-item-provides"></a><span data-ttu-id="97315-161">プロジェクト アイテム BufferWrapper が提供する機能</span><span class="sxs-lookup"><span data-stu-id="97315-161">What the BufferWrapper Project Item Provides</span></span>
 <span data-ttu-id="97315-162">構成したコンポーネントの出力ごとに、プロジェクト アイテム BufferWrapper には、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> から派生した、出力と同じ名前のクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="97315-162">For each output that you have configured, the BufferWrapper project item contains a class that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> and has the same name as the output.</span></span> <span data-ttu-id="97315-163">各出力バッファー クラスには、次のプロパティおよびメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97315-163">Each input buffer class contains the following properties and methods:</span></span>

-   <span data-ttu-id="97315-164">各出力列の、名前付きで型指定された、書き込み専用のアクセサー プロパティ。</span><span class="sxs-lookup"><span data-stu-id="97315-164">Named, typed, write-only accessor properties for each output column.</span></span>

-   <span data-ttu-id="97315-165">列の値をに設定するために使用できる、選択した各出力列の書き込み専用の\*\* \<column> _IsNull\*\*プロパティ `null` です。</span><span class="sxs-lookup"><span data-stu-id="97315-165">A write-only **\<column>_IsNull** property for each selected output column that you can use to set the column value to `null`.</span></span>

-   <span data-ttu-id="97315-166">空の新しい行を出力バッファーに追加するための `AddRow` メソッド。</span><span class="sxs-lookup"><span data-stu-id="97315-166">An `AddRow` method to add an empty new row to the output buffer.</span></span>

-   <span data-ttu-id="97315-167">データ フロー エンジンに対し、これ以上データのバッファーがないことを知らせるための `SetEndOfRowset` メソッド。</span><span class="sxs-lookup"><span data-stu-id="97315-167">A `SetEndOfRowset` method to let the data flow engine know that no more buffers of data are expected.</span></span> <span data-ttu-id="97315-168">現在のバッファーが、データの最後のバッファーであるかどうかを確認するための `EndOfRowset` 関数もあります。</span><span class="sxs-lookup"><span data-stu-id="97315-168">There is also an `EndOfRowset` function to determine whether the current buffer is the last buffer of data.</span></span> <span data-ttu-id="97315-169">通常、基本クラス `UserComponent` に実装された出力処理メソッドを使用する場合、この関数は必要はありません。</span><span class="sxs-lookup"><span data-stu-id="97315-169">You generally do not need these functions when you use the input processing methods implemented in the `UserComponent` base class.</span></span>

#### <a name="what-the-componentwrapper-project-item-provides"></a><span data-ttu-id="97315-170">プロジェクト アイテム ComponentWrapper が提供する機能</span><span class="sxs-lookup"><span data-stu-id="97315-170">What the ComponentWrapper Project Item Provides</span></span>
 <span data-ttu-id="97315-171">プロジェクト アイテム ComponentWrapper には、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> から派生する `UserComponent` という名前のクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="97315-171">The ComponentWrapper project item contains a class named `UserComponent` that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>.</span></span> <span data-ttu-id="97315-172">また、カスタム コードを記述する `ScriptMain` クラスは、`UserComponent` から派生します。</span><span class="sxs-lookup"><span data-stu-id="97315-172">The `ScriptMain` class in which you write your custom code derives in turn from `UserComponent`.</span></span> <span data-ttu-id="97315-173">`UserComponent` クラスには次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97315-173">The `UserComponent` class contains the following methods:</span></span>

-   <span data-ttu-id="97315-174">`PrimeOutput` メソッドをオーバーライドして実装したメソッド。</span><span class="sxs-lookup"><span data-stu-id="97315-174">An overridden implementation of the `PrimeOutput` method.</span></span> <span data-ttu-id="97315-175">実行時、データ フロー エンジンは、このメソッドを `ProcessInput` の前に 1 回だけ呼び出します。</span><span class="sxs-lookup"><span data-stu-id="97315-175">The data flow engine calls this method before `ProcessInput` at run time, and it is only called one time.</span></span> <span data-ttu-id="97315-176">`PrimeOutput` は `CreateNewOutputRows` メソッドに処理を渡します。</span><span class="sxs-lookup"><span data-stu-id="97315-176">`PrimeOutput` hands off processing to the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="97315-177">コンポーネントが変換元の場合 (つまりコンポーネントに入力がない場合)、`PrimeOutput` はオーバーライド可能な `FinishOutputs` メソッドと private メソッド `MarkOutputsAsFinished` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="97315-177">Then, if the component is a source (that is, the component has no inputs), `PrimeOutput` calls the overridable `FinishOutputs` method and the private `MarkOutputsAsFinished` method.</span></span> <span data-ttu-id="97315-178">`MarkOutputsAsFinished` メソッドは、最後の出力バッファーの `SetEndOfRowset` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="97315-178">The `MarkOutputsAsFinished` method calls `SetEndOfRowset` on the last output buffer.</span></span>

-   <span data-ttu-id="97315-179">`CreateNewOutputRows` メソッドのオーバーライド可能な実装。</span><span class="sxs-lookup"><span data-stu-id="97315-179">An overridable implementation of the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="97315-180">既定の実装では、空のままです。</span><span class="sxs-lookup"><span data-stu-id="97315-180">The default implementation is empty.</span></span> <span data-ttu-id="97315-181">このメソッドは、カスタム データ処理コードを記述するために、通常はオーバーライドして使用します。</span><span class="sxs-lookup"><span data-stu-id="97315-181">This is the method that you will normally override to write your custom data processing code.</span></span>

#### <a name="what-your-custom-code-should-do"></a><span data-ttu-id="97315-182">カスタム コードとして組み込むべき機能</span><span class="sxs-lookup"><span data-stu-id="97315-182">What Your Custom Code Should Do</span></span>
 <span data-ttu-id="97315-183">`ScriptMain` クラスの出力を処理するには、次のメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="97315-183">You can use the following methods to process outputs in the `ScriptMain` class:</span></span>

-   <span data-ttu-id="97315-184">入力行を処理する前に出力行を追加して設定できる場合にのみ、`CreateNewOutputRows` をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="97315-184">Override `CreateNewOutputRows` only when you can add and populate output rows before processing input rows.</span></span> <span data-ttu-id="97315-185">たとえば、`CreateNewOutputRows` を変換元に使用することはできますが、非同期出力型の変換では、入力データの処理中または処理後に `AddRow` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="97315-185">For example, you can use `CreateNewOutputRows` in a source, but in a transformation with asynchronous outputs, you should call `AddRow` during or after the processing of input data.</span></span>

-   <span data-ttu-id="97315-186">出力を閉じる前に、出力に対して何らかの処理を行う場合は、`FinishOutputs` をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="97315-186">Override `FinishOutputs` if you have to do something to the outputs before they are closed.</span></span>

 <span data-ttu-id="97315-187">`PrimeOutput` メソッドは、これらのメソッドが適切な時点で確実に呼び出されるようにするものです。</span><span class="sxs-lookup"><span data-stu-id="97315-187">The `PrimeOutput` method ensures that these methods are called at the appropriate times.</span></span>

## <a name="postexecute-method"></a><span data-ttu-id="97315-188">PostExecute メソッド</span><span class="sxs-lookup"><span data-stu-id="97315-188">PostExecute Method</span></span>
 <span data-ttu-id="97315-189">データの行を処理した後に 1 回だけ実行する必要のある処理がある場合は、基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="97315-189">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class whenever you have processing that you must perform one time only after you have processed the rows of data.</span></span> <span data-ttu-id="97315-190">たとえば、変換元でデータをデータ フローに読み込むために使用した `System.Data.SqlClient.SqlDataReader` を閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="97315-190">For example, in a source, you may want to close the `System.Data.SqlClient.SqlDataReader` that you have used to load data into the data flow.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="97315-191">`ReadWriteVariables` のコレクションは、`PostExecute` メソッド内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="97315-191">The collection of `ReadWriteVariables` is available only in the `PostExecute` method.</span></span> <span data-ttu-id="97315-192">したがって、データ行を処理するたびにパッケージ変数の値を直接増やすことはできません。</span><span class="sxs-lookup"><span data-stu-id="97315-192">Therefore you cannot directly increment the value of a package variable as you process each row of data.</span></span> <span data-ttu-id="97315-193">代わりに、ローカル変数の値をインクリメントし、 `PostExecute` すべてのデータが処理された後に、パッケージ変数の値をメソッドのローカル変数の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="97315-193">Instead, increment the value of a local variable, and set the value of the package variable to the value of the local variable in the `PostExecute` method after all data has been processed.</span></span>

## <a name="releaseconnections-method"></a><span data-ttu-id="97315-194">ReleaseConnections メソッド</span><span class="sxs-lookup"><span data-stu-id="97315-194">ReleaseConnections Method</span></span>
 <span data-ttu-id="97315-195">通常、変換元および変換先は外部データ ソースに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97315-195">Sources and destinations typically must connect to an external data source.</span></span> <span data-ttu-id="97315-196">基本クラス <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> メソッドをオーバーライドして、以前に <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> メソッドで開いた接続を閉じ、解放します。</span><span class="sxs-lookup"><span data-stu-id="97315-196">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class to close and release the connection that you have opened previously in the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> method.</span></span>

```vb
    Dim connMgr As IDTSConnectionManager100
...
    Public Overrides Sub ReleaseConnections()

        connMgr.ReleaseConnection(sqlConn)

    End Sub
```

```csharp
IDTSConnectionManager100 connMgr;

public override void ReleaseConnections()
{

    connMgr.ReleaseConnection(sqlConn);

}
```

<span data-ttu-id="97315-197">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="97315-197">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="97315-198">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="97315-198">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="97315-199">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="97315-199">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="97315-200">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="97315-200">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="97315-201">参照</span><span class="sxs-lookup"><span data-stu-id="97315-201">See Also</span></span>
 <span data-ttu-id="97315-202">スクリプトコンポーネント[エディターでのスクリプトコンポーネントの構成](configuring-the-script-component-in-the-script-component-editor.md)[スクリプトコンポーネントのコーディングおよびデバッグ] (../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md</span><span class="sxs-lookup"><span data-stu-id="97315-202">[Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md) [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md</span></span>


